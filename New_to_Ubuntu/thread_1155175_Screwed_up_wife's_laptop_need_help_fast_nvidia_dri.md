---
title: "Screwed up wife's laptop need help fast nvidia driver / wireless driver gone..."
date: 2009-05-10
forum: New to Ubuntu
---

### Post by crjackson on 2009-05-10
Okay,

Thought I was smart and would do some updates while the wife is at work. Lost nvidia driver, wireless, and automatic hardware driver detection. been trying for 3 hours to get it working.

Help fast please. She's going to give me hell if she finds out...

---

### Post by nothingspecial on 2009-05-10
Details please. I know where your coming from.  :)

---

### Post by lanceps on 2009-05-10
there is an option for nvida drivers in the adminstation section

---

### Post by Didius Falco on 2009-05-10
> **crjackson said:**
> Okay,

Thought I was smart and would do some updates while the wife is at work. Lost nvidia driver, wireless, and automatic hardware driver detection. been trying for 3 hours to get it working.

Help fast please. She's going to give me hell if she finds out...

If you didn't purge the packages, they'll still be in the cache.try doing a few searches through the cache by using ```
sudo apt-cache search packagename
``` with packagename being what you are looking for. You can use wildcards too, so you could, for example, search for  ```
sudo apt-cache search nvid*
``` for the nvidia driver.

With a little creative searching, you should be able to retrieve what you lost fairly quickly, and the configuration files should be intact - again, unless you purged them.

I hope this helps...Good Luck!!

Regards,

Didius

---

### Post by crjackson on 2009-05-10
I just made matters worse... I tried using envy and now it won't boot to anything but a black scree.

It's an HP dv 2000 series laptop with a broadcom wireless card and an nvidia go 7150M.

If I could just get the damn hardware drivers thing working... How in the hell did I do that? 

I got to a desktop in recovery mode... I need to know how to reinstall the hardware driver detection so I can get wireless back asap

---

### Post by Didius Falco on 2009-05-10
**jockey-gtk**  and **jockey-common** are the **Hardware Drivers** packages, so ```
apt-get install jockey
``` should get that back, and that might trigger the others - do you have a net connection on that laptop?

If not, then the cache search continues to be the best bet. Give us some details on the wireless if you can...

Regards,

Didius

---

### Post by crjackson on 2009-05-10
okay, i got wireless back. It wasn't jockey it was the restricted modules. I enabled the restricted nvidia driver and it installs but boots me to low graphics mode...

---

### Post by crjackson on 2009-05-10
Okay, the hardware driver applet says the nVidia driver is in use, but it boots to low graphic mode and tells me to reconfigure. Tried several times, now what?

---

### Post by crjackson on 2009-05-10
Is there anybody who can help me fix this graphics issue.  I'm begging please...

---

### Post by durand on 2009-05-10
```
sudo gedit /etc/X11/xorg.conf
```
If there is a vesa or something present, change it to nvidia. If it isn't present, add something like this:
> 
Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


---

### Post by crjackson on 2009-05-10
> **durand said:**
> ```
sudo gedit /etc/X11/xorg.conf
```
If there is a vesa or something present, change it to nvidia. If it isn't present, add something like this:

No it's exactly like the one you posted.

---

### Post by crjackson on 2009-05-10
Is there no way to fix this without a re-install?

---

### Post by durand on 2009-05-10
Hmm, you could try running nvidia-xconfig with sudo. That should reconfigure xorg for nvidia however I have no idea its booting into safe graphics mode for you. Check the boot line in grub, it may have extra options which you don't want.

---

### Post by crjackson on 2009-05-10
I guess there's no answer to fix this.

---

### Post by crjackson on 2009-05-10
Can no one tell me how to fix this?

---

