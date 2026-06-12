---
title: "wireless can not work (bcm4312 802.11b/g (rev 01); chipset: 14e4:4315 (rev 01)"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by johnshentiro1 on 2008-10-31
I have the problem WPA was not working (while connecting, only one green dot in network manager applet). 

so I find the instruction 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.1%20(Obsolete,%20and%20no%20longer%20recommended](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.1%20(Obsolete,%20and%20no%20longer%20recommended))

and **simonas** has the same problem with me, so i follow his instruction ,when i finish the step of bug fix,type "lshw -C network" the module is still  "wl",so I do Compile ndiswrapper from Source.When i restart,even worse!!so many warnings ! I have no idea about it. could anybody help me to fire it? Ooops!!!

Nearly forget my laptop is dell Vostro 1400 .

---

### Post by johnshentiro1 on 2008-11-02
it can work now.But i find the system is slow after the ndis module is installed.

---

### Post by meowsus on 2009-01-16
Did you ever get this fixed? I have not yet tried the steps in the documentation you've provided, but i used the driver files i found at Dell.com and Wi-Fi worked immediately. I installed the .inf file using **ndisgtk** (after disabling my WPA/WPA2 password in the router) and it worked like a dream... Showed up in the Network Manager and everything.

Until i rebooted...

Now **ndiswrapper** shows the driver installed, and properly, but Network Manager does not recognize the card or turn on the wi-fi radio.

The whole thing is confusing me greatly. Did you ever solve this problem?

I'm running Intrepid, with the same exact card as you.

Curdo
[http://meows.us/history.html](http://meows.us/history.html) - for a complete listing of the horrors of my most recent install.

---

