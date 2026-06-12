---
title: "Edgy: Laptop loses wireless comms"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Roland of Gilead on 2007-04-08
I say it loses wireless **comm **because it appears that the network device is still associated and transceiving link-level traffic, but no IP communications function.

**Environment:**
Ubuntu Edgy, latest updates as of yesterday (via wired Ethernet)
IBM Thinkpad T40 w/Centrino wireless-B (ipw2100)

Linksys WRT54GP2 (Vonage router)
NO wlan encryption, wireless MAC filtering only
Static IP assigned to host, works fine under WinXP Pro


**Symptoms:**
*Centrino wireless device detected at eth1, configured against router using static IP
*Network functions normally for 30 seconds to 4+ mins, then appears to go dark.
*Outbound pings from laptop go nowhere (destination net unreachable)
*Same with traceroutes
*Output of "route -n" shows normal results
*Gnome network status panel for eth1 shows device associated and link packet counts incrementing regularly.
*Attempts to launch network configuration tool crash, resuling in bug tool capture [as noted in this thread.]("http://ubuntuforums.org/showthread.php?t=403939")
*Attempts to ping laptop from other machines on the network result in timeouts
*Other WLAN hosts on the network respond to pings normally

**Here's the really weird one:**
If I bounce eth1 down and up, it fixes nothing...but if I bounce the *router*, then IP communication to the laptop is restored!  Well, at least for another 30 seconds to 4 minutes...then the cycle repeats itself.

Anyone have any ideas where to start looking?

---

### Post by Roland of Gilead on 2007-04-09
Anyone?  Any ideas at all?  Hell, I'll take shots in the dark at this point...

---

### Post by rolando on 2007-04-09
have you tried using DHCP from your router? Does that make any difference?

Have you got a spare router to try?

:)

I have a similar kind of problem with my VPN at the moment, works fine for 30 seconds then just drops the ppp interface, very odd.  Only since I moved ISPs.

---

### Post by ew16301 on 2007-04-09
What about some kind of quarantine? Maybe when the router goes down, it clears the list of blocked hosts, but down/up would do nothing. The 30s-4min wait could be due to a script scanning the network and finding your computer at different times. Theres a shot in the dark :-/

---

### Post by Roland of Gilead on 2007-04-09
I probably should have been clearer about the WinXP configuration...

Anyhow, it's a dual-boot machine.  Under Winders, it uses an identical wireless networking configuration...that is to say, it's assigned the same static IP address and ancillary parameters.  This WLAN configuration has been working for well over two years.

The point of this is that the hardware is not the problem...it's something in the operating system, but damned if I know what.  I'm not familiar with driver-level tracing, so I'd appreciate any advice:  log files to look at, methods of turning on extended logging, processes to manually load drivers, whatever.

---

### Post by gargo2000 on 2007-04-11
I have the same problem with my router Linksys WRT54G.  I loose the connection to the router that hasn't moved for 2 years and in since I have been using Ubuntu, I have noticed this issue which I never got while running Windows XP.  I'd appreciate input on this matter as well.

Gargo

---

### Post by Phantommxr on 2007-04-11
hi all
new to ubuntu but loving the forum, nice (in a manner of speaking) to know that others are have SOME of the same problems I am having. the wifi is 1 prob, but I also have another...when I install beta...I can't login...I set up my user and pswrd but cant login!!!
anyone else?

---

