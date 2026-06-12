---
title: "No wireless routers seen by lap top"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by gordon33 on 2010-08-15
Hello All

What do I need to click ON to make my lap top see the wireless routers again? 

I am using Ubuntu 10.04.* Things were working fine for the last few months.

However, very early this morning I started up my HP G60t lap top.* When I went to connect to the* Net gear wireless router (Internet) a box came up that listed my wireless router name and wep code.* The 2 options I remember were Cancel, and Delete.* I should have picked cancel.* It
was early and I clicked Delete hastily.* Now my lap top does not see any wireless routers. 

Now when I clicking on the wireless Icon I see "Wireless Disconnected".* Their use to be several other neighbor's routers listed now their are none.

Where should I begin. This system has ran for about 1.5 years now.

Any help would be appreciated.

Gordon33

---

### Post by anewguy on 2010-08-16
Not that it will be the problem, but I would start with something simple like right-clicking on the network manager icon and being sure the "Enable Wireless" option is checked.

---

### Post by diablo75 on 2010-08-16
Some laptops have these special features for controlling the wireless adapter via the BIOS.  If you go into your BIOS you may find your wireless adapter is set to be off by default when the system is booted but allow an OS to turn the adapter on.  Unfortunately not all wireless adapters do this when you attempt to turn them on and off with Ubuntu, so if your laptop does have a feature like this it's best to tell it to keep the adapter on at all times so things will just work.

---

### Post by gordon33 on 2010-08-16
Hello Anewguy

I right-clicking on the network manager icon and the "Enable Wireless" option was checked.  I clicked it off tried to turn it back on but it would not go back on.  The charters of "Enable Wireless" were in a gray video.  I rebooted the computer and the "Enable Wireless" was in normal video and checked.


Hello diablo75

 How do I get to the BIOS on my HP G60t lap top.  When the thing is booting up all I see is hit Esc for set up.  When I ESC I get a list of 10-20 different Linux  (I think they are) Kernels to pick from.

gordon33

---

### Post by diablo75 on 2010-08-16
If you're seeing Linux Kernels, then you're just looking at your Grub bootloader menu, which comes AFTER the opportunity to enter your BIOS, so if the screen that you say is telling you "Press ESC for setup" and it also has an HP logo nearby, then you just need to hit ESC sooner, as in, repeatedly right after you turn the computer on.

Other keys that are sometimes used to access the BIOS (on HP systems) include F1 or F2.  If ESC doesn't work, try those instead.

---

### Post by gordon33 on 2010-08-16
Hello  diablo75

Thank you. I have wanted to know how to get to the BIOS for a long time. 

I did not find any thing in the BIOS for the Wierless connection. 

What I found was a list when hitting Esc when the HP first showed up on the screen.    The list included:
F1 System Information
F2 System  Diagnostics
F9 Boot Device Options
F10 BIOS setup
F11 System  Recovery

Clicking on F10 I get a screen that is labeled “InsydeH2O Setup Utility”.  It has listed across the top Main, Security, Diagnostics, System Configuration, Exit.  I opened up each of the sections and did not see any thing that listed my computers wireless card.

gordon33

---

### Post by gordon33 on 2010-08-17
Hello All

Does the result from iwconfig give any? What does "no wireless" indicate? extensions.





gordon@gordon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
gordon@gordon-laptop:~$

---

### Post by alphacrucis2 on 2010-08-17
> **gordon33 said:**
> Hello All

Does the result from iwconfig give any? What does "no wireless" indicate? extensions.





gordon@gordon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
gordon@gordon-laptop:~$

Some laptops have an external switch that powers off the wireless transceiver. I guess it is possible that you have powered it off by mistake. Just something to check anyway.

---

### Post by gordon33 on 2010-08-18
Hello alphacrucis2

The HP G60t does not have a external switch for the wireless transceive.  I did not find any thing in the BiOS to turn on or off the Wireless card.

Still I think the fix is some thing as simple as turning on or picking the correct switch.  

So far I have not stumbled on to the needed answer.

Gordon

---

