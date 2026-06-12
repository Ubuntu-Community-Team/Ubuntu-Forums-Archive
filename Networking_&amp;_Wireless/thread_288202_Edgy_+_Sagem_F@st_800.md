---
title: "Edgy + Sagem F@st 800"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by SledgeHammer_999 on 2006-10-29
hi guys. how can I make my Sagem F@st 800 modem work under edgy? I used eagle-usb.2.3.3 under dapper and it workded perfectly. But now I can't compile it under edgy. Can you help me?

thanks in advance.

---

### Post by khaledaboualfa on 2006-10-31
Hey all, I'm having troubles with the external Sagem modem as well. Problem is I actually had it working before I upgraded as well. From this How to:

[http://www.ubuntuforums.org/showthread.php?t=201127&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=201127&highlight=sagem)

I get everything sorted out until I have to run the following:

```
$ sudo modprobe ueagle-atm
```

Once I do that I get the following error message:

**"FATAL: Error inserting ueagle_atm (/lib/modules/2.6.17-10-generic/kernel/drivers/usb/atm/ueagle-atm.ko ): Unknown symbol in module, or unknown parameter (see dmesg)"**

Now there are two modules the 2.6.17-10-generic and the 2.6.17-10-386 which has got the extra folder.

Reading from the following page:
[http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc](http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc)

It would seem that the problem might be to do with the Kernel? Any ideas about how to go about this? I could reinstall ubuntu and then not upgrade the Kernel (I downloaded a slightly, by one day, copy of edgy and things seem to have broken with it).

Any ideas would be well appreciated.

---

### Post by aces21 on 2006-10-31
SledgeHammer_999 - did you find my howto [here]("http://www.ubuntuforums.org/showthread.php?t=201127")? It works for me with both Dapper and Edgy, so long as you have the linux-headers and build-essential as it mentions.

khaledaboualfa - what output do you get from ```

$ dmesg|grep eagle
$ sudo lsmod | grep eagle
```

---

### Post by khaledaboualfa on 2006-10-31
Hey there,when I type in 
```
dmesg|grep eagle 
```

I get several lines returned which seem to be the same however the first numbers change (as it's on another machine to what I'm writing this comment on this is kinda what I'm getting:

```
[17180773.092000] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[17180773.092000] ueagle_atm: Unknown symbol usbatm_usb_probe
```

and this repeats like 5 times or something.

I get nothing back when I type in 
```
sudo lsmod | grep eagle
```

thanks

---

### Post by SledgeHammer_999 on 2006-10-31
yes I've seen your tutorial but I wanted to install eagle-usb because it has easier configuration. But I'll give a try to ueagle, if I find what are the values for VP.VC for Greece. Do you know what are they? Or maybe could you tell me how to find them?(in Windows are they stored somewhere?)

---

### Post by aces21 on 2006-11-03
> **khaledaboualfa said:**
> Hey there,when I type in 
```
dmesg|grep eagle 
```

I get several lines returned which seem to be the same however the first numbers change (as it's on another machine to what I'm writing this comment on this is kinda what I'm getting:

```
[17180773.092000] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[17180773.092000] ueagle_atm: Unknown symbol usbatm_usb_probe
```

and this repeats like 5 times or something.

I get nothing back when I type in 
```
sudo lsmod | grep eagle
```

thanks

It looks like ueagle-atm might be trying to use the usbatm module built into the kernel, rather than the one that comes with ueagle. Did you definitely remove the module usbatm from /lib/modules/'uname -r'/kernel/drivers/usb/atm/usbatm.ko. I'd check its not there and if it is, then remove it. If it is there you may need to unload the module first

```
$ sudo modprobe -r eagle-usb
```

Then I'd go back to your ueagle-atm folder and do make && make install again. I have also seen in the past that this didn't work but it did after a reboot - worth a go.

---

### Post by capitan.harlock on 2006-11-04
> **khaledaboualfa said:**
> 
```
[17180773.092000] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[17180773.092000] ueagle_atm: Unknown symbol usbatm_usb_probe
```

and this repeats like 5 times or something.

I get nothing back when I type in 
```
sudo lsmod | grep eagle
```

thanks

```
$ sudo modprobe -f ueagle_atm
```

worked for me (also try to unplug and plug again your modem, after doing that)

---

### Post by capitan.harlock on 2006-11-04
By the way: how can I get module loaded at boot...? In Dapper I was able to make connection start whit Gnome, at least; but now I have to manually load ueagle_atm as above specified, of course must be done as superuser...

---

### Post by aces21 on 2006-11-08
After some digging it appears that the edgy kernel includes the ueagle-atm module, so there is no need to build it yourself. However, it also contains the eagle-usb module which conflicts with ueagle. There is a way to prevent modules being loaded and once I've got it sorted, I'll update my howto with new instructions for edgy. But for now, you can simply follow the howto, ignoring the bit about building ueagle-atm from source.

---

