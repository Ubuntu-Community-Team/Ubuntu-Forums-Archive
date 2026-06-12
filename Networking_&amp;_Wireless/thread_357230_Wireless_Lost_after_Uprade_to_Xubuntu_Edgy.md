---
title: "Wireless Lost after Uprade to Xubuntu Edgy"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by haz2a on 2007-02-09
I'm trying to get wireless working in Xubuntu on an old AMD K6-2/500 desktop with a Buffalo WLI2-PCI-G54S adapter. My big mistake was probably not buying a card with native linux support as listed on the [http://linux-wless.passys.nl](http://linux-wless.passys.nl) site. It can be hard to identify a supported card that you can actually buy, and even then there is no guarantee that the card you get will have the same chipset as the one they tested - but I wish I had tried it first.

Anyway I started out last week by installing Xubuntu 6.06 LTS, ndiswrapper-utils, and the bcmwl5 drivers recommended for the Buffalo  adapter, following varios How-Tos. The card worked OK without encryption, but I couldn't get it to work with WEP. I started with the US driver, but when I changed to the one suitable for the UK (R81435 v3.40.73.0) it made no difference. With WEP enabled on the router, iwconfig always reported 'Access Point: Not-Associated', and ifconfig showed that wlan0 failed to obtain an inet IP from the DHCP server. I did not have a wired adapter installed at this time. 'iwlist wlan0 scan' can always see the router, whether WEP is enabled or not. 

I tried ASCII key and Hex key, Open System and Shared Key. I have Frame Bursting and Turbo modes disabled on the router. 'Wireless User Isolation' whatever that is, is set to Off. I tried '802.11b only', '802.11g only', and 'Auto' modes.

Queries about the bcmwl5 Drivers
The driver exe from Dell contains two driver folders: 'AR' and 'IR' with identically named files. I read somewhere that someone else used the 'AR' versions, so I did too, but does anyone know what the difference is?
Each folder has 2 inf files and one sys file. There is bcmwl5a.inf which is 38KB and readable with gedit, and bcmwl5.inf which is 1.2MB and not readable with gedit. They both seem to install via 'ndiswrapper -i'. Anyone know what the difference is and which one should be installed? Dell's README (in the parent of these 2 folders) talks about "the update" - is bcmwl5a.inf an update to bcmwl5.inf? - and if so, do they have to be installed in order?
The only difference I noticed after installing  the bcmwl5a version (see below) was that iwconfig started showing a new line: "Encryption Key: 3967-..." with a 22 digit set of numbers, which I didn't recognise - they arent the WEP ASCII or Hex codes set in the router.
When installing both the drivers via 'ndiswrapper -i bcmwl5[a].inf' there was a warning message "Forcing parameter IBSSGMode|0 to IBSSGMode|2" repeated 10 times. I read in the Ubuntu Wireless Troubleshooting guide that some cards "need a command to adjust the mode to work properly" and using their example I tried putting 'pre-up iwpriv wlan0 authmode 2' into /etc/network/interfaces, but that didn't help so I commented it out.

Ndiswrapper Queries
I installed the bcmwl5.inf first. WEP would not work, so I did 'ndiswrapper -e bcmwl5' then 'ndiswrapper -i bcmwl5a.inf' to try the other one. But now I seem to have both installed. 'ndiswrapper -l' lists both drivers, saying both are present with hardware present. Is it OK, or even required, to have both?
How does ndiswrapper know which to use?
If one should be deleted, how do I do that - 'ndiswrapper -e bcmwl5' didn't seem to work?

I put a wired adapter back in (leaving the wifi card in too) and the wired interface worked fine.

I installed network-manager-gnome to see if that would help, but it only seemed to recognise the "wired connection" - no mention of wireless at all.

After trying everything I could think of to get WEP working, I upgraded to Xubuntu Edgy - but now I can't get wireless working at all, even without encryption.

At first there was no Network Manager on the XFCE panel, but after rebooting I had TWO NtwkMgr icons?
Both NtwkMgr icons behave identially - they both give info about the wired i/f eth0, and neither of them mention wireless at all!?
/proc/net/ndiswrapper/lan0/settings has:-
	mac_address=XX:XX:XX:XX:XX:XX (all 'X's no numbers)
	driver_version=Broadcom ... 3.4.73.0  (so that seems about right)
	- - -
	Country=US  (its in the non-US bcmwl5a.inf for some reason?)
	- - -
	NetworkAddress=   (blank)
	- - -
	RadioState=0      (?)

No wireless now, even with encryption disabled!
If you can't help, please send the men in white coats.

---

