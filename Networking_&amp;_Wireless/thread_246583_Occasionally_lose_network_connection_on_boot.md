---
title: "Occasionally lose network connection on boot"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by Corfy on 2006-08-29
I am having an intermittent problem that just all of the sudden started.

Occasionally, when I boot up my Linux laptop, it will hang at "Network Connections" for about 30 seconds before moving on (although it indicates "OK" after moving on). Once the computer is booted, however, I have no wireless connection. It claims my wireless network card is enabled, but I am not receiving a signal (despite the fact that I am usually literally within arm-stretch of our wireless access point).

The only thing I know to do is restart the computer. Usually that works, and I have full connectivity again. Occasionally, however, I have to restart a second or even a third time.

I'm still a bit new to Linux, and so I don't know where to begin to track down this problem. Conversely, if there is a way I can fix this without having to restart my computer, that would be helpful as well. If all I have to do is run a command or a couple of commands to get network connection back, then I can work with that. I am just tired of rebooting (or re-rebooting, or re-re-rebooting) to get a network connection.

I'm running a Dell Latitude D600 with a Dell TrueMobile 1400 wireless card (which took me forever to get working in the first place). I don't know if it matters, but I am also using Kubuntu rather than Ubuntu (although when I first got the network card working, I was using Ubuntu). And I am running Dapper. This computer also dual-boots into Windows XP Pro, although I have not had any problems with the wireless connection in Windows (which leads me to think it probably isn't a hardware issue, but I could be wrong about that).

I noticed the problem first started about a week after I installed the Firestarter firewall. I have since uninstalled Firestarter, but the problem persists.

If there is any more information I can give you, let me know and I will track it down (although I am still somewhat of a newb with Linux, so you might need to tell me how to track it down).

Thanks ahead of time for your help.

Corfy

---

### Post by haiku99 on 2006-08-29
are you using ndiswrapper??

---

### Post by Corfy on 2006-08-30
Yes I am. In fact, here are the instructions I followed to finally get my wireless to work (in case you are wondering):

>  Originally Posted by TheAngryPenguin
It didn't work for me. I have a Dell Latitude D400 with a "0000:01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)" wireless card. I tried with the files from the first post as well as with a .sys that's known to work well with ndiswrapper. In all cases, I've ended up with a kernel panic right as the wireless card became active. To anyone else with this particular flavor of Broadcom, here's what I've done to get it to work (and I won't go that much into detail since most of this is documented very well elsewhere...):

1) Install ndiswrapper-utils

2) Download the TrueMobile 1400 (BCM4309 - 802.11a+b+g) driver package from Linuxant's site.

3) Rename R63259.EXE to R63259.EXE.ZIP and open with Archive Manager -- extract bcmwl5.inf and bcmwl5.sys from /TMSetup

4) Do the ndiswrapper voodoo with the file(s) above.

5) Blacklist bcm43xx

6) Add ndiswrapper to /etc/modules

7) Reboot

Sorry I didn't respond earlier... I thought I had subscribed to this thread but I hadn't, so I didn't get an email notification that you had replied. I have fixed that now.

---

### Post by haiku99 on 2006-08-30
I had a similar problem (ndiswrapper stopped loading at boot) and found that I had to manually add the module, even though I had entered "sudo ndiswrapper -m" on installation and I got a message that it was already entered when I repeated the command after i started having problems....however when I opened the file to edit by typing "gksudo gedit /etc/modules"  it was NOT there, had to add "ndiswrapper" at the end....many howto's imply that the two methods of adding a module accompish the same thing, but after this experience I'm going to enter them manually.
  Anyway, hope that helps and FWIW my machine seems to boot faster now too, 
gets through the network step quicker...

---

### Post by Corfy on 2006-09-01
Thanks for the tip. I added ndiswrapper to the modules file and I haven't had the problem since. I really appreciate the help.

---

