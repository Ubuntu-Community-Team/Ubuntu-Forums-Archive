---
title: "Live to Local"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by BobJam on 2011-05-15
I've posted this on the Joomla forums where it may be more appropriate, but I've gotten a lot of good tips here, so I thought I'd try this too.

I want to get a working copy of my live site onto my local machine (yes, I did it backwards . . . whereas most do it locally at first and then upload to live, I did it the other way around).

My OS is Ubuntu 9.10, and instead of LAMPP, I did a standalone install of PHP 5.2, Apache2, and MySQL Server version 5.1.37-1ubuntu5.5.  So my local root is /var/www.

Apache runs just fine and so does PHP and MySQL.  I transferred my live site db to my local machine and believe it or not the privileges are such that it CAN connect to the MySQL server (I got the usual "Cannot connect . . ." at first, but assigned the privileges to that db via phpmyadmin.)

In any case, now I'm sitting on my local machine with a working apache2, PHP, and MySQL, the db from the live site and not much else.  Sort of like all dressed up and no place to go.

I did however FTP all my public_html folders and files to the /var/www folder.  The live site is Joomla built, but simply transferring the folders and files and also the db to my local machine doesn't do anything but give me the standard apache welcome screen, "It works!  This is the default web page for this server.  The web server software is running but no content has been added, yet."  For some reason the Joomla built content is missing in action. 

I really don't know where to go from here.  I have no idea what I have to do or even if I can do anything, like modify the configuration.php file from my live site, a copy of which now resides on /var/www.

What I'm thinking about is removing those Joomla folders and files on /var/www and just using Akeeba to backup my live site and installing kickstart.php on my local /var/www and the zipped Akeeba backup and then running kickstart.  (Would I remove the apache index.htm file from /var/www, so that only the archived backup and kickstart.php reside on /var/www, and then run kickstart?  Do I need to modify the permissions on the /var/www folder for kickstart to work?).

I'm really lost here . . . I need some kind of a step-by-step guide on where to go from here.

Again, the ultimate goal is to get a working copy of my live site on my local machine, so that I can 'speriment with mods and no longer risk borking the live site.  Obviously, included in the scheme would be how to go from local to live when I like the mods and see that they work.  Could I do that also with Akeeba?

---

### Post by An Sanct on 2011-05-15
When you go to 'localhost' in your browser, Apache serves you the first site it finds, that is index.htm (this one holds "It works!"), remove or rename that file and you should get index.php.

---

### Post by BobJam on 2011-05-15
Now I'm getting:

```
**Warning**:  include(/home/rbjamie/public_html/zbblock/zbblock.php) [[function.include]("http://www.rogerchang.net/function.include")]: failed to open stream: No such file or directory in /var/www/index.php on line 1

**Warning**:  include() [[function.include]("http://www.rogerchang.net/function.include")]:  Failed opening '/home/rbjamie/public_html/zbblock/zbblock.php' for  inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/index.php on line 1

**Warning**:  Cannot modify header information - headers already sent by (output started at /var/www/index.php:1) in /var/www/libraries/joomla/factory.php on line 566
Database Error: Unable to connect to the database:Could not connect to MySQL

```First of all, "zbblock" is the security software I use on my LIVE site.  But more importantly, I think that first "Warning" line is because the path on line one in index.php does NOT exist on my local machine.  Which is why I'm thinking to try and use Akeeba because maybe it will adjust those paths.

In the alternative, I guess I could just as well go in there and edit the index.php with my IDE.  But then I'd have to do that on my LIVE site everytime I uploaded my content modifications.

The second warning seems to be the same.

The third warning I'm not too sure about, except I see there's that damn " . . . could not connect to MySQL" nonsense again.

I thought I had solved that whole problem when I just flat out reset the MySQL password with the sequence:
```
sudo /etc/init.d/mysql stop

sudo mysqld --skip-grant-tables &

mysql -u root mysql
```And then at the MySQL prompt:
```
UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE User='root'; FLUSH PRIVILEGES; exit;
```And then I was using my own "testme.php" file:

```
<?php
/**********************************************************************
 START editing here...
**********************************************************************/

$mysql_host     =   'localhost';
$mysql_username =   'root';
$mysql_password =   '';
$mysql_database =   '';

/**********************************************************************
 STOP editing here...
**********************************************************************/

echo('<p>Trying to connect to MySQL on server <strong>'.$mysql_host.'</strong> as user <strong>'.$mysql_username.'</strong> with password <strong>'.$mysql_password.'</strong>.</p>');
$db=mysql_connect($mysql_host,$mysql_username,$mysql_password);
if(!is_resource($db)) {
    echo('<p style="color:#c00">FAILED</p>');
    echo('<p>Debug - '.mysql_errno($db) . ':' . mysql_error($db). '</p>');
    exit();
} else {
    echo('<p style="color:#0c0">SUCCESS</p>');
}
echo('<hr />');
mysql_query('SET CHARACTER SET \'utf8\';',$db);
mysql_query('SET NAMES \'utf8\' COLLATE \'utf8_general_ci\';',$db);
echo('<p>Trying to talk to database <strong>'.$mysql_database.'</strong>.</p>');
if(!mysql_select_db($mysql_database,$db)) {
    echo('<p style="color:#c00">FAILED</p>');
    echo('<p>Debug - '.mysql_errno($db) . ':' . mysql_error($db). '</p>');
    exit();
} else {
    echo('<p style="color:#0c0">SUCCESS</p>');
    exit('<p>Thank God! Now it's time for that cigar...</p>');
}
mysql_close($db);
?>

```to see if it worked.  The indication was "[COLOR=Lime]**Success**[COLOR=Black]" when I plugged in the LIVE site db name and reset password.[/COLOR][/COLOR]

But I think the configuration.php file from my LIVE site, plus some other imported files, needs to be edited also.

Bottom line, again this was why I was thinking of using Akeeba to avoid all this hassle . . . which it advertises it will do.

Another problem is that I know just enough to be dangerous, and I was hoping maybe Akeeba would help me not to shoot myself in the foot, which I often end up doing when I try to do things myself.

I get it "half-right" and screw myself up with the other half that is absolutely wrong.

Which is another reason why I need to get my site on my local machine for edits.  I've been lucky so far, but sooner or later if I keep editing the LIVE site, the law of averages is going to catch up with me and I'm going to bork the LIVE site.

Fortunately I just renamed the Apache index.htm file to "indexold.htm" and was able to recover to at least where I was getting the apache "working" message, which essentially puts me back to square one.

---

### Post by An Sanct on 2011-05-15
Well, the *index.htm* file is just a small "*Hello world*" and can be deleted without worrying.

All files in your /var/www have to be an exact representation of the live site, also the database should be identical (same tables should exist).

To make life easy on you, create a user with the same username as for the live version with the same password as that user, this way you will not have to change settings.

If both sites don't have the same scripts in the same locations, you cannot expect it to work and as a result, you will have two different sites.

*don't give away the username/password info, I am in no way interested of knowing it*

---

