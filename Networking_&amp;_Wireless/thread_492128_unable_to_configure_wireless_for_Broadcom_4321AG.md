---
title: "unable to configure wireless for Broadcom 4321AG"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by jimbo11 on 2007-07-04
Hello, 

I'm trying to get wireless working on my laptop. My wireless card is a Broadcom 4321AG 802.11 a/b/g/draft-n . 
I've followed several suggestion to downloading and extracting the firmware with bcm43xx-fwcutter for both the wl_apsta.o and bcmwl5.sys file, but unlike those "other people", simply doing this, then rebooting and then connecting to your wireless network doesn't work at all. There is no wireless icon at the top right hand portion of the menu bar, it still comes up with my wired network connection. And yes, I had the network cable out when I rebooted and wireless card was on. 
When I do an lspci | grep Broadcom\ Corporation I get:
03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)

Just for some other details, I have Feisty fawn 7.04 installed on a HP pavilion dv9000. Any help on this would be greatly appreciated. ;)

---

### Post by greenwom on 2007-07-06
I;m having a similar problem with my dv9000 (I'm in vista now)
I tried the fw-cutter deal an it was  a no go.  /when I run lspci 
I get a Dell chipset for my wireless (1390 I believe) I really would like to avoid ndiswrapper
it has worked well in the past it just nice not having to deal with it.

So I 2nd your request for help

---

### Post by kevdog on 2007-07-06
Do you guys have 32 or 64 bit installs?  Although Ive used fwcutter approach in the past, ndiswrapper (despite what you hear) is actually fairly easy to install however it doesnt work for everyone. (Works great for Dell 1390!)

You will most likely need winxp drivers.

Can you please post
lshw -C network
lspci -nn

Thanks.

---

### Post by Perfex on 2007-07-07
I extracted the drivers (attached)

Try using Ndiswrapper

```
lsmod | grep 43xx
sudo gedit /etc/modprobe.d/blacklist
```

Add blacklist bcm43xx between the "" at the end of the file, save and close
Now you unload the module with:
```
sudo modprobe -r bcm43xx
```

Download and install ndiswrapper here [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

after

```
sudo ndiswrapper -e bcm
sudo ndiswrapper -i /home/$user/bcm/bcmwl6.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

then add ndiswrapper to the end of the list

```
sudo gedit /etc/modules
```

restart

I dont have your card, so im not sure if its going to work, but tis worth a shot
basicly this is the way I did my card a 4318 though it was bcmwl5.inf for me this is where I found drivers for your card [http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&dlc=en&lc=en&softwareitem=ob-46095-1&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&dlc=en&lc=en&softwareitem=ob-46095-1&jumpid=reg_R1002_USEN)
closest to it was bcmwl6

---

### Post by digitalgecko on 2007-07-08
I also had trouble my wireless then I found a link to this debian file. Clicked it and my wireless started working. Mine was Broadcom 4318. Don't know if it will work for you but look for and give it a try. Only thing is you have to to press the button and close out the wireless before restarting or turning off the computer. Minor annoyance for working wireless. Good luck! 

bcm43xx_compwiz18.1-all.deb

---

### Post by greenwom on 2007-07-08
I had trouble with the bcm drivers.  Even though lscpi shows a broadcom card that is supposed to use the bcm driver, I had to use a driver from dell.  (I even pulled the inf file right from the windows partition and that didn't work.)  

I used ndiswrapper and a dell driver. (1390) 

it worked but this was a weird one....  

:guitar:

---

### Post by kingbree on 2007-09-14
Yep mine is screwed as well, I have a 4321AG card but, after I ran the automated script in the sticky post Ubuntu thinks its a Dell 1390.
I know I could get it working if I could just get rid of that Dell driver, at least I would be happier that nothings obviously wrong.
Is this possible to clear all that 1390 stuff off my machine?

---

### Post by RedLXXXIV on 2008-03-13
Hey guys, I have the Broadcom 4321AG w/l card in my HP tablet. You DO need to use ndiswrapper with the drivers for it. It's straight forward, and simple to do.

Download the driver package [here]("http://www.hackapedia.org/downloads/wireless_sp36684a.zip").

Install ndiswrapper from the (k)ubuntu install disc/livecd using synaptic/adept.

Then:

```
su
[enter password]
cd [insert path to directory where you unpacked the drivers]
ndiswrapper -i bcmwl5.inf
ndiswrapper -m
ndiswrapper -mi
ndiswrapper -ma
reboot now
```

After all that is done, your comp will reboot, and you should have your wireless show up in your statusbar. After you connect to your w/l network, don't forget to set up your repositories in your package manager.

Only problem with using ndiswrapper that I've come across so far, is that when using airmon, you can't set the card to monitor mode.

:) RedLXXXIV

---

### Post by bebops_lost on 2008-06-23
hey, 
I have the exact same wireless card and I think it's the exact same laptop
Broadcom 4321AG w/l card in my HP tablet tx1314.

I fixed my wireless issues by following this guide here:

[http://ubuntuforums.org/showthread.php?p=5233659](http://ubuntuforums.org/showthread.php?p=5233659)

it worked for me, I recommend trying it (though you have to give it an extra reboot at the end) 

(by the way, do you have any idea how to fix the suspend/hibernate issues on that laptop, or get the tablet feature going? if so send me msg and I'll start a thread. -thanks)

---

