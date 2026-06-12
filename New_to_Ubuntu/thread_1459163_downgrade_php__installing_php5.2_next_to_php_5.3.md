---
title: "downgrade php / installing php5.2 next to php 5.3"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by brouwser on 2010-04-21
Hi all,

I've installed a LAMP server with php 5.3 ubuntu 10.04. I need to run a webapp that has problems with 5.3, so I want to install php 5.2.x as well. I have, however, no idea how to get that done. All my searches on this forum and google led to upgrading from a previous version to the latest one. Who can help?

---

### Post by indytim on 2010-04-21
The only way that I can think of would be to re-compile with v5.2x... not a task for the "Absolute Beginner".  

It may be easier to resolve the problems that you are seeing with 5.3.  I would recommend starting a new thread in the Programming Forum or post the problems you are having with PHP in the PHP forum at the main PHP site.  You will find a larger audience of "hard-core" PHP-types in these locations :).

IndyTim

---

### Post by brouwser on 2010-04-21
Hi IndyTim,

Thanks for your response. I don't particularly need to keep php 5.3. Would it be easier to uninstall the current LAMP and reinstall it with 5.2.8?

---

### Post by indytim on 2010-04-21
If you can get it through the repository, that would also be an "easy button".

:)

IndyTim

---

### Post by brouwser on 2010-04-21
That sounds like a "no, 'cos you won't get it through the repository"?:(

---

### Post by rubo77 on 2010-04-30
I created a script solution for 

[_Reverting PHP to 5.2 in Lucid 10.04_](http://ubuntuforums.org/showpost.php?p=9080474&postcount=7)

but i may not post it there so i tell you here now ;)

create the script 
```
#!/bin/bash
# by Ruben Barkow (rubo77) http://www.entikey.z11.de/

# Originally Posted by Bachstelze http://ubuntuforums.org/showthread.php?p=9080474#post9080474
# OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:

echo "Am I root?  "
if [ "$(whoami &2>/dev/null)" != "root" ] && [ "$(id -un &2>/dev/null)" != "root" ] ; then
  echo "  NO!

Error: You must be root to run this script.
Enter
sudo su
"
  exit 1
fi
echo "  OK";


#install aptitude before, if you don`t have it:
apt-get install aptitude
# or if you prefer apt-get use:
# alias aptitude='apt-get'

# finish all apt-problems:
aptitude update
aptitude -f install
#apt-get -f install

# remove all your existing PHP packages. You can list them with dpkg -l| grep php
PHPLIST=$(for i in $(dpkg -l | grep php|awk '{ print $2 }' ); do echo $i; done)
echo these pachets will be removed: $PHPLIST 
# you need not to purge, if you have upgraded from karmic:
aptitude remove $PHPLIST
# on a fresh install, you need purge:
# aptitude remove --purge $PHPLIST


#Create a file each in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php5_2);
#
#Package: php5
#Pin: release a=karmic
#Pin-Priority: 991
#
#The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic:

echo ''>/etc/apt/preferences.d/php5_2
for i in $PHPLIST ; do echo "Package: $i
Pin: release a=karmic
Pin-Priority: 991
">>/etc/apt/preferences.d/php5_2; done

# duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:
#sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list

# better exactly only the needed sources, cause otherwise you can get a cachsize problem:
echo "# needed sources vor php5.2:
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic main restricted

deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu/ karmic universe
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic universe
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic-updates universe

deb http://old-releases.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://old-releases.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu karmic-security main restricted
deb http://old-releases.ubuntu.com/ubuntu karmic-security universe
deb-src http://old-releases.ubuntu.com/ubuntu karmic-security universe
deb http://old-releases.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu karmic-security multiverse
" > /etc/apt/sources.list.d/karmic.list

aptitude update

apache2ctl restart

echo install new from karmic:
aptitude -t karmic install $PHPLIST

# at the end retry the modul libapache2-mod-php5 in case it didn't work the first time:
aptitude -t karmic install libapache2-mod-php5

apache2ctl restart

```

make it executeable:
```
chmod +x /usr/local/sbin/php5.2-downgrade
```

edit:
i added the historical karmic sources:
```
http://old-releases.ubuntu.com/ubuntu/
```

---

### Post by arkangl on 2010-04-30
Thank you very much fors this script.
It saved my day.

---

### Post by rubo77 on 2010-05-01
the problem now is, that the update manager wants to upgrade php to 5.3 now everytime

to tell the update-manager not to do so, you have to set the php packages to hold with
```

for i in $(dpkg -l | grep php|awk '{ print $2 }' ); 
do echo "echo $i hold |sudo dpkg --set-selections"; echo $i hold |sudo dpkg --set-selections; done

``` or so?

---

### Post by siamect on 2010-05-02
Thank a lot for the script... 
One warning though... aptitude wanted to remove some 338M of packages from my computer... if I use apt-get instead it does not remove anything but the pap packs...
Take care 
Martin

---

### Post by rubo77 on 2010-05-02
please lets not discuss 
[google.com/search?q="aptitude+vs+apt-get"]("http://www.google.com/search?q="aptitude+vs+apt-get"")
here ;)
(sure: you can use apt-get if you prefer that)

one notion: 

the file ```
/etc/apt/preferences.d/php5.2
``` 
must be called
```
/etc/apt/preferences.d/php5_2
```
without dots !!!

---

### Post by gaellafond on 2010-05-03
Thanks for your script, it was helpful.

Btw, I used Hardy instead of Karmic since Hardy as a newest version of PHP (v. 5.2.4-2ubuntu5.10) and the Karmic version was giving me warnings... I also change the mirror, I'm not sure where [http://de](http://de)... is but it's definitely not my country.

---

### Post by rubo77 on 2010-05-04
> **gaellafond said:**
> I'm not sure where [http://de](http://de)... issorry, that#s germany.

how can i change that to the local mirror in the script?

is there a system variable?

---

### Post by Eugene_Bondarenko on 2010-05-05
Thanks for the script, it saved my day!

I am not sure how to put my software sources back though. I checked the list and it has lots of karmic sourced and none lucid ones. I am rather new to ubuntu so I may be misunderstanding something but shouldn't I have lucid sources there to keep all my other stuff updated?

---

### Post by Inside on 2010-05-05
Check for the instructions at the bottom of the article.

[http://jtrancas.wordpress.com/2010/05/04/cakephp-1-1-and-php-5-3/](http://jtrancas.wordpress.com/2010/05/04/cakephp-1-1-and-php-5-3/)

It would work for installing karmic PHP packages.

Regards.

---

### Post by Eugene_Bondarenko on 2010-05-05
Thanks but I've already installed karmic packages by executing the script posted earlier in this thread. What I am worried about is the current state of my system. The software sources list has all karmic sources and none lucid ones. Also when I check for updates, I get a huge list of recommended updates (including stuff that is definitely not related to php) which I find strange because I updated yesterday.

---

### Post by Inside on 2010-05-05
Oops, sorry. Anyway, i also installed it using karmic packages and i dont have that update suggestions in my system.

---

### Post by rainboww on 2010-05-08
[I]Many thanks! 
[/I]

---

### Post by ami7878 on 2010-05-10
> **rubo77 said:**
> the problem now is, that the update manager wants to upgrade php to 5.3 now everytime

to tell the update-manager not to do so, you have to set the php packages to hold with
```

for i in $(dpkg -l | grep php|awk '{ print $2 }' ); 
do echo "echo $i hold |sudo dpkg --set-selections"; echo $i hold |sudo dpkg --set-selections; done

``` or so?

First let me say thanks for the script to downgrade to 5.2.  That really saved my day :P.
I'm working with Drupal and it seams it doesn't support php 5.3.

I do have couple of questions:
1. Do I run the above code, to disable updates, in terminal?
2. What about updates to php 5.2?

Thanks again

---

### Post by rainboww on 2010-05-10
After installing php 5.2.10 to  hold karmic php packages 
```
#!/bin/bash
for i in $(dpkg -l | grep php|awk '{ print $2 }' ); 
do echo "echo $i hold |sudo dpkg --set-selections"; echo $i hold |sudo dpkg --set-selections; done
```To enable lucid php packages upgrade
```
#!/bin/bash
for i in $(dpkg -l | grep php|awk '{ print $2 }' ); 
do echo "echo $i install |sudo dpkg --set-selections"; echo $i install |sudo dpkg --set-selections; done
```To set update priority i try this```
#!/bin/bash
PHPLIST=$(for i in $(dpkg -l | grep php|awk '{ print $2 }' ); do echo $i; done)

for i in $PHPLIST ; do echo "Package: $i
Pin: release a=lucid
Pin-Priority: -10
">>/etc/apt/preferences.d/php5.2; done

for i in $PHPLIST ; do echo "Package: $i
Pin: release a=karmic
Pin-Priority: 900
">>/etc/apt/preferences.d/php5.2; done
```but it doesn't work :(

More info here
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by ami7878 on 2010-05-10
Thanks.  The code for holding karmic packages worked.

---

### Post by angiebb.dm on 2010-05-11
Hi everyone, I tried to downgrade php5.3 but I got an error when I ran the script: 

Dynamic MMap ran out of room. Increase size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: An error occurred while muse (NewVersion1) was processed
E: Problem with MergeList /var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_karmic-updates_universe_binary-amd64_Packages
W: Unable to munmap
E: It couldn't analyze or open packages list 

*sorry I had to translate part of the error* 

now aptitude doesn't work because that error and I don't have neither php5.3 or php5.2 :( , any ideas to solve this?

thanks in advance

---

### Post by rubo77 on 2010-05-12
@angiebb.dm:

that is, cause you have too many sources in your list.

if you used the first example with copying th lucid list into a karmic list:
```
# duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:
#sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list
```then there are too many sources.

so use exactly only the needed sources, cause otherwise you get the cachsize problem

delete all karmic sources except:
```

deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```


(i tried to "Increase size of APT::Cache-Limit" but it didn't work)

---

### Post by rubo77 on 2010-05-12
> **rainboww said:**
> To set update priority i try this```
#!/bin/bash
PHPLIST=$(for i in $(dpkg -l | grep php|awk '{ print $2 }' ); do echo $i; done)

for i in $PHPLIST ; do echo "Package: $i
Pin: release a=lucid
Pin-Priority: -10
">>/etc/apt/preferences.d/php5.2; done

for i in $PHPLIST ; do echo "Package: $i
Pin: release a=karmic
Pin-Priority: 900
">>/etc/apt/preferences.d/php5.2; done
```but it doesn't work :(

More info here
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

maybe there is not allowed to have any dots in the filename?
so does it work if you use
/etc/apt/preferences.d/php5_2
instead of
/etc/apt/preferences.d/php5.2
???

[_here_]("https://help.ubuntu.com/community/PinningHowto") it sais:
> Make sure the file name does not have a dot in it! 

---

### Post by rainboww on 2010-05-12
Sorry, but /etc/apt/preferences.d/**php5_2** instead of /etc/apt/preferences.d/**php5.2** doesn't work.
I think                                                                                "Aptitude  ignores /etc/apt/preferences.d/*": [https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/508545](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/508545)

To "Increase size of APT::Cache-Limit" take a look here: [http://linux.chrissweeney.co.uk/topic.php?t=49](http://linux.chrissweeney.co.uk/topic.php?t=49)

create a file such as: 
/etc/apt/apt.conf.d/**11cache** 
And add the line: 
```
APT::Cache-Limit "32768000";
```This worked for me.

---

### Post by angiebb.dm on 2010-05-12
Thanks rubo77 and rainboww for replying, I checked the file karmic.list and it only had the sources you mentioned. What I think happened was that aptitude got both files sources.list and karmic.list because when I renamed the sources.list file I didn't get the cachsize problem and I could install php5.2 from karmic sources. Any way thanks so much for your contribution.

---

### Post by thinguy on 2010-07-06
Great script helped with my Drupal 6 install.
worked great. Do I need to do anything to my sources list after running this or was the script updated?
Are source lists pulling latest updated with the exception of php5.2?

Thanks.

---

### Post by manguito on 2010-07-21
Hi everyone,
I did downgrade to php 5.2.10 successfully following the steps mentioned above; however, I need to go back to php 5.3.2.
How should I do it?
any ideas?

---

### Post by rubo77 on 2010-07-21
maybe just delete the file 
```
/etc/apt/preferences.d/php5_2

```
and unselect all the karmic sources in your sources list and then do a dist-upgrade?

---

### Post by motd on 2010-08-02
is the downgrade procedure different if i have a maverick release rather than lucid?
Cheers !!

---

### Post by pschalkx on 2010-09-16
@ Rubo77:

Man, you are a star!

Saved my day with this script.

Rgds,

Philip

---

### Post by Glank on 2010-09-22
i have downgraded successfully to 5.2.10, but i get another problem with cURL, cURL is not active and when i want to install it, got some broken package warn.
```
user@comp:~$sudo apt-get install curl libcurl3 libcurl3-dev php5-curl php5-mcrypt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcurl3 is already the newest version.
Note, selecting libcurl4-openssl-dev instead of libcurl3-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-curl: Depends: phpapi-20090626+lfs
             Depends: php5-common (= 5.3.2-1ubuntu4.5) but 5.2.10.dfsg.1-2ubuntu6.5 is to be installed
  php5-mcrypt: Depends: phpapi-20090626+lfs
E: Broken packages

```
anyone can help me ?

---

### Post by AleKi83 on 2010-09-29
Hi all,
I have the same problem.
Any help is very precious.

Thanks.
AlessandroC

---

### Post by sbinkerd1 on 2010-10-20
Same issue here:


Hello. I had downgraded my php install to what came before 5.3.2 because it didn't work with my joomla sites at the time. I just updated alot of packages including apache, but did not update the PHP to 5.3.2 yet. after all the packages went through now I have a broken php install:

here is the version I show on my system:

dpkg -l| grep php
rc libapache2-mod-php5 5.2.10.dfsg.1-2ubuntu6 server-side, HTML-embedded scripting languag
hi php5-common 5.2.10.dfsg.1-2ubuntu6 Common files for packages built from the php
ii php5-dev 5.2.10.dfsg.1-2ubuntu6 Files for PHP5 module development
rc php5-gd 5.2.10.dfsg.1-2ubuntu6 GD module for php5
rc php5-mcrypt 5.2.6-0ubuntu2 MCrypt module for php5
rc php5-mysql 5.2.10.dfsg.1-2ubuntu6 MySQL module for php5
rc phpmyadmin 4:3.3.2-1 MySQL web administration tool


I have these linked to the Karmic Repositories using the prescribed method below. this did work well until the last Apache upgrade I did.

[URL="http://www.nickveenhof.be/blog/reverting-or-downgrading-php-53-52-ubuntu-lucid-lynx-1004"]

now I get broken package errors:

> apt-get install php5-imap
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
php5-imap: Depends: phpapi-20090626+lfs
E: Broken packages


The following packages have unmet dependencies:
php5: Depends: libapache2-mod-php5 (>= 5.2.10.dfsg.1-2ubuntu6) but it is not going to be installed or
libapache2-mod-php5filter (>= 5.2.10.dfsg.1-2ubuntu6) but it is not going to be installed or
php5-cgi (>= 5.2.10.dfsg.1-2ubuntu6) but it is not going to be installed
E: Broken packages


ANY help is much appreciated!
:(

---

### Post by Silvernail on 2010-10-23
This solved my problem Thanks. The script in post #6 works like a charm.

---

### Post by ImaLamer on 2010-11-10
Hate to do the bump thing... but I've reverted my server to 5.2 using the script in this thread (thank you!) - but can not installed a few php5 packages such as:

php5-dev
php5-xcache

The development packages (where I need to get 'phpize' from) give me this error:
```
The following packages have unmet dependencies:
  php5-dev: Depends: php5-common (>= 5.3.2-1ubuntu4.5) but 5.2.10.dfsg.1-2ubuntu6.5 is to be installed

```

And the xcache package gives me this:
```
The following packages have unmet dependencies:
  php5-xcache: Depends: phpapi-20090626+lfs

```

Which I'm sure means that it's pulling both from Lucid repos and not the Karmic - is there any way to get around this on the command line or will I have to make other changes to basically mimic what the script does?

---

### Post by ppafford on 2010-11-19
I'm having the same problem. Updated to 10.10 then installed Zend-server. when trying to uninstall things went to crap. now I'm stuck at 5.3.3 with no options to downgrade. Any suggestions???

I've modified the script a little, room for improvement as well

```

#! /bin/sh

#check if running as ROOT
ROOTUSER_NAME=root

username=`id -nu`              # Or...   username=`whoami`
if [ "$username" = "$ROOTUSER_NAME" ]
then
  echo "Running as ROOT!!!"
else
  echo "Please run as Root as you are just an ordinary user (but mom loves you just the same)."
  exit 0
fi

php_packages=`dpkg -l | grep php | awk '{print $2}'`

#check if PHP Packages are NULL
if [ -n php_packages ]
then
  echo "Using Found PHP Packages"
  echo $php_packages
else  
  echo "Nothing found, using defaults"
  php_packages="libapache2-mod-php5 php-pear php5-cgi php5-cli php5-common php5-curl php5-gd php5-gmp php5-ldap php5-mcrypt php5-mhash php5-mysql php5-odbc php5-pgsql php5-pspell php5-recode php5-snmp php5-sqlite php5-sybase php5-tidy php5-xmlrpc php5-xsl"
fi            

# Restart Apache Command
RESTART="/etc/init.d/apache2 restart"

#might need to run aptitude purge to remove all the config/ini files
aptitude purge $php_packages
#apt-get remove $php_packages
echo "Removed Packages\n"

sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list
echo "SED Command\n"

#Create the directory
mkdir -p /etc/apt/preferences.d/
echo "Make DIR: /etc/apt/preferences.d/\n"

# Check if PIN php file exists -- NOT WORKING
#if [ -f /etc/apt/preferences.d/php ] 
#then 
#rm /etc/apt/preferences.d/php
#fi

# PINing the verion number so Ubuntu wont upgrade the package
for package in $php_packages;
do echo "Package: $package
Pin: release a=karmic
Pin-Priority: 991
" | sudo tee -a /etc/apt/preferences.d/php
done
echo "Finished with PIN\n"

#Update apt-get repos
apt-get update
echo "Updating Apt-Get\n"

#Just listing all the packages that should be installed
for package in $php_packages;
do echo "Package: $package "
done

echo "Starting PHP Install\n";
apt-get install $php_packages php5-mcrypt
echo "Finished Install.........\nRestarting Apache...........\n"

#Restart Apache
RESTART

#Autoclean, remove old files
apt-get autoclean

```

---

### Post by kart3r on 2010-11-22
First of all thank you rubo77 for your script, it helped me a lot, however i had to do some changes regarding aptitude commands, that had to changed to apt-get. I'm using 10.10 and i think that's why i need to do this changes.

I've attached my file in this post to whoever has trouble with the first release.

Peace

---

### Post by ppafford on 2010-11-23
> **kart3r said:**
> First of all thank you rubo77 for your script, it helped me a lot, however i had to do some changes regarding aptitude commands, that had to changed to apt-get. I'm using 10.10 and i think that's why i need to do this changes.

I've attached my file in this post to whoever has trouble with the first release.

Peace

Will this work for 10.04 installs as well? I was running 10.10 and installed Zend-Server and I un-installed. After that my PHP installation was all screwed up, had to re-install 10.04.

---

### Post by rubo77 on 2010-12-08
> **kart3r said:**
> First of all thank you rubo77 for your script, it helped me a lot, however i had to do some changes regarding aptitude commands, that had to changed to apt-get. I'm using 10.10 and i think that's why i need to do this changes.

I've attached my file in this post to whoever has trouble with the first release.


Your script uses apt-get instead of aptitude, this doesent work correct on my ubuntu 10.10 where i use aptitude already!!!

it only installs some packages.
it doesent install the 5.2-packages for some of these:
php-pear php5-cli php5-common php5-gd php5-imagick php5-mcrypt php5-mysql phpmyadmin

if you don't have aptitude, install with:
```
apt-get install aptitude
```

i had to repair it with
```

# deleting wrong preferences
rm -i /etc/apt/preferences.d/php*
#reinstall needed packages in php5.3
aptitude install php-pear php5-cli php5-common php5-gd php5-imagick php5-mcrypt php5-mysql phpmyadmin

```
and then again the script ***php5_2-downgrade_aptitude.sh*** from my first post:
**[http://ubuntuforums.org/showpost.php?p=9201854&postcount=6](http://ubuntuforums.org/showpost.php?p=9201854&postcount=6)**

---

### Post by Cardale on 2010-12-15
This script was extremely useful.  I just made a few very small changes to make it work with 10.10

Here it is
```
#!/bin/bash
# by Ruben Barkow (rubo77) http://www.entikey.z11.de/

# Originally Posted by Bachstelze http://ubuntuforums.org/showthread.php?p=9080474#post9080474
# OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:
#
# modified by Ryein C. Bowling (Cardale) www.kinggoddard.com
# December 15, 2010
echo "Am I root?  "
if [ "$(whoami &2>/dev/null)" != "root" ] && [ "$(id -un &2>/dev/null)" != "root" ] ; then
  echo "  NO!

Error: You must be root to run this script.
Enter
sudo su
"
  exit 1
fi
echo "  OK";


# finish all apt-problems:
apt-get -f install

# remove all your existing PHP packages. You can list them with dpkg -l| grep php
PHPLIST=$(for i in $(dpkg -l | grep php|awk '{ print $2 }' ); do echo $i; done)
echo these pachets will be removed: $PHPLIST 
# you need not to purge, if you have upgraded from karmic:
apt-get remove $PHPLIST
# on a fresh install, you need purge:
# aptitude remove --purge $PHPLIST


#Create a file each in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php5_2);
#
#Package: php5
#Pin: release a=karmic
#Pin-Priority: 991
#
#The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic:

echo ''>/etc/apt/preferences.d/php5_2
for i in $PHPLIST ; do echo "Package: $i
Pin: release a=karmic
Pin-Priority: 991
">>/etc/apt/preferences.d/php5_2; done

# duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:
#sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list

# better exactly only the needed sources, cause otherwise you can get a cachsize problem:
echo "# needed sources vor php5.2:
deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
" >> /etc/apt/sources.list.d/karmic.list

apt-get update

apache2ctl restart

echo install new from karmic:
apt-get -t karmic install $PHPLIST

# at the end retry the modul libapache2-mod-php5 in case it didn't work the first time:
apt-get -t karmic install libapache2-mod-php5

apache2ctl restart
```

---

### Post by rubo77 on 2010-12-16
@Cardale:
the changes you made are, that you use apt-get instead of aptitude.

did it work with apt-get?
cause at my mashine it didnt!

safer solution is (again) use the original script with aptitude and install aptitude before, if you don`t have it:
```
apt-get install aptitude
```
i added this to the initial script in post #6: ***[http://ubuntuforums.org/showpost.php?p=9201854&postcount=6](http://ubuntuforums.org/showpost.php?p=9201854&postcount=6)***

---

### Post by sheirkoo on 2011-01-27
hi 
i downgrade to 5.2 with no problem at ubuntu 10.10 but when i want to install Curl i get this error:
 
***sudo apt-get install curl libcurl3 libcurl3-dev php5-curl php5-mcrypt***
*Reading package lists... Done*
*Building dependency tree*
*Reading state information... Done*
*Note, selecting 'libcurl4-openssl-dev' instead of 'libcurl3-dev'*
*php5-mcrypt is already the newest version.*
*Some packages could not be installed. This may mean that you have*
*requested an impossible situation or if you are using the unstable*
*distribution that some required packages have not yet been created*
*or been moved out of Incoming.*
*The following information may help to resolve the situation:*
*The following packages have unmet dependencies:*
***php5-curl : Depends: phpapi-20090626+lfs***
***Depends: php5-common (= 5.3.3-1ubuntu9.3) but 5.2.10.dfsg.1-2ubuntu6.7 is to be installed***
 
what must I do?
 
thanks

---

### Post by rubo77 on 2011-01-27
you must add all php-packages to 

```
sudo nano  /etc/apt/preferences.d/php5_2 

```
maybe you dont have php5-curl in it?

---

### Post by sheirkoo on 2011-01-28
hi [rubo77]("http://ubuntuforums.org/member.php?u=426110")
that was the trick.
I found it by googling.

thanks

---

### Post by jaredsten on 2011-02-23
Huge help - Thanks a ton.

---

### Post by LeonHeart on 2011-03-09
Thanks a million times. 
I've tried rubo's script on a maverick installation and everything was fine.
Just one problem with the php5-imagick package.
When I try to install it I get this error and the package doesn' install:
```


The following packages have unmet dependencies:
 php5-imagick : Depends: libmagickcore2 but it is not going to be installed
                Depends: libmagickwand2 but it is not going to be installed
E: Broken packages

```
Ideas?

---

### Post by Fatalentity on 2011-04-18
Hey everyone.

I used the script mentioned on the first page to downgrade from 5.3

However now I would like to upgrade back to 5.3. I removed the php5.3 file from /etc/apt/prefrences.d/php5_3, however I still can't seem to upgrade to the 5.3 package.

Thanks!

---

### Post by stamina on 2011-05-08
The first script allows to run PHP Version 5.2.10-2ubuntu6 with Ubuntu 11.04 although when I try to install phpmyadmin:

sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 phpmyadmin : Depends: php5-mcrypt but it is not going to be installed
              Recommends: php5-gd but it is not going to be installed
E: Broken packages

---

### Post by avrcan10 on 2011-06-07
> **rubo77 said:**
> I created a script solution for 

[_Reverting PHP to 5.2 in Lucid 10.04_](http://ubuntuforums.org/showpost.php?p=9080474&postcount=7)

but i may not post it there so i tell you here now ;)

create the script 
```
#!/bin/bash
# by Ruben Barkow (rubo77) http://www.entikey.z11.de/

# Originally Posted by Bachstelze http://ubuntuforums.org/showthread.php?p=9080474#post9080474
# OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:

echo "Am I root?  "
if [ "$(whoami &2>/dev/null)" != "root" ] && [ "$(id -un &2>/dev/null)" != "root" ] ; then
  echo "  NO!

Error: You must be root to run this script.
Enter
sudo su
"
  exit 1
fi
echo "  OK";


#install aptitude before, if you don`t have it:
apt-get install aptitude
# or if you prefer apt-get use:
# alias aptitude='apt-get'

# finish all apt-problems:
aptitude update
aptitude -f install
#apt-get -f install

# remove all your existing PHP packages. You can list them with dpkg -l| grep php
PHPLIST=$(for i in $(dpkg -l | grep php|awk '{ print $2 }' ); do echo $i; done)
echo these pachets will be removed: $PHPLIST 
# you need not to purge, if you have upgraded from karmic:
aptitude remove $PHPLIST
# on a fresh install, you need purge:
# aptitude remove --purge $PHPLIST


#Create a file each in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php5_2);
#
#Package: php5
#Pin: release a=karmic
#Pin-Priority: 991
#
#The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic:

echo ''>/etc/apt/preferences.d/php5_2
for i in $PHPLIST ; do echo "Package: $i
Pin: release a=karmic
Pin-Priority: 991
">>/etc/apt/preferences.d/php5_2; done

# duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:
#sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list

# better exactly only the needed sources, cause otherwise you can get a cachsize problem:
echo "# needed sources vor php5.2:
deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
" >> /etc/apt/sources.list.d/karmic.list

aptitude update

apache2ctl restart

echo install new from karmic:
aptitude -t karmic install $PHPLIST

# at the end retry the modul libapache2-mod-php5 in case it didn't work the first time:
aptitude -t karmic install libapache2-mod-php5

apache2ctl restart

```

make it executeable:
```
chmod +x /usr/local/sbin/php5.2-downgrade
```
nice work !!!

---

### Post by carlitoxd on 2011-07-25
does this work in Ubuntu 11.04? :confused:
I have problem with PHP 5.3.:(





Esto funciona en Ubuntu 11.04?..:confused:
yo tengo un problema con PHP 5.3:(

---

### Post by rubo77 on 2011-07-25
yes,

i had to select one of the options aptitude offers, where the main php packages are still 5.2 and then it worked

---

### Post by rubo77 on 2011-10-21
i don't dare to upgrade my ubuntu to **Oneiric Ocelot 11.10**, cause the support of karmic was only until april.
i guess, if i upgrade, then it will install **php 5.3** again and no karmic sources are left to **downgrade to php 5.2** again?

anyone has done this already?

maybe it woks with the **debian Lenny** packages?
what would i have to put in here?
> /etc/apt/preferences.d/php5_2

---

### Post by gsmanners on 2011-10-21
Lenny is pretty old. I wonder if php5.2 would work even in Debian.

EDIT: Here's a thought: What about CentOS 5.7? That still has php5.1.

---

### Post by sridharpandu on 2011-10-22
This script works on Natty.

---

### Post by rubo77 on 2011-10-25
> **sridharpandu said:**
> This script works on Natty.

thats not the question, 11.10 is Oneiric Ocelot

---

### Post by rubo77 on 2011-11-28
the sources of karmic are gone on most mirrors, but you can still use the historical sources:
```
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic main restricted

deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu/ karmic universe
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic universe
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic-updates universe

deb http://old-releases.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://old-releases.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu karmic-security main restricted
deb http://old-releases.ubuntu.com/ubuntu karmic-security universe
deb-src http://old-releases.ubuntu.com/ubuntu karmic-security universe
deb http://old-releases.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu karmic-security multiverse
```

i updated this in my initial post, 

anyone has tested that already?

---

### Post by clearbucketLabs on 2011-11-28
Hey,

Ran into an issue with zend optimizer that needed php5.2 for some app, so it seems to have worked so far :)

Thanks a zillion.

---

### Post by rubo77 on 2011-12-08
i created a new bash script with the new sources in my initial post here:
[http://ubuntuforums.org/showthread.php?p=9201854#post9201854](http://ubuntuforums.org/showthread.php?p=9201854#post9201854)

php5_2-downgrade_with_historical_karmic_sources.sh

---

### Post by wizardrpg on 2012-07-10
how to revert to php 5.3 now. As my boss needs php 5.3

---

### Post by rubo77 on 2012-07-10
the easyest way to upgrade again is 
```
sudo apt-get dist-upgrade
```

but you can also delete the php5_2 file ```
sudo rm /etc/apt/preferences.d/php5_2
```
and then just ```
sudo apt-get upgrade
```

---

### Post by wizardrpg on 2012-07-10
Thanks rubo,

are there anyway to disable that auto updater stopper for php versions as now i have upgraded now i want new versions to be installed automatically.


i used this before

for i in $(dpkg -l | grep php|awk '{ print $2 }' );  do echo "echo $i hold |sudo dpkg --set-selections"; echo $i hold |sudo dpkg --set-selections; done

---

### Post by rubo77 on 2012-07-10
yes, it is disabled if you deleted the php5_2 "stopper" file ```
sudo rm /etc/apt/preferences.d/php5_2
```

---

### Post by oldos2er on 2012-07-10
Old thread closed. Please start a new thread for any additional questions.

---

