---
title: "Where is HPlip located in Kubununtu jaunty?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by cptrohn on 2009-04-29
Anybody know?  I'm trying to setup my HP WiFi printer and can't for the life of me find where hplip is located in jaunty....

I checked the kpackagekit and it is showing hplip is already installed... I just can't find it for anything in jaunty to save my life...

---

### Post by Didius Falco on 2009-04-29
Check under Accessories if you haven't already. If it's still MIA have a read through this thread:

[http://ubuntuforums.org/showthread.php?t=1108108](http://ubuntuforums.org/showthread.php?t=1108108)

BTW, I'm originally from SE lower Michigan, and I've driven through BFE Indiana dozens of times. ;-)

---

### Post by cptrohn on 2009-04-29
Ok.... I can print while the printer is hardwired to the computer no problems at all...


But I can't seem to print with the WiFi option?  So HPlip is there, I just can't figure out how to get the WiFi part of it working.....

Is there any documentation from conical about how to do this?

---

### Post by SuperSonic4 on 2009-04-29
You may need to set it up which can be done via ```
sudo hp-setup
```

---

### Post by cptrohn on 2009-04-29
> **SuperSonic4 said:**
> You may need to set it up which can be done via ```
sudo hp-setup
```

Yes, I have done the set-up through hplip, but when I search for the printer in the network devices it doesn't show up at all... I do have the printer connected succesfully to the WiFi access point though.....


For some reason it just isn't showing up in the devices for wireless through hplip.

---

### Post by gn2 on 2009-04-29
Have you installed hplip-gui?
It was left out in older versions, don't know about 9.04....

---

### Post by cptrohn on 2009-04-29
> **gn2 said:**
> Have you installed hplip-gui?
It was left out in older versions, don't know about 9.04....

No I have not.... What I have showing as being installed is;

hplip-3.9.2-3ubuntu4(i386)
HP Linux Printing and Imaging System(HPLIP)


hplip-data-3.9.2-3ubuntu4(all)
HP Linux Printing and Imaging...(with the WiFi, it works fine connected to the USB port)



Then it shows 3 other available packages as being uninstalled... one is listed as being for debugging, another for documentation and the last one for GUI utilities.

Do I need to install the other packages to get it to work?

---

### Post by gn2 on 2009-04-29
I've no idea if wireless printing will work, but the hplip-gui package is well worth installing.

---

### Post by cptrohn on 2009-04-29
> **gn2 said:**
> I've no idea if wireless printing will work, but the hplip-gui package is well worth installing.

I installed the GUI and the other packages as well just to have them all... but still nothing working with the WiFi... (grrr) it doesn't recognize the printer at all.  It does through CUPS and i tried to set it up through there, but it asked for a username/password and kept coming back saying there was an error?  They want my systems username/password right?  I've never tried to use CUPS before so I am learning this one... LOL

---

### Post by gn2 on 2009-04-29
The username/password will likely be the ones for the printer...?

---

### Post by cptrohn on 2009-04-29
> **gn2 said:**
> The username/password will likely be the ones for the printer...?

This one has me completely stumped... LOL I have no idea at all on this new printer/new OS...


I can still use the printer completly with the USB....  I will just keep messing around with it until i figure out what is up with the WiFi....  but I'm at a loss.

---

### Post by cptrohn on 2009-04-29
Man I have been digging all over google etc, and don't seem to be able to find an answer to this one...  I put up a post about it on the HP website and maybe they can come up with an answer to this... I guess if i don't get it resolved by tomorrow I will try and get in touch with HP's tech support to see if they have a known issue with this or not....

---

### Post by cptrohn on 2009-04-29
OK, heard back from an HP tech on this today.....

Pretty much we don't know why this is happening and it's your problem not ours was their answer to it.

---

### Post by dickeybird on 2009-04-30
Although I do not have an icon for HP or HPLIP, my Officejet 7410 does print wirelessly after running "sudo hp-setup" from terminal. It took me months to discover that if I also wanted to secure my wireless network including the wireless printer, I must configure the hp printer via a browser. On my system I type "192.168.1.130" in the browser address to configure the wireless printer.:)

---

