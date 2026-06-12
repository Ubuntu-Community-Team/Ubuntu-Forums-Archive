---
title: "Mail checker wanted"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by 315234 on 2007-09-04
I am looking for a mail checker (POP/gmail) which can check for new mail every few minutes, and run a command if I have new emails. I would prefer it to be a non-GUI application or a daemon. Does anyone know of such a thing?

Thanks in advance

---

### Post by yousufinternet on 2007-09-04
their is a gui 1 it's called 
gmail notifey

---

### Post by x-point on 2007-09-04
I think that the most simple way is to write perl script to check mailbox data and put this script to cron. I also recommend mutt e-mail client for this purpose (for manual checking of the mail box).

---

### Post by KCPokes on 2007-09-04
> **x-point said:**
> I think that the most simple way is to write perl script to check mailbox data and put this script to cron. I also recommend mutt e-mail client for this purpose (for manual checking of the mail box).

I agree, if it needs to be non-gui.  I wrote one to check a specific set of mailboxes, parse the email looking for a specific URL, retrieve the images from the URL and upload them to Gallery.  The purpose was to be able to send pictures from my phone to my gallery, immediately.  You could do a similar process using either Perl or PHP.

---

### Post by 315234 on 2007-09-04
Hmmm.

```
$ sudo apt-get install gmail-notify

...

The following extra packages will be installed:
  libgail-common libgail17 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common
  libgksu1.2-0 libgksuui1.0-1 libgtkhtml2-0 libgtksourceview-common
  libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgtop2-common libmetacity0
  libmozjs0d libnautilus-burn3 libpanel-applet2-0 libtotem-plparser1
  libwnck-common libwnck18 libxres1 libxul-common libxul0d metacity-common
  python-cairo python-gnome2-desktop python-gnome2-extras python-gtk2
  python-numeric python-pyorbit
Suggested packages:
  gda2-mysql gda2-postgres gda2-odbc gda2-sqlite gda2-freetds
  python-gnome2-desktop-doc python-gnome2-extras-doc python-numeric-tutorial
Recommended packages:
  libgda2-bin

```


I'd rather not, if I could avoid it. Any lighter packages?

---

### Post by 315234 on 2007-09-04
Yeah, I had suspected it would come to scripting in the end. However, neither Perl nor PHP is my forte. I tried scripting mutt in the past (to do a very similar thing to what KCPokes describes) with little success.

KCPokes, do you still have that script? Would you mind posting it?

---

### Post by KCPokes on 2007-09-04
```

<?

if (!isset($gallery_basedir)) {
$gallery_basedir = './';
}
require($gallery_basedir . "init.inc");

// include pear libraries
include ("Net/pop3.php");
include ('Mail/mimeDecode.php');

$apop=0;
$pop3_connection=new pop3_class;
$pop3_connection->hostname="<mail.yourmailserver.com>";
$savedir = '<where to save the file>';
$scriptDir = '<where your script runs>';


$link = mysql_connect("<database location>", "<db_username>", "<db_password>")
   or die("Could not connect : " . mysql_error());
mysql_select_db("<db_name>") or die("Could not select database");
echo "Connected successfully to MySQL database.  Retrieving user info....\n";
$query = "SELECT email, emailDomain, password, album FROM users";
$result = mysql_query($query,$link) or die("Query failed : " . mysql_error());


while ($row = mysql_fetch_array($result, MYSQL_NUM)) {

   $user=$row[0];
   $pop3_connection->hostname=$row[1];
   $password=$row[2];
   $album=$row[3];

   if(($error=$pop3_connection->Open())=="")
   {
      if(($error=$pop3_connection->Login($user,$password,$apop))=="")
      {
   	 echo "Connected to email $user successfully.\n";
	 $pop3_connection->Statistics(&$messages,&$size);
	 echo "Retrieving $messages messages...\n";
	 for($i=0;$i<=$messages;$i++)
	 {
	    if(($error=$pop3_connection->RetrieveMessage($i,&$headers,&$body,-1))=="")
  	    {
	       for($line=0;$line<count($body);$line++)
	       {
	          $searchOn = "inviteToken";
	          if(strpos($body[$line],$searchOn))
	          {
	             $url = html_entity_decode($body[$line]);
	             // strip out the html before the image url
	             $url = substr($body[$line],strpos($body[$line],"http:"));
	            // strip out everything after the image url
                     $newfile = "EmailUpload_".date("Ymd:H:m:s");
	             $outfile= $savedir.$newfile.".jpg";
	    	     echo "Copy URL: ".$url."\n";
	 	     //copy the image to the temp directory
		     echo "Copy image to temp directory\n";
                     copy($url,$outfile);
		     // add image to the gallery
		     log_image($outfile,$album,$scriptDir);
                     echo "Delete temp image: $outfile\n";
		     unlink ($outfile);
		     $pop3_connection->DeleteMessage($i);
 	           }
 	        }
             }
          }
     }
     else
     {
        echo "Error: $error\n";
     }

    $pop3_connection->Close();
    echo "Closed $user email connection\n";
  }
}

mysql_free_result($result);
mysql_close($link);


function log_image($file,$album,$scriptPath)
{
  echo "Uploaded File: $file\n";
  echo "Album: $album\n";
  // quick hack: get $tag and $name code from save_photos.php
  $caption = "emailed from mobile device at ".date("D M j G:i:s T Y");
  $command = $scriptPath."/galleryadd.pl -G 2 -g <gallery URL> -a $album $file";
  echo $command."\n\n";
  $output = system($command);
  echo $output."\n\n";
}

?>

```

It is an old script, modified only when I moved from Gallery to Gallery2, so it can definitely be cleaned up to be far more efficient, but it works so I don't mess with it much.  You will need the POP3 and mimeDecode PEAR add-ons, but otherwise it is pretty straightforward.  I run it against a DB, as it connects to a number of email accounts and pulls images for all of them, but you could eliminate the DB connection and just hardcode your information if it is limited to a single account. 

May at least be enough to get you started as to how you want to do it, but its not perfect.

---

