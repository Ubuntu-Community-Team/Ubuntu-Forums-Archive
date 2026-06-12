---
title: "Lost wlan0 after update (new to this)"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by scottsanpedro on 2006-10-13
Hi,
New to all this but really getting into it.
I have managed to get my Belkin Pre-N wireless adapter running last night and was well chuffed, I used ndiswrapper etc. I have since run through a load of updates on my laptop using [http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)
I then ran 
```
sudo aptitude install linux-686
```
I was then asked to re-boot. On reboot I lost wlan0 and am getting errors like;
SIOCSIFADDR: No such device
Seems its gone. Any chance anyone will know how I get this back. Was working fine :(
Many thanks
Scott

---

### Post by nyinge on 2006-10-13
I believe your kernel was updated.  You'll have to reinstall ndiswrapper, which is a kernel module.

Go inside ndiswrapper (if it's still there, otherwise download and extract it again), and run the following commands to install/insert the module:

```
sudo make uninstall
```
to completely wipe out the previous installation.

```
sudo make && make install && modprobe ndiswrapper
```
to get the ndiswrapper module installed into the kernel.

Finally, configure wlan0 with your favorite tool.  I personally like to use the commnand-line...

```
iwconfig wlan0 essid ESSID
```
to set your SSID.

[optional]
```
iwconfig wlan0 key YOUR_WEP_KEY
```
to set your wep key, if there's one.

```
dhclient wlan0
```
to get an ip from your dhcp router.

Hope this helps.  :)

---

### Post by scottsanpedro on 2006-10-13
Many thanks.
I will try this when I get home after work and let you know.
Cheers

---

### Post by scottsanpedro on 2006-10-13
I can't seem to re-install it. Getting

```
install: cannot create regular file `/lib/modules/2.6.15-27-686/misc/ndiswrapper .ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/scott/Desktop/ndiswrapper-1.25/driver'
make: *** [install] Error 2
```

I am slightly confused. There is the normal 1.8-Oubuntu2 program in Synaptic. I also have a later version of ndiswrapper-1.25 which I'm trying to use.
1. Not sure how to clear the old one completely 
2. Compile the new one and make it work

Many thanks for your help so far
Scott

---

### Post by scottsanpedro on 2006-10-13
After messing around and finally reseating the adapter its come back up. Its seems happy now. Thanksl for the help

---

### Post by diepruis on 2006-10-13
BTW: Your previous problme was because you didn't run "make install" with root privaleges. It should be:

```

sudo make install

```

---

### Post by scottsanpedro on 2006-10-13
of course..understand. getting there :)

---

