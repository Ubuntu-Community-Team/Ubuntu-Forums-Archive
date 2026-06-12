---
title: "How to change resolution on ubuntu server 10.10?"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by alfamuzjak on 2010-12-28
Does anyone know how to change resolution on ubuntu server?
I need 1280x960

---

### Post by cariboo on 2010-12-28
Are you running a gui on the server? What graphics adapter does the system have?

---

### Post by alfamuzjak on 2010-12-28
> **cariboo907 said:**
> Are you running a gui on the server? What graphics adapter does the system have?

NO GUI...my graphic card is ATI EAH2400

---

### Post by alfamuzjak on 2010-12-29
Plz help me guys...Any idea?!
Thanks

---

### Post by alfamuzjak on 2010-12-29
> **alfamuzjak said:**
> Does anyone know how to change resolution on ubuntu server?
I need 1280x960

Finnaly success!!!

If someone is interested how...u can ask in anytime

---

### Post by vipanbalrai on 2010-12-29
> **alfamuzjak said:**
> Finnaly success!!!

If someone is interested how...u can ask in anytime

Hi, Can you please tell me how you have changed the resolution. I have also similar problem. I am using intel x3100. and i want to set resolution to 1280x1024. I am using ubuntu 10.10

---

### Post by alfamuzjak on 2010-12-29
1.	Comment blacklisted framebuffer drivers and save.
**sudo vi /etc/modprobe.d/blacklist-framebuffer**
add a "**#**" before
_vesafb_
and
_vga16fb_

2.	Add modules in initramfs.
**sudo vi /etc/initramfs-tools/modules**
append following 3 lines then save.
_vesafb_
_vga16fb_
_fbcon_

3.	Update initramfs.
**sudo update-initramfs -u**

4.	Check your graphic card's framebuffer mode.

If you don't have hwinfo installed, install it first.
**sudo apt-get install hwinfo**

**sudo hwinfo --framebuffer**


5.	Then it will show something like this:
Mode 0x033c: 1920x1440 (+1920), 8 bits
Mode 0x034d: 1920x1440 (+3840), 16 bits
Mode 0x033a: 1600x1200 (+1600), 8 bits
Mode 0x034b: 1600x1200 (+3200), 16 bits
Mode 0x035a: 1600x1200 (+6400), 24 bits
Mode 0x0307: 1280x1024 (+1280), 8 bits
Mode 0x031a: 1280x1024 (+2560), 16 bits
Mode 0x031b: 1280x1024 (+5120), 24 bits
Mode 0x0305: 1024x768 (+1024), 8 bits
Mode 0x0317: 1024x768 (+2048), 16 bits
Mode 0x0318: 1024x768 (+4096), 24 bits
Mode 0x0312: 640x480 (+2560), 24 bits
Mode 0x0314: 800x600 (+1600), 16 bits
Mode 0x0315: 800x600 (+3200), 24 bits
Mode 0x0301: 640x480 (+640), 8 bits
Mode 0x0303: 800x600 (+832), 8 bits
Mode 0x0311: 640x480 (+1280), 16 bits
Write down the mode code you want to use, u say u need 1280x1024, so the code is "0x031a"

...Now, this part i found is probably for some other(older) version of ubuntu server so if u have those files ...u follow this step. I didnt have that files so next step for u will be **6a**

**6**.	Edit menu.lst
sudo vi /boot/grub/menu.lst
find the following 2 lines and add your mode code at the end of each line.

# defoptions=quiet splash locale=zh_TW vga=0x031a

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=452c3352-f739-4df0-8930-8c80a9f212d4 ro quiet splash locale=zh_TW vga=0x031a

**7**.	Reboot.


**6a**.Edit grub file
**sudo vi /etc/default/grub**  -->find following sentance:
&#61672; GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet text vga=0x031a&#8221; and next to **quiet** add **text vga="ur code"**

**7a**. Then u must update grub
**sudo update-grub**

**8a**. Reebot
**sudo shutdown -r now**

...And thats it.
BTW i changed mine to 1024x768 (0x0317)-(1280x960 wasnt full screen, some bug i think or who knows what) but in any case its better than previous little window...

let me know if you succeeded.bye

---

