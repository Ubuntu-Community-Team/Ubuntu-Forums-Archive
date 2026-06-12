---
title: "64 bit flash plugin - Firefox 3.5.2"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by expatCM on 2009-08-04
I have just upgraded to Firefox 3.5.2 and flash stopped working.

So I downloaded the latest 64 bit flash plugin from the Adobe site and unpacked.  I created a directory in the Home directory at /username/.mozilla/plugins and copied the .so file there.

I restarted Firefox and entered about:plugins in the address bar.  No plugins are found.

I have taken a look on google and what I have done appears to be correct.  Some people report problems with amd64 which happens to be what I am running but I do not see any suggestions of how to proceed.

I have uninstalled through synaptic the existing flashplugin and the swf files ...  but no change.

Any suggestion what may be wrong?

---

### Post by Ubun2 Us3r on 2009-08-04
I had this same problem and this worked for me
[http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177)

---

### Post by expatCM on 2009-08-04
Nice link, thank you.

It did not work for me.  The script ran but then I got the following error messages.....

```
libflashplayer.so
cp: cannot stat `install_flash_player_10_linux/libflashplayer.so': No such file or directory
nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin

```

---

### Post by prkos on 2009-08-04
I got the same message at the end of the install process

Finally I just installed from synaptic and copied the /usr/lib/flashplugin-installer/libflashplayer.so into .mozilla/plugins and now flash works :)

---

### Post by expatCM on 2009-08-04
out of total despair I just copied the libflashplayer.so file to several locations ....  basically if it looked good then put a copy there.  I started the browser again and ....  amazing, it works :)

At some stage I will rename then delete files to find out which one is being used ...  but not yet ...

---

### Post by LaPalida on 2010-03-07
Found the solution:

from here [http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html) in comment 156 
> 
James Shields 01.16.10 at 2:22 pm

    Thanks for the script.

    Had to tweak in slightly because libflashplayer.so ended up in my home directory rather than a install_flash_player_10_linux/ subdir.

    Thanks!

    James

- just make that sub dir in the home folder
- move the .so file into it
- re-run the script

the error occurs because in the script it's pointing to a directory that does not exist or isn't created.

OR

you can just edit the script and remove the offending directory.

the line **sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/**
should be changed to **sudo cp libflashplayer.so /usr/lib/mozilla/plugins/**

---

