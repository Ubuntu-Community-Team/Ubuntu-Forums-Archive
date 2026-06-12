---
title: "[SOLVED] Broadcom 4311 wireless"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by xecure on 2008-04-29
hi, after freshly installing 8.04 i saw that my wireless wasn't working so I went over to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc") to try and get my wireless to work. Fortunately it was detecting wireless broadcasts (don't know if it works because I can never connect to wireless from my dorm anyways, they are just here) 

But my problem is that not that it detects wireless connections it cannot detect any wired connection.

I ran ```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local

``` in terminal hoping I wouldnt have to set up the driver everytime I rebooted, but now that I have done that my wired connection cannot be detected

(I posted this in another forum by mistake: [http://ubuntuforums.org/showthread.php?p=4830669#post4830669](http://ubuntuforums.org/showthread.php?p=4830669#post4830669) Moderators can delete if they want)

---

### Post by xecure on 2008-04-30
bump..

---

### Post by xecure on 2008-04-30
second bump

---

### Post by Ayuthia on 2008-04-30
You might try to do the following:
```
sudo modprobe b44
```
I am guessing that the b44 driver is your wired driver.  If that is the case, you could edit your /etc/rc.local file to load the b44 driver after ndiswrapper.  The b44 driver should automatically load the ssb driver, but I could be wrong.

---

### Post by kevdog on 2008-04-30
Can you post lspci -nn?

---

### Post by xecure on 2008-05-01
```
sudo modprobe b44
``` seemed to have worked for me. If I have problems connecting again (like after rebooting or something I'll post here again)

*edit*
After rebooting my laptop I have to re-enter ```
sudo modprobe b44
``` to make it work. Is there anything I can do so that I don't have to re-enter every time I reboot?

---

### Post by Ayuthia on 2008-05-01
> **xecure said:**
> ```
sudo modprobe b44
```
After rebooting my laptop I have to re-enter ```
sudo modprobe b44
``` to make it work. Is there anything I can do so that I don't have to re-enter every time I reboot?
Yes.  The information in your original post added information to /etc/rc.local. What you need to do is edit that file and replace modprobe ssb (not rmmod ssb)with modprobe b44.  To edit the file, you will need to do something like (or use your favorite editor in gksudo/sudo/root mode):
```
gksudo gedit /etc/rc.local
```

The /etc/rc.local script is one of the files that is run at startup.  What is being done here is that you are removing the b43, b44, and ssb modules.  Then you add ndiswrapper and b44 (which should load ssb automatically since it needs it)

---

### Post by gerben1 on 2008-05-01
yes the command you ran
```

echo -e '\necho -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local

```
has put a few lines in the file /etc/rc.local, namely these lines:
```

#hardy ssb bug-fix
rmmod b43
rmmod b44
rmmod b43legacy 
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
```
The lines with rmmod unload a module (i.e. "rmmod b44" unloads module b44).
The line with modprobe load a module (i.e. "modprobe ssb" loads module sbb).
So what the script does is unload a bunch of modules and the load a few of them again. Since you want to load b44 again you can just add a line "modprobe b44" so that module b44 will also be loaded again when rc.local gets executed (i.e. when you reboot).

to add that line:
```

sudo gedit /etc/init.d/rc.local

```
add the line: modprobe b44
and save it.

---

### Post by xecure on 2008-05-01
thanks guys that did the trick for me

---

