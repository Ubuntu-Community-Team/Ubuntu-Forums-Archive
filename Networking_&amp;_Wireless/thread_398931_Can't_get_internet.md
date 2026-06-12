---
title: "Can't get internet"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by finisdiem on 2007-04-01
I just put xubuntu on my laptop (compaq presario 1247) using the oem install because i don't have a lot of ram.
 I installed it with with my wireless card but the card didn't show up under networking so i switched to my lan card (RealTek RTL 8139c). 
I have no idea how to get it working or if it's even my computer. I get my Internet from my school's network. i have my desktop running ubuntu and i haven't had a problem with the Internet nor did i have to register on the network like i did with XP.
I am a noob. i didn't want to upgrade to vista because i can't pirate it and XP won't let me upgrade anymore because it was pirated too. Please help

---

### Post by chili555 on 2007-04-01
I'm not sure we understand. You installed with wireless? But now your wireless is not recognized? I guess I also don't understand why you gave us some details about your LAN, or ethernet card but no details about your wireless, that you'd like to get going.

Please open up a terminal and issue a command: ```
lspci -v | grep Network
``` and tell us what it says about your wireless card.

---

### Post by finisdiem on 2007-04-01
the output for lspci for my card is:

02:00.0 Ehternet Controller: Atheros Communications, Inc. AR5005g 802.11abg Nic (rev  0) 
       Subsystem: D-Link System Inc Unknow device 3b08
       Flags: medium devsel, IRQ 9
       Memory at 12000000 (32-bit, non-prefetchable) [disabled] [size=64K]
       Capabilities: <access denied>


I told you about my LAN because i put the LAN card in after installation to see if it would work. it showed up under Networking but still no Internet. i want the wireless to work so that i can take my labtop to class.

Thanks for the reply! :-)

---

### Post by finisdiem on 2007-04-01
i installed from an alternative install cd, i had my wireless card in thinking it would be setup automatically, but it didn't work thats why i put in the LAN card

---

### Post by chili555 on 2007-04-01
Your wireless should spring to life, if you install *linux-restricted-modules*. It is, I believe on your CD. Do the following with the CD in the drive:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install linux-restricted-modules
``` Then see if your card shows up and can be configured.

Is your LAN card a pcmcia stick-in-the-slot card? Or built-in?

---

### Post by finisdiem on 2007-04-01
it's stick in pcmia, like the wireless card

---

### Post by finisdiem on 2007-04-01
after typing what you said in the terminal i got this output "E: Couldn't find package linux-restricted-modules"

---

### Post by finisdiem on 2007-04-01
i found "linux-restricted-modules-386" in synaptic i'm installing them now

---

### Post by finisdiem on 2007-04-01
well that worked! My labtop recognizes it, and it is working but i can't get on my network, i think it is a network problem i'm not sure what to use for Essid, i used "NEC Wireless" thats what it was called on my Hallmate's computer. i think i'll tak it into IT to have them help me, but they aren't Linux friendly. 

THANX!

---

### Post by chili555 on 2007-04-01
Glad it's working for you! Let's get you on line, now. Open a terminal and do: ```
iwlist ath0 scan
``` Your wireless interface is ath0, right? You will get a result something like this:```
Cell 01 - Address: 99:12:9E:46:9C:76
                    ESSID:"WEST5214"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:18/153  Noise level:12/153, etc.
``` Oops! That's actually my neighbor! The ESSID here, WEST5214, is what you are looking for there. If the one you find actually has a space in it, you may have better luck putting it in quotes: "NEC Wireless" In the world of wireless security, remember NEC is not the same as Nec is not the same as nec. As Miss Johnson said in 6th grade, neatness counts.

Good luck and post back if we can help.

---

### Post by finisdiem on 2007-04-02
thanx i just got out of class that why i had such a long reply. I took my labtop to the IT department they told me what the ESSID would be i had the internet for about 2 minutes after seting the ESSID then it was gone. I got four cell adresses that turned out 4 ESSIDs, "NEC Wireless", "NEC Wireless", " ", and "hpsetup". i tryed both "NEC Wireless" and "hpsetup" but the didn't work. I'm still stuck

---

### Post by chili555 on 2007-04-02
Did you try NEC Wireless in quotes, "NEC Wireless" when you put in your settings? We could use the router's MAC address, too, from the scan results. Like here:```
Cell 01 - Address: **99:12:9E:46:9C:76**
                    ESSID:"WEST5214"
```

---

### Post by finisdiem on 2007-04-02
Yeah i tried the MAC address and putting the quotes in. Like is said earlier, i had internet for two minutes, just enough time to load google and start to try to download updates but i lost it soon after that. when i had it the i had just NEC Wireless as the ESSID. Is this just a network problem now?

---

