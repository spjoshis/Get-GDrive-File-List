# Get-GDrive-Files-List

Get list of files and folders stored in Google Drive.

# Setup
- Run `composer install` command from terminal in root directory of application.

# Usage
<pre><code>&lt;?php

  require('google-client.php');

  // Get the API client and construct the service object.
  $client = getClient();
  $service = new Google_Service_Drive($client);

  // Print the names and IDs for up to 10 files.
  $optParams = array(
    'pageSize' => 10,
    'fields' => 'nextPageToken, files(id, name)'
  );
  $results = $service->files->listFiles($optParams);

  if (count($results->getFiles()) == 0) {
    print "No files found.\n";
  } else {
    print "Files:\n";
    foreach ($results->getFiles() as $file) {
      printf("%s (%s)\n", $file->getName(), $file->getId());
    }
  }
?&gt;
</code></pre>
