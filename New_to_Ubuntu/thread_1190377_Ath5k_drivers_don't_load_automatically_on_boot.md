---
title: "Ath5k drivers don't load automatically on boot"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-06-17
I just recently installed madwifi-tools via:

```
sudo apt-get install madwifi-tools
```

Because I needed it for some WEP cracking program to work correctly.

Worried that this might somehow interfere with my atheros drivers, I posted a thread about the issue before going ahead with the install: [http://ubuntuforums.org/showthread.php?t=1186430](http://ubuntuforums.org/showthread.php?t=1186430)

but I got no response. I went ahead with the installation, and wound up having to remove the madwifi-tools package because it **did** in fact interfere. 

After removing the package, every time I boot up my computer, I have to manually load the ath5k drivers and load the wlan0 interface:
```
sudo modprobe ath5k
sudo ifconfig wlan0 up
```

is there some way to fix this to how it was before, so i don't have to issue these commands every time i restart?

thanks ;)

---

### Post by munky99999 on 2009-06-17
Completely remove madiwifi and not just remove.

Also u probably needed to switch over the drivers in the admin hardware drivers. Even though you removed madwifi.. that's perhaps still actively blacklisting.

Thusly a file /etc/modprobe.d/blacklist-ath_pci.conf is still actively being used.

also /etc/modules file wouldnt hurt having ath5k in there.

---

### Post by asuastrophysics on 2009-06-17
hey thanks! :D

in the directory /etc/modprobe.d/

i found a file called "madwifi.conf"

inside it there was a line that was uncommented that read "blacklist ath5k"

i just deleted the whole madwifi.conf file. that should fix it. i'll let u know when i reboot next. pretty sure that was the culprit though. :)

---

### Post by asuastrophysics on 2009-06-18
yup just rebooted. works perfectly ;)

thanks again.

---

### Post by asuastrophysics on 2009-06-24
[Solved]Re: mark post as solved

---

### Post by porchrat on 2009-06-24
> **asuastrophysics said:**
> [Solved]Re: mark post as solved

I don't think you can mark threads solved anymore, I believe it was removed a while back.

If it hasn't then for the love of God show me how to do it again because it annoys me leaving solved threads open like that.

---

### Post by shifty21 on 2009-07-23
> **asuastrophysics said:**
> hey thanks! :D

in the directory /etc/modprobe.d/

i found a file called "madwifi.conf"

inside it there was a line that was uncommented that read "blacklist ath5k"

i just deleted the whole madwifi.conf file. that should fix it. i'll let u know when i reboot next. pretty sure that was the culprit though. :)

I'm having the same problem...same scenario. Upon hard reboot the wifi doesn't work. I have to use the same commands to start the ath5k driver. I followed your advice (thanks) and was going to delete the madwifi driver from the system. However, the file won't delete! What am I missing?

---

### Post by spcwingo on 2009-07-23
> **shifty21 said:**
> I'm having the same problem...same scenario. Upon hard reboot the wifi doesn't work. I have to use the same commands to start the ath5k driver. I followed your advice (thanks) and was going to delete the madwifi driver from the system. However, the file won't delete! What am I missing?

You need to run Nautilus as root to be able to delete that file.  To run Nautilus as root press ALT+F2 and that will bring up a run prompt.  Then enter:

```
gksu nautilus
```

---

### Post by shifty21 on 2009-07-23
> **spcwingo said:**
> You need to run Nautilus as root to be able to delete that file.  To run Nautilus as root press ALT+F2 and that will bring up a run prompt.  Then enter:

```
gksu nautilus
```

Thanks a bunch. That worked.

---

