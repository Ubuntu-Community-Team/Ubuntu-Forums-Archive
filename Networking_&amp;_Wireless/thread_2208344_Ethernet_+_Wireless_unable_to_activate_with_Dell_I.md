---
title: "Ethernet + Wireless unable to activate with Dell Inspiron 1520"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by thedoc3 on 2014-02-27
Hi all,

I think the simple fact I'm posting here is the last straw.Over the years I've attempted numerous times to put Ubuntu onto my laptop, but always reverted back to windows do to frustration and issues with drivers and internet connectivity. 

Assuming with years past and onto the latest release of ubuntu, I figured my drivers for my network card would work off the bat, how silly was I.

AS I installed the latest version via USB, eth0 and ethernet connection was shown during installation, and a green tick beside connected to internet during installation. However once finished, I can see no wireless or ethernet connections anywhere. I'm four hours at it now, and really frustrated. Assistance would be greatly appreciated.

**Note** I have no internet access either through ethernet or wireless to the laptop, so apt-get installs are out of the question. I'll need to transfer any relevant files over via usb. I've found a number of threads and guides that claim to solve the problem, but none worked, and I hit a mountain of errors and couldn't complete any steps from what I read in full. 

Below is the various information that might help (Please remember that the laptop is beside me as I post from my main PC, I'm not typing out all the **** its spouting back from commands, so I can't copy and paste all the information)

**LSPCI**
```
Ethernet Controller : Broadcom Corporation BCM4401-B0 100Base-TX(rev02)
Network controller : Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

**iwconfig wlan0**
```
No such device
```

**lsb_release -d**
```
Ubuntu 12.04.4 LTS
```


Really would like help here guys, I want to give Linux a chance, and Ubuntu. It looks ideal for what I want to use the laptop for, but at this point, I really can't be arsed much more.

---

### Post by thedoc3 on 2014-02-27
I've done the following just now, with no joy

[http://ubuntuforums.org/showthread.php?t=2161582&page=5&p=12729240#post12729240](http://ubuntuforums.org/showthread.php?t=2161582&page=5&p=12729240#post12729240)

When trying to do the first set or rmmod I get errors saying resource is busy and no file/directory found

Also to note when I run sudo modprobe -r b43 , or sudo modprobe b43, terminal just hangs there for ages doing nothing

---

### Post by chili555 on 2014-02-27
Please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and tell us if the ethernet is working. If so, we'll fix the wireless in a few seconds.

---

### Post by thedoc3 on 2014-02-28
> **chili555 said:**
> Please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and tell us if the ethernet is working. If so, we'll fix the wireless in a few seconds.

Thanks Chilli, I'm based in Ireland so that post was relatively late last night. I'll try when I get home and let you know.

To add insult to injury, in a final ditch attempt to do some stuff, I dropped the firewall and protections I had, in the event it was maybe causing blockages from the new Os I put on the laptop.

Was maybe about 10 minutes before a virus jumped into my main PC, and has it completely locked down. In desperation I was clicking links like mad on my main PC, and obviously go to a site that "claimed" to resolve the Dell inspiron 1520 issue, but instead put a horrible virus on my machine.

Ironically, its AN Garda Siochana something something, and basically tells me I've to pat €100 to have my poc unlocked. The irony is I'm from Ireland, and it was clearly a scam virus setup by someone from elsewhere. Picture of our little elf president in the corner haha 

So that's going to be priority one this evening, fix my main pc, remove the virus, before hitting back on this laptop. 

It's always a tragedy when I try install Ubuntu :(

---

### Post by chili555 on 2014-02-28
I'm sorry about your trouble. There are a few things I never go without and first is both a hardware and a software firewall. 

I hope you get your Ubuntu going smoothly. In your case, installation offers to install the wrong driver for your 4311 device. I don't care what Broadcom themselves say; I don't care what askubuntu says, the STA driver is incorrect. New-ish users don't know better and accept the wrong driver. Then, not only does your wireless not work properly, but the driver inexplicably blacklists the correct driver for your ethernet! Then guys like me and Varun and Wild Man and others spend all day unraveling a knot.

---

### Post by thedoc3 on 2014-02-28
> **chili555 said:**
> I'm sorry about your trouble. There are a few things I never go without and first is both a hardware and a software firewall. 

I hope you get your Ubuntu going smoothly. In your case, installation offers to install the wrong driver for your 4311 device. I don't care what Broadcom themselves say; I don't care what askubuntu says, the STA driver is incorrect. New-ish users don't know better and accept the wrong driver. Then, not only does your wireless not work properly, but the driver inexplicably blacklists the correct driver for your ethernet! Then guys like me and Varun and Wild Man and others spend all day unraveling a knot.

OK I've no idea what happened, maybe it flicked on WHILE it was doing the purge command above, but ethernet just came on. I've rebooted the laptop to see what happens.

Ethernet light is finally showing on the port, internet access working.

THanks so much, I'll guess that command is what did it. Ethernet now working, it will never need wireless so meh, its being connected by cable to be a 24/7 machine.

Now to get installing ssh,dyanicdns' and sickbeard and all the other goodies I want to do.

THanks again for the help, 

P.S Wireless is actually working aswell

---

### Post by chili555 on 2014-02-28
Awesome! Please use thread tools at the top to mark Solved.

---

