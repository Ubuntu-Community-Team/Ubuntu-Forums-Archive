---
title: "HOW-TO: Installing RT2500 (Ralink) based native drivers"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by magicfab on 2005-04-15
Hello,

I have reviewed and proof read this [HowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo) and can confirm that it works, including the WPA support. 

It was originally discussed [here](http://ubuntuforums.org/showthread.php?p=133176).

The system I managed to get connected with is an Averatec 3250HX laptop.

Cheers,

F.

---

### Post by markthecarp on 2005-04-15
Thanks for testing magicifab. I've been able to confirm that my Encore ENPWI-G-RLAM works using the diswrapper module. 

I apologize for not replying to my post in the previous thread earlier. I'll try this tonight w/o all the qt dependencies. 

Are you aware of anyone developing the gui in gtk?

-mark

---

### Post by dgantony on 2005-04-17
Thank you, magicifab. I have a Averatec 3250 and was using Ndiswrapper. Couldn't listen to shoutcast because it was soooo slow. Followed your directions and now the speed has really improved.

There was one step that did not work for me : In the "Installing" section - 

> 3. Type:

sudo echo "alias ra0 rt2500" >/etc/modprobe.d/rt2500 

gave a permission denied. 

I just used 
```
sudo vi /etc/modprobe.d/rt2500
``` 
and typed in 
```
alias ra0 rt2500
```
to get through that step.

Thanks again.

---

### Post by Yaniv on 2005-04-24
I managed to get the Edimax wireless card to work with the native driver. By chance, I'm also the one who originally wrote the Howto ([http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)).

---

### Post by jpablo on 2005-04-26
i think i have a problem with raconfig, the first time i run it the program asked me about my zone, for the channels or something like that, but i think i entered the wrong zone, and i don't know how to change it back, is there any way to change the option of the zone???

sorry for my poor english

---

### Post by fluideye on 2005-05-10
Hi all, just installed Hoary 5.04 tonight and so far am very pleased.  I have been trying to get my rt2500 driver to work with Mandrake 10.1 which kept freezing.  Anyhows, I have an Averatec 3260 and followed the how to mention above and whenever I got to the last step of :

sudo nautilus

this was my return:

corey@crypto:~/rt2500-cvs-20050510/Utilitys$ sudo nautilus

--- Hash table keys for warning below:
--> file:///home/corey/rt2500-cvs-20050510/Utilitys
--> file:///root
--> file:///home/corey/rt2500-cvs-20050510
--> file:///home/corey
--> file:///
--> file:///home

(nautilus:14828): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 6 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///home/corey/rt2500-cvs-20050510/Utilitys
--> file:///root
--> file:///home/corey/rt2500-cvs-20050510
--> file:///home/corey
--> file:///
--> file:///home

(nautilus:14828): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 6 elements at quit time (keys above)
corey@crypto:~/rt2500-cvs-20050510/Utilitys$

I then went in as root to the driver's folder /Utilitys/RaConfig2500 double clicked and activated.  

Connection properties show that ra0 is connected and is sending recieving packets but I can't get google or any site to come up, browser is looking without timing out.  

Any help?

---

### Post by fluideye on 2005-05-11
And now on reboot, when configuring network devices I got  "unable to apply power" continuously and the boot process stopped or was in continuous loop.   So I booted in recovery mode and changed the network device from ra0 to eth0 and am able to ping lan.  

The problem now is the wireless card has dissapeared.  When I do iwconfig I get back eth0 & lo.  

I am a newbie as you can tell, and would appreciate your help.

---

### Post by fluideye on 2005-05-11
This may be helpful too.  when booting now, 

cs pcmcia_socket0: unable to apply power

Does anyone know what that means?

---

### Post by trtrl on 2005-05-12
Unfortunately, I'm not yet able to use my rt2500 card (a cheap pci card), as it is my only connection. Which means that I can download and transfer the rt2500 driver package (either via the dualboot windows installation or via usb key), but I cannot apt-get the necessary build tools. So, how can I get those with a - for all intents and purposes - standalone ubuntu system?

---

### Post by linux_fish on 2005-05-13
[QUOTE=magicfab]Hello,

I have reviewed and proof read this [HowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo) and can confirm that it works, including the WPA support. 

It was originally discussed [here](http://ubuntuforums.org/showthread.php?p=133176).

The system I managed to get connected with is an Averatec 3250HX laptop.

Cheers,

F.[/QUOTE]

I am trying this on the same setup and am having trouble at:
> sudo cp ~/rt2500-cvs-daily/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/

I get this:
> 
cp: cannot create regular file `/lib/modules/uname -r/kernel/drivers/net/wireless/rt2500.ko': No such file or directory

Please help!

---

### Post by linux_fish on 2005-05-14
Nevermind ... I used nautilus to acomplish the file copy since I couldn't figure where I was going wrong.

---

### Post by bdmp on 2005-05-15
I have a AV3225HS-20.  How do I know if it has the broadcom or the Ralink drivers? I read in a site that tells you if your card is compatible that some of the 3200 series have Broadcom chips.  When i do "lspci" to list my hardware this comes out "0000:00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)". So that means I have broadcom right?  Well I do the in stall twice. Once with the drivers for my model from the averatec site and once from  some other broadcom driver. Anyway, its not working still. Any advice would be appriciated.

---

### Post by moon2js on 2005-05-15
My wifi card (b), an SMC2635W (blue edition) uses the RT2400, and I'm wondering if there is any difference between the RT2400 and RT2500 other than a digit. I followed the howto in the past and just substituted 4's for 5's, and it seems to be working. But it's not perfect, but that just may be my inexperience with linux and wifi in general. Also, I could never get the utility working.

Is there any issue I should be aware of regarding using this howto for a RT2500 when my card needs a RT2400. If there isn't or if it's just some minor details, maybe the howto should be edited into a RT2X00 howto.

---

### Post by craft47 on 2005-05-24
Hi!  I've just tried the How-to step by step and ended up with this:

{standard input}: Assembler messages:
{standard input}:689: Error: symbol `set_mac' is already defined
make[2]: *** [/home/number6/rt2500-cvs-20050523/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/number6/rt2500-cvs-20050523/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
rt2500.ko failed to build!
make: *** [module] Error 1

I see that 'set_mac' is already defined.  I don't know if that has anything to do with the wired nic being connected?  Do I need to disable that first?  The mac addresses of the nic and the wireless card are not the same so I am confused.  Any Ideas?

---

### Post by slux on 2005-05-25
[QUOTE=craft47]
I see that 'set_mac' is already defined.  I don't know if that has anything to do with the wired nic being connected?  Do I need to disable that first?  The mac addresses of the nic and the wireless card are not the same so I am confused.  Any Ideas?[/QUOTE]

It's a compiler error and your other NIC can't be interfering in any way. If you downloaded a daily CVS, my first guess would be that you just happened to get it at the wrong moment when the CVS code actually didn't build. If it does that with the beta release it must be something else. 

BTW, does anyone know whether or not the driver works on PPC?

---

### Post by craft47 on 2005-05-25
[QUOTE=slux]It's a compiler error and your other NIC can't be interfering in any way. If you downloaded a daily CVS, my first guess would be that you just happened to get it at the wrong moment when the CVS code actually didn't build. If it does that with the beta release it must be something else. 
[/QUOTE]

You were right, it was the daily release.  I downloaded the beta release 1.1.0 and substituted that in the How-to and YES!!!!!! it is all working!!!  The utility as well!  Now I have a computer devoted almost entirely to linux (20G xp, 60G Ubuntu).  At this rate, I may eliminate xp all together!!
I'm a happy camper!! \\:D/

---

### Post by cdean on 2005-05-28
[QUOTE=fluideye]This may be helpful too.  when booting now, 

cs pcmcia_socket0: unable to apply power

Does anyone know what that means?[/QUOTE]

I'm also getting this.  It may have something to do with the card not being on at boot.  I'm gonna test this theory.

edit: there is a separate thread on this error: [http://www.ubuntuforums.org/showthread.php?t=27629](http://www.ubuntuforums.org/showthread.php?t=27629)

---

### Post by saeba on 2005-05-29
i have a problem to make my conceptronic pcmcia card work, I've done all the steps of the how-to - it seems with no problem- but when i tried to activate the card (sudo ifup ra0) i get this message: "ignoring unknown interface ra0=ra0", the module is loaded. I use kubuntu 5.04.

Any ideas??

P.D. sorry for my english

---

### Post by RavanH on 2007-09-26
> **magicfab said:**
> Hello,

I have reviewed and proof read this [HowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo) and can confirm that it works, including the WPA support. 

It was originally discussed [here](http://ubuntuforums.org/showthread.php?p=133176).

The system I managed to get connected with is an Averatec 3250HX laptop.

Cheers,

F.

Hmmm, such a very old thread - but such sweet promesses!!! RT2500 working even with WPA?

But where did that How-To go :confused:

Ah, well. I hope for Gutsy to solve this ;)

---

### Post by Belgar on 2007-09-26
i use RutilT under Feisty and after compiling, WPA works directly. The only problem i haven't solved yet is the fact that it will only run with 'root' instead of your personal account.

The "direct" method probably also still works, but i prefer the graphical interface as i need to switch quite often

[http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

---

