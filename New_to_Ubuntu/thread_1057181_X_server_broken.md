---
title: "X server broken"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by marcusesses on 2009-02-01
Hi all, 

Wonder if someone can offer some advice. I recently ran some updates, though not all of them could be installed, unfortunately. When I rebooted my computer, I received an error message saying that there was some kind of error in the X-server (I can't remember exactly what it said), and when i attempted to login, I was met with the white screen of death. 

when I run lshw -C video, I am met with this output

```


-display:0 UNCLAIMED
.....

-display:1 UNCLAIMED
.....


```

When I run in failsafe GNOME mode, I still get the WSOD, and the same thing happens when I boot using a different kernel. 

Does anyone have any suggestions? 

Also, the output of xorg.conf (I've truncated some of the output, and only put the relevant information, since I can't copy/paste)

```


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
     Identifier    "Configure Monitor"
EndSection

Section "Screen"
     identifier     "Default Screen"
     Monitor      "Configured Monitor"
     Device      "Configured Video Device"
EndSection



```


 Thanks in advance.

---

### Post by gettinoriginal on 2009-02-01
have you tried this?:  Or does it WSOD on grub also?

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by marcusesses on 2009-02-02
> **gettinoriginal said:**
> have you tried this?:  Or does it WSOD on grub also?

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter


I tried that initially, and it spits out the following when I "Repair Broken Packages"

```

Failed to fetch http://  ... (etc.)
Could not resolve ... (etc.)

```

```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

When I run "apt-get update", it does not update, but gives  similar error.

When I enter "Try to fix x-server", it says it's overwriting old settings....but when I resume normal boot, the problem is still there.

---

### Post by gettinoriginal on 2009-02-02
At the grub splash, hit escape and choose the option to open Command Line, then run these in terminal, one at a time.  If you are not running intrepid, edit the first one for your distribution.

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```
```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by marcusesses on 2009-02-03
> **gettinoriginal said:**
> At the grub splash, hit escape and choose the option to open Command Line, then run these in terminal, one at a time.  If you are not running intrepid, edit the first one for your distribution.

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```
```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```

When I run those commands at the command line from the grub splash, it says 

```

Error 27: Unrecognized command

```

When I run those commands at the terminal using my current kernel, it says 

```

Resolving www.medibuntu.org...failed: Name or service not known. 

wget: unable to resolve host address 'www.medibuntu.org"

```

The second command gives...

```

gpg: no valid OpenPGP data found.


```

??

---

### Post by marcusesses on 2009-02-04
bump

---

### Post by gettinoriginal on 2009-02-04
Sorry I was so slow to respond, had surgery yesterday, and just now getting back on here.
Check your software sources and make sure that your updates read as mine do:
[ATTACH]102188[/ATTACH]

---

### Post by marcusesses on 2009-02-04
> **gettinoriginal said:**
> Sorry I was so slow to respond, had surgery yesterday, and just now getting back on here.
Check your software sources and make sure that your updates read as mine do:
[ATTACH]102188[/ATTACH]

I can't check my software sources because I'm getting the WSOD...how would I check them using the command line?

Also, it's wierd, because I get the WSOD (with either failsafe GNOME, or regular GNOME), but when I press <alt> + <ctrl> + <delete>, it briefly displays my background before it spits me back out to the log-in screen.

---

### Post by gettinoriginal on 2009-02-04
OK, at the CL
```
 startx 
```
then when/if that fails, try
```
 sudo dpkg --configure xserver-xorg 
```

If that fails, you can check your sources.list here:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by marcusesses on 2009-02-05
> **gettinoriginal said:**
> OK, at the CL
```
 startx 
```
then when/if that fails, try
```
 sudo dpkg --configure xserver-xorg 
```



When I run "startx", i get this

```

X: warning; process set at priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again

```

So I'm assuming that failed...

The next command also fails, with the line

```
 dpkg: error processing xserver-xorg (--configure):
package xserver-xorg is already installed and configured
Errors were encounter while processing:
xserver-xorg
```

> If that fails, you can check your sources.list here:
```
sudo gedit /etc/apt/sources.list
```

What should I be looking for in my sources list? Also, how would I install any updates without an internet connection? (unless my computer automatically detects a wired connection)....

Also, thanks for your help so far :P

---

### Post by gettinoriginal on 2009-02-05
Ok, went back and reviewed what we have tried, so here is my xorg.conf file.  If you are running nvidia, then try to edit your xorg file to match
[ATTACH]102253[/ATTACH]
```
sudo gedit /etc/X11/xorg.conf
```.  Right now we are just trying to get your screen back, then we will go back to the update issue.

---

### Post by alphaniner on 2009-02-05
> Failed to fetch http://  ... (etc.)
Could not resolve ... (etc.)

> 

Resolving [www.medibuntu.org...failed:](www.medibuntu.org...failed:) Name or service not known. 

wget: unable to resolve host address 'www.medibuntu.org"

Based on this output it looks like you have some network issues, ie. no internet connectivity.  This may have caused the initial problems during the update, but it could just be because network-mangler - err... network-manager - doesn't run in recovery mode.  When you boot to the recovery terminal try 'ping google.com' or some such.

---

### Post by marcusesses on 2009-02-05
> **gettinoriginal said:**
> Ok, went back and reviewed what we have tried, so here is my xorg.conf file.  If you are running nvidia, then try to edit your xorg file to match
[ATTACH]102253[/ATTACH]
```
sudo gedit /etc/X11/xorg.conf
```.  Right now we are just trying to get your screen back, then we will go back to the update issue.

Ok, so when I rebooted, the Ubuntu load screen  (after BIOS) was all fuzzy and wierd colors...now it says "Ubuntu is running in low-graphics mode"...I just put "Continue"......and it takes awhile to get to the log-in screen....But I can log in (with a GUI!) in failsafe GNOME mode. So (thankfully) that is sorted out now.

But this happened to me about a month ago as well (check out my history)..and I can't for the life of me remember what I did to resolve it, but when I finally did, the same thing happened....it takes forever to get to the log-in screen and it tells me that Ubuntu is running in low-graphics mode, even though there's no noticeable difference in graphics performance...hmmm..


> **alphaniner said:**
> Based on this output it looks like you have some network issues, ie. no internet connectivity.  This may have caused the initial problems during the update, but it could just be because network-mangler - err... network-manager - doesn't run in recovery mode.  When you boot to the recovery terminal try 'ping google.com' or some such.

That problem is resolved now, so hopefully I can connect to the internet...though I use WICD, not network manager.


Also, maybe I had swept this under the rug, but when I run

```

sudo apt-get update

```

none of the updates actually occur. Rather, I get this message

```


W: Duplicate sources.list entry http://archive.ubuntu.com intrepid/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid_mutliverse_binary_i386_Packages)
W: You may want to run apt-get update to correct these problems

```

I've been updating through the Update Manager since I installed Ubuntu (~6 months ago.).....If that helps.

So the update that initially led to this X problem probably started there, but I'm not sure how...

---

### Post by marcusesses on 2009-02-05
(a bit of an unrelated question)

I think the key component that was missing in the xorg.conf file was the in the "Device" section, I had no driver information!
I initially added some other lines that were missing, but when I ONLY add the driver "ndivia" line, I get a nice looking desktop. 

So my question is why would the update have changed my configuration file in the first place?

---

### Post by gettinoriginal on 2009-02-05
Don't know the reason, but sometimes if there is a driver update, it will throw mine for a loop.  But if your xorg file is now how you want it, then do this now:
Xorg Backup  
```
gksudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Then if it messes up again, do this:
Xorg Restore
```
sudo cp -f /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by marcusesses on 2009-02-07
Yeah, I'm a bit curious why it would get rid of the "driver" setting. Oh well...Thanks for your help!!

---

