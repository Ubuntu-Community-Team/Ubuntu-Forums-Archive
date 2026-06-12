---
title: "Turn off one of two wifi cards"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by GrzegorzJZD on 2009-08-23
Hi,

I have a Lenovo IdeaPad Y530 notepad, witch has a hardware switch on front panel. It works perfectly, when I'm using built-in wifi card (wlan0). 

Sometimes I'm using external usb wifi (wlan1). My problem is, every time I turn off wifi using hardware switcher, it turns off also external usb wifi card.

The same is when I type
sudo iwconfig wlan0 txpower off

It also turns off built-in wifi card (wlan0) and external usb wifi (wlan1). 

Is it possible to turn off only embedded into laptop wifi card and not turn off external wifi card?

---

### Post by nothingspecial on 2009-08-23
I would blacklist the internal's module and load the externals.

If you don`t know what I`m talking about post back.

---

### Post by SuaSwe on 2009-08-23
Does the same thing happen with 'ifconfig wlan0 down'?

---

### Post by GrzegorzJZD on 2009-08-23
SuaSwe: 'ifconfig wlan0 down' just disconnects me from network. Not turn off card.

nothingspecial: Could You write something more how can I blacklist internal's module?

---

### Post by nothingspecial on 2009-08-24
To remove a module

```
sudo modprobe -r *module*
```

That should remove it from the kernel

To make this permanent, ie only use the external, add the module to /etc/modprobe.d/blacklist.conf, so

First make a backup ```
sudo cp /etc/modprobe.d/blacklist.conf ~/blacklist_backup
```

```
sudo cp /etc/modules ~/modules.backup
```
```

sudo nano /etc/modprobe.d/blacklist.conf
```

Add ```
blacklist *module*
```

to the end of that file. This will stop the internal loading at boot.

As the external is working you shouldn`t need to add it to the /etc/modules file but it shouldn`t harm.

```
sudo nano /etc/modules
```

add the external module to the end of that file.

If anything goes wrong either change those 2 files back or restore them from your backups.

Obviously you have to specify the correct modules. Find out which modules both cards use and use apropriatly ie the internal in /etc/modprobe.d/blacklist.conf and the external in /etc/modules.



Save close reboot.

---

### Post by GrzegorzJZD on 2009-08-25
Okej, I definitly try this.

But I'd like to know if there is any way to change behavior of hardware switcher, so it turns off only internal devices (bluetooth and wifi) and not turning off external usb wifi?

---

### Post by MoebusNet on 2009-08-27
You could always look in your BIOS to see if you can turn off the internal card without affecting the external card. On my Dell D800 I select <F2> before the Ubuntu screen shows up when I turn the computer on to enter the BIOS configuration page. Other computers use <Esc>. There may be a message when you first turn on your computer that tells you which key to press to enter "Setup" or "BIOS" or some such.

---

