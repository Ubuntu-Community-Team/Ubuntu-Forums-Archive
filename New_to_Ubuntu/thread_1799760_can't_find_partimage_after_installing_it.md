---
title: "can't find partimage after installing it"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by bobmac on 2011-07-08
Folks,

I installed partimage, after installation, however, I can't find it so that I can get it into one of the menus.

I've tried sudo apt-get install partimage-gtk

but all I get is the message 'E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?'

Any help to sort this out would be appreciated.

Regards,

Bob

---

### Post by sikander3786 on 2011-07-08
>  'E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?'

This error means that some other package manager is running currently like Software Center, Synaptic, Update Manager, Jockey or another instance of apt-get. Let it finish its job and quit and then try the command again.

Or, you might need to relogin if the error persists.

BTW, I couldn't find a package named 'partimage-gtk'.

You can start 'partimage' by pressing Alt + F2 and typing 'partimage' (without quotes).

---

### Post by bobmac on 2011-07-08
sikander3786

Rebooted my machine and tried the sudo... again. No joy. Then tried the Alt+F2 partimage and nothing happened.

Regards,

Bob

---

### Post by pjd99 on 2011-07-08
Go to a terminal, type "part" (no quotes) and press tab a few times. If partimage shows up, its installed.

That dpkg lock message probably means you have synaptic/aptitude open while trying to apt-get. Only one program can access the package management system at a time. If you don't have a package manager open, you can do the following:
sudo rm /var/lib/dpkg/lock

If partimage-gtk is already installed, apt-get will do nothing.


If you are just trying to get it into the menus, find a program in the menu that is in the right location, find its /usr/share/applications/progname.desktop file and make one that is similar.

Example attached. chown the file and change its permissions, rename it to partimage.desktop (the .desktop extension isn't allowed as an upload here) then place it in the /usr/share/applications directory. The icon may not exist, so you might need to specify a new one. It should then show up in "System Tools' or similar.


Oh, do these repo's even exist anymore. 8.04 is quite old. I know it was LTS, but thought the support had been dropped for desktop...

---

### Post by Mark Phelps on 2011-07-08
Just so you know ... PartImage will not work with the newer Ext4 Linux Filesystem -- which has been the default filesystem for Ubuntu for several releases now.

So, if you installed it to manipulate files in recent ubuntu version ... you wasted your time.

---

### Post by bobmac on 2011-07-08
Mark,

Many thanks for the info. At least I now know what's wrong. 

Bob

---

