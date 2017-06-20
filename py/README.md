# Downloading Tiles

We have created a script that gives you the ability to fetch a subset of Valhalla json/osmlr tiles.  The script uses a bounding box to determine the list of tiles that intersect with the bounding box.

### Run via the command line

./download_tiles.sh `Bounding_Box` `URL` `Output_Directory` `Number_of_Processes` `File_Type` `Tar_Output`

`Bounding_Box`:  This is the bounding box that will be used to fetch the subset of tiles.  The format is lower left lng/lat and upper right lng/lat or min_x, min_y, max_x, max_y (e.g., NYC Bounding box:  -74.251961,40.512764,-73.755405,40.903125)

`URL`:  This is the prefix of the URL where the tiles are located.  For example, if the full URL for a tile is https://thewebsite.com/dir/000/753/542.json, you would enter https://thewebsite.com/dir.

`Output_Directory`:  This is where the tiles will be created.  NOTE: Output directory will be deleted and recreated.

`Number_of_Processes`:  This is the number of cURL requests that you want to run in parallel.

`File_Type`: json|osmlr: This is the type of files that exist at this s3 location.

`Tar_Output`:  True|False: do you want the tiles tar'd up after they are download? This is an optional parameter that defaults to False.  

Example Usage: ./download_tiles.sh -74.251961,40.512764,-73.755405,40.903125 https://thewebsite.com/dir /data/tiles 5 json false

If cURL reports and error the script will report on what tiles were not downloaded.  This could be due to issues from connection problems, to a high number of processes being set, or just the fact that tile no longer exists.  For example://

[WARN] https://thewebsite.com/dir/000/753/542.json was not found!

A listing of the graph tile files is saved to files.txt.  Moreover, cURL output is saved to curl_output.txt.
