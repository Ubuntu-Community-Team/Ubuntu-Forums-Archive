---
title: "user ID 1000 Fresh re-install Lucid ?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by bluestreak patriot on 2011-06-28
I just performed a fresh destructive install of Ububtu 10.04.2 LTS over an insisting dual-boot installation of 10.04.1 LTS and Windows XP.

During the install process the setup utility recognized two existing users "Administrator" and "Paul". 

The only error message I received was that there was a "Broken Package state" /usr/bin/dpkg, so as soon as the install completed I restarted the system and booted into the "repair" option in the Grub menu.

I did a repair packages a s was advised there were 3 new packages to install (linux-headers 2.6.32-32, linux (generic) 2.6.32-32 and linux-image 2.6.32-32.

Also there were 131 updates to install as well.  I proceeded with the update and all seems to have gone well.

Question:
During the install process i was asked for my "name" and to accept or modify the machine name.  I used my first name - paul.

When I go in to manage Users & Groups, Paul is the only user listed and my User ID is 1000, which if I remember correctly is gives me Administrative privileges.   What  is the easiest way to correct this?  

I am assuming I should have selected the name "Administrator" during install, then setup an additional lower level user "Paul" for my normal use.

I have done nothing else at this point, so if would be very easy for me to do a clean re-install and update using "Administrator" as the initial user.

Any suggestions would be appreciated.

Cheers

---

### Post by JC Cheloven on 2011-06-28
I'd say you're fine. My user id is 1000 in all my machines. 

If you want to create an additional unprivileged user (so that he's unable to run sudo) you can do that with command "adduser", or from the "users and groups" gui in the admin menu.

---

### Post by oldfred on 2011-06-28
You are not really the administrator unless you preface a command with sudo. In windows everyone is administrator unless you take away privileges. 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bluestreak patriot on 2011-06-28
Thank you.  I understand.  It's OK to let me be me, so to speak, which really makes life easier since I am the only user on this machine and login is required.  

It's running great.

I was able to restore my Evolution backup without problems, although it would be nice to see a "wait-working" message displayed on the restore.

Actually configured Firefox correctly this time from the get-go for java and flash support.  For anyone that may be interested:

Java support - use Synaptec Package Manager to install "OpenJDK Runtime Environment (IcedTea6 1.9.8) (6b20-1.9.8-0ubuntu1~10.04.1)"

Flash support - use Synaptec Package Manager to install "flashplugin-installer
Adobe Flash Player plugin installer 10.3.181.26ubuntu0.10.04.1"

I used [www.dslreports.com](www.dslreports.com) / Tools / Speed Tests to verify both of these.

For recording videos from YouTube, etc. I found the Firefox Extension "Easy YouTube Video Downloader version 5.1" to work very well.  

Thank you your help. I hope some of the additional information I provided will be of some help to someone else.

I will mark this as solved.

Cheers

---

### Post by oldfred on 2011-06-28
Glad you have it working.

When I do a clean install I like to have backups of /home, some files I may have manually edited in /etc (I  copy them into /home so my normal backup includes them) and a list of installed apps.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

