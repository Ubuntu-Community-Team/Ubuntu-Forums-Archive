---
title: "Serious Problems"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Jyscal on 2011-03-22
Hello all. 

Over the past 2 weeks i have made the a switch from windows to Ubuntu Karmic, and although i love the system, i find myself having never ending problems. I have re-installed three times in the past 2 days trying to figure out what could be the problem. 

On the first install, everything ran fine until i updated with Synaptic. The download and install of the update packages went fine buy after reboot, my system would not boot. Fair enough, i thought i must have done something wrong (allthough im not sure what). 

Second install, after updating things started going seriously wonky, like apps shutting down for no reason i could see, cpu running at 68 degrees celsius according to my bios when i start up. 

Third install seemed fine after i left for work this morning, but i when i got home and started the pc i found my resolution had changed to one that is not supported by my monitor. Top panel was at the bottom and bottom one was at the top with the buttons in the wrong order.  Only after three reboots does everything appear to be normal but i wonder for how long?

My system is not the greatest, only a 

    P4 3.06Ghz 
    4Gb DDR2 Ram
    512mb GeForce 8400 GS

I would really like to have Ubuntu as my os, but cant have it if things are going to carry on like this.
I dont mean to sound like im complaining but i feel thats all i have left to do. Please can anybody suggest something so i dont have to return to Windows.

Much appreciated.

---

### Post by Paqman on 2011-03-22
Could be hardware, especially with apps randomly shutting, failing to boot and weird CPU temps.

Start by ruling out the easy stuff like RAM and graphics cards. You can run memtest86 from the Grub menu when you boot to check your RAM, then try booting up without the GPU. Check that all your cables are securely pushed home, especially power cables.

---

### Post by BugBuster on 2011-03-22
Is there any specific reason for using Ubuntu Karmic?
It is a very old version and the support will end soon...
If possible try 10.04.2 LTS or 10.10 and see if you have better luck.

---

### Post by philinux on 2011-03-22
Jyscal,

Is this a wubi install or a proper dual boot?

---

### Post by Arijit_Kundu on 2011-03-22
+1 for 10.04.2
And at first dont go for update. If you still have problems, try to figure out the reasons. Also, if you are not used-to, try to install softwares from software center.

---

### Post by Jyscal on 2011-03-22
Ok i checked all the cables and everything is secure, all though a friend suggested it might be a hardware problem as well. The components are 2 years old but i dont think that would cause these problems but correct me if im wrong.

> **BugBuster said:**
> Is there any specific reason for using Ubuntu Karmic?
It is a very old version and the support will end soon...
If possible try 10.04.2 LTS or 10.10 and see if you have better luck.

Karmic is the only one i have at the moment apart from 8.10! Lol. I have been planning to upgrade to a later version, but also wanted to see how 9.10 ran for about 3 months before making any further commitments.

> **philinux said:**
> Jyscal,

Is this a wubi install or a proper dual boot?

To be honest its a complete 'Erase and use entire drive' install so i no longer have windows installed which is why im so worried, because as it stands i basically dont have a functioning os. 

After turning on the pc now again i ve found another 2 problems. 

1 is  that my fonts seem totally messed up.
While reading an email, pdf or html doc i find that the words blur half way though. 

For eg in Hysterical, the 'Hyst' part is blurred while, the end is fine. In another word it starts fine and ends blurry.

2 Something is updating on my system although i have check for updates turned off for now, and only Wine installed. Just while typing this post, the system monitor says that 11.6mb have been used, but i have only clicked 3 pages coming into the forum. Is there a command i can run in the terminal to see what is using the network? I am using Sakis3g at the moment as i cant seem to get Betavines BCM to install.

Mabye Ubuntu just would not like to be installed on my machine! That is my luck lol!

Thanks very much for all the support.

---

### Post by philinux on 2011-03-22
Jyscal,

Boot the livecd and see if that works ok.

---

### Post by crispy_420 on 2011-03-22
I think maybe the issue is the old version you are running. Is it possible that 9.10 may not have the proper drivers built it for your hardware? I can vouch for hardware support getting better with versions. I have a laptop (Acer) that everytime I install/update something just works or gets better.

Why suffer through three months of "issues" that a simple download may fix and be done with the problem?

---

### Post by matt_symes on 2011-03-22
Hi

Check your hard drive's SMART data. A failing hard drive can cause random crashes.

You can use disk utility for that. Make sure there is no dust in any of the fans.

Kind regards

---

### Post by Jyscal on 2011-03-22
The live cd works like a dream, thats why i tried the full install thinkin it would be even better. I think the thing to do at this stage would be to get a later version and take it from there.  I got a few font packages so thats ok now. Almost there!

---

### Post by Immolatus on 2011-03-22
The "upgrade" button has not worked properly for me since 7.10, so I don't use it anymore. The best method is just to install the most recent stable version and put your /home on a separate partition. That way when you upgrade next you don't lose all your data, or have to back it up (although you really should).

---

### Post by Jyscal on 2011-03-22
Well its definately hardware. My video card just died. The tears are borderline but i suppose it gives me reason to buy a new one. Thanks for all the help though at least the problem is solved

---

