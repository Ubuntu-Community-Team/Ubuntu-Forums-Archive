---
title: "Issues with installing Subversion"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by farseer11 on 2011-07-01
Hi all,
Having freshly installed Ubuntu, I tried to install SVN with the following steps from my user account (/home/myusername):

sudo apt-get install subversion libapache2-svn

sudo svnadmin create /svn

vi /etc/apache2/mods-enabled/dav_svn.conf then uncommented "DAV svn" and changed the repository location to "usr/lb/svn" to "/svn". This, in retrospect, was probably a mistake.

I then tried : sudo /etc/init.d/apache2 restart and sudo /etc/init.d/apache2 start but both of them gave me a weird "missing MPM package" error. As this happened a while ago, I can not give the exact error message.

For troubleshooting, I visited this site: [http://ubuntuforums.org/showthread.php?t=526020](http://ubuntuforums.org/showthread.php?t=526020)

I discovered that I was missing the apache2 directory in /etc, so I installed apache2 and php by hand with 
sudo apt-get install apache2
sudo apt-get install php5
which worked, but when I tried to start apache2, I kept getting a multitude of errors.

I finally decided to start over on a clean slate with the purge command: apt-get purge apache2. I then, following instructions, tried to remove the apache2 directory to remove all traces of my installation, but when attempting the use rm -r, I was told : descent into write protected directory? I said no.

Now I am stuck here, confused and feeling stupid, and with my computer in a very messed up, indeterminate state. How can I remove everything I've done so that I can start over?

Any help is appreciated.
:

---

### Post by wildmanne39 on 2011-07-01
> **farseer11 said:**
> Hi all,
Having freshly installed Ubuntu, I tried to install SVN with the following steps from my user account (/home/myusername):

sudo apt-get install subversion libapache2-svn

sudo svnadmin create /svn

vi /etc/apache2/mods-enabled/dav_svn.conf then uncommented "DAV svn" and changed the repository location to "usr/lb/svn" to "/svn". This, in retrospect, was probably a mistake.

I then tried : sudo /etc/init.d/apache2 restart and sudo /etc/init.d/apache2 start but both of them gave me a weird "missing MPM package" error. As this happened a while ago, I can not give the exact error message.

For troubleshooting, I visited this site: [http://ubuntuforums.org/showthread.php?t=526020](http://ubuntuforums.org/showthread.php?t=526020)

I discovered that I was missing the apache2 directory in /etc, so I installed apache2 and php by hand with 
sudo apt-get install apache2
sudo apt-get install php5
which worked, but when I tried to start apache2, I kept getting a multitude of errors.

I finally decided to start over on a clean slate with the purge command: apt-get purge apache2. I then, following instructions, tried to remove the apache2 directory to remove all traces of my installation, but when attempting the use rm -r, I was told : descent into write protected directory? I said no.

Now I am stuck here, confused and feeling stupid, and with my computer in a very messed up, indeterminate state. How can I remove everything I've done so that I can start over?

Any help is appreciated.
:
Hi, I am not sure how to fix your problem, I just wanted to tell your that the rm -r command you was trying to use is very dangerous, it will remove everything in the directory you specify. So if you give it the wrong directory it could delete your system and make it unusable.

---

