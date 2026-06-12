---
title: "Installed fglrx and killed Jaunty"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by sturdy on 2009-08-27
I've been playing with Jaunty since it came out and have finally killed it. I no longer have a usable logon screen. I have the ATI 3850 graphics card and was previously (happily) using compiz with the proprietary ATI driver which was downloaded from the AMD site. All was good until I tried to re-activate compiz which had been dead for a few days (I think due to a system update). Of course, when I changed the appearance selection, it wanted to install the fglrx driver and I (unthinking) said yes. After fglrx was installed, I am now unable to get the logon or any other usable screen.

Can someone tell me how to remove the fglrx driver when I cannot logon? My plan is then to reload the latest ATI driver which has some fixes for Jaunty. TIA...

---

### Post by fela on 2009-08-27
Start up the operating system, and when it's booted up to what would be the login screen, press ctrl+alt+f2. When you see a terminal (press the combo again if it doesn't come up in a few seconds), you can login there. From there you can just do:

```
sudo apt-get remove packagename
```

I'm assuming the package name is fglrx. You can decide that though :)

---

### Post by NoaHall on 2009-08-27
Boot into repair mode and type "sudo apt-get remove --purge xorg-driver-fglrx"

---

### Post by sturdy on 2009-08-27
Thanks fela, I'll try that tonight after work. Much appreciated...

---

### Post by sturdy on 2009-08-27
Thanks NoaHall.  Noobie here...is repair mode the same as recovery? Recovery has the same problem. I assume the command will also work with ctl+alt+F2 as fela provided?

---

### Post by NoaHall on 2009-08-27
Oh, yeah, recovery, that's what I meant (Y) Yes, it will work anywhere, but if you boot into recovery, and select root, it will work too.

---

### Post by fela on 2009-08-27
> **sturdy said:**
> Thanks NoaHall.  Noobie here...is repair mode the same as recovery? Recovery has the same problem. I assume the command will also work with ctl+alt+F2 as fela provided?

yes repair mode == recovery mode. In recovery mode it'll give you a list of options. You want the root shell prompt (once you're in as root you can forget sudo, you have system wide permissions so you can just do apt-get remove). Also you don't need to press ctrl+alt+f2 once your in a root shell. The key combo is actually for switching ttys, which are virtual terminals.

---

### Post by sturdy on 2009-08-29
I'm back...using recovery mode I was able to "sudo apt-get remove --purge xorg-driver-fglrx" but I still have no login screen. ctl+alt+F2 does nothing. I see no way to load the proprietary graphics driver but I clearly need to do something to get the login screen back. One more point; I see the Ubuntu splash screen as it tries to boot, then the screen blows up with garbage graphics and nologin screen. Any ideas?? Thanks...

---

### Post by NoaHall on 2009-08-29
Load into recovery and then run "sudo apt-get update" and see if there is anything that can be uninstalled. If so, uninstall it.

---

### Post by sturdy on 2009-08-29
Hi NoaHall, thanks again. I tried update and there were a few things removed but it didn't give me anything usable on reboot. I also tried the auto graphic fix that is the last recovery menu choice...no joy.

---

### Post by NoaHall on 2009-08-29
Hm. Do you have a onboard video card? Try removing your ATI one, and use the onbord one instead.

---

### Post by sturdy on 2009-08-29
No onboard video but the card works well in WinXp. It's beginning to look like I'm toast and reload might be the simplest route.

---

### Post by NoaHall on 2009-08-29
I had this error after trying out my ATI - but the problem is, ati isn't well supported on Linux. I would reinstall if I was you, because I've run out of ideas :) Good luck

---

### Post by sturdy on 2009-08-29
Thanks...I haven't had an issue with the ATI driver. This only happened when I mistakenly activated the fglrx driver. Strangely, I now see part of a Solaris logo where the logon screen should be. OpenSolaris is installed on another partition of the same drive. I used GParted to look at the partitions and I seem to now have an extra ext3 partition. Ubuntu/Linux and OpenSolaris may not play well together. I think I'll try removing OpenSolaris first since I don't use it.

---

### Post by randcoop on 2009-08-29
I think all you need to do is restore your xorg.conf file.  While you're on the command line, change into the /etc/X11 directory (```
cd /etc/X11
```).  

From there, you'll need to run an editor as root.  You can sudo nano...what you want to do is look at the xorg.conf file that was backed up when you made the error and installed fglrx.  It will be xorg.conf with a long number (signifying date and time of backup) after it.  One of them will be the generic xorg.conf file that Ubuntu made for you when you first installed.

When you have one that doesn't have fglrx as the driver, you can simply copy it to xorg.conf, overwriting the bad xorg.conf file.  

Then reboot or you can even just try the command ```
startx
```.  It should just work.

---

### Post by sturdy on 2009-09-10
Resolved...just to close the loop, here is the link:

[http://ubuntuforums.org/showpost.php?p=7898359&postcount=17](http://ubuntuforums.org/showpost.php?p=7898359&postcount=17)

---

