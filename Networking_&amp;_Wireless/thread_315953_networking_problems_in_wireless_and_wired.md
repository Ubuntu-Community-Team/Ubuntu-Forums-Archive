---
title: "networking problems in wireless and wired"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by susantha on 2006-12-10
I'm a new person to Linux world even though I had the the curiosity for it for years. I've been trying to stay with the open source but lack of time and knowledge and time always pushed me to windows world. But I've taken a strong decision to keep Ubuntu as my main os in my notebook. I'm running Ubuntu 6.10 aka Edgy. I need some help to resolve the following problems, First a brief description of my machine, it's a Dell Inspiron 6000 with 512 MB Ram 40 GB HDD and Intel 10/100 lan (BCM 4401-B0)and Intel wireless b/g(2200 BG) compatible card. Integrated shared memory Intel VGA card. 

1. I did my Ubuntu installation with a DVD came with Linux Magazine. All seems fine. I've connected my PC to broadband via the 10/100 Ethernet cable and also connected a usb mouse. I found if I removed the network cable and the mouse machine is getting long time to boot. Can anyone expalin why is that? Once I taken this laptop to my office and it's a like a 486 machine crawling to bootup. Really annoying!

2. Configring wireless lan should be painless but in my machine it is a real pain. While I'm working in the battery power I selected the wireless connection and select the option DHCP to obtain the IP address. Machine display it connected on the taskbar but I cannot access internet. Tried to ping for the router address and 100% packet loss. Can anyone tell me a way to release the IP and obtain IP address through command prompt? I know it is very easy to do it in windows XP environment by typing ipconfig /renew, ipconfig /release & renew commands. I only found ifconfig command and couldn't find much luck with it. Am I over reacting about this matter?

I'm not going to say windows is better or giving example it is when I find linux is so exciting to experiment. After all I beleive I should stick to Ubuntu, can't get away with it once you see the power of it. I really love this product but need support badly. 

Susantha(

---

### Post by compwiz18 on 2006-12-10
**sudo dhclient** will get you a new IP.

as for the slow boot...I can't help you, sorry.

---

### Post by susantha on 2006-12-10
Hi thank you for your reply. Will keep in mind that command. BTW yesterday around 4a.m. I manged to get the wireless connection. Dunno how I get it but kept on fiddling in the settings. Finally when I restart the notebook I got an error message saying cannot load Hal properly, but it load properly. But today it gave up on me and got stuck in a certain stage when loading the GUI screen. Couldn't do anything and end up reinstalling OS again.  

 
Can anyone tell me how can I see what's going on behind the screen while machine loading. All I can see is the UBUNTU logo but I really like to see the apps loading in the background to get an idea about errors. ;)

---

### Post by koenn on 2006-12-10
> **susantha said:**
>  
Can anyone tell me how can I see what's going on behind the screen while machine loading. All I can see is the UBUNTU logo but I really like to see the apps loading in the background to get an idea about errors. ;)

edit the boot menu, by typing this in a terminal:
```
sudo gedit /boot/grub/menu.lst
```

Find the menu entry that boots your ubuntu, something like:
```
title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,2)
kernel		/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro quiet splash
initrd		/initrd.img-2.6.15-27-686
savedefault
boot
```

remove the "splash" (maybe also "quiet"), and save.
Don't change anything else unless you know what you're doing !

As for the slow boot in your original post : it may well be that with the network cable unplugged, the system keeps trying in vain to get an IP address from a dhcp server - it can take minutes before it gives up and continues to start up.

---

