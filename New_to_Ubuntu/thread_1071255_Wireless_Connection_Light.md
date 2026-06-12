---
title: "Wireless Connection Light?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by deeejz on 2009-02-15
OK, i dual booting ubuntu and vista, but i can't seem to figure out how to connect to my wireless modem? Help me:(

---

### Post by deeejz on 2009-02-16
Im dual booting ubuntu and windows vista on a compaq presario laptop, in vista my wireless connection light turns blue when i press it, allowing me to connect to my wireless modem, but in ubuntu it stays red, even when i press it, so i can't connect unless i have a chord:(

---

### Post by deeejz on 2009-02-16
desperation bump:(

---

### Post by jimrz on 2009-02-16
Try posting the make / model / chipset of thw wireless card you are trying to setup. This will give the folks here something to work with and, possibly allow others with the same card to help you get it going.

If you do not know the card info, on the panel go to Applications > Accessories > Terminal then type
```
lspci
```
and enter. If, after reading the output, you are still unsure just post the entire output here.

---

### Post by deeejz on 2009-02-16
> **jimrz said:**
> Try posting the make / model / chipset of thw wireless card you are trying to setup. This will allow others with the same card to help you get it going.

If you do not know the card info, on the panel go to Applications > Accessories > Terminal then type
```
lspci
```
and enter. If, after reading the output, you are still unsure just post the entire output here.

Sorry, its not a card im trying to connect to a modem. Linksys if that helps

---

### Post by jimrz on 2009-02-16
> **deeejz said:**
> Sorry, its not a card im trying to connect to a modem. Linksys if that helps

OK, so are you trying to connect your laptop to the Linksys router or modem or whatever via wifi? Also, is the light that should turn blue on the laptop? If so, then it would seem that it is the laptop's onboard wifi card that you are having trouble with and that we need to get the info on. If not, then I misunderstood your question and apologize.

---

### Post by deeejz on 2009-02-16
> **jimrz said:**
> OK, so are you try to connect your laptop to the Linksys router or modem or whatever via wifi? Also, is the light that should turn blue on the laptop? If so, then it would seem that it is the laptop's onboard wifi card that you are having trouble with and that we need to get the info on. If not, then I misunderstood your question and apologize.

Yes im trying to connect my laptop via wifi to my lynksis router. The light is on the laptop, its actually a button, it is red when wifi is not enabled, when you press it it turns blue saying that wifi is enabled. When i press it in Ubuntu it stays red, but in vista it turns blue and lets me connect to the internet.

---

### Post by jimrz on 2009-02-16
> **deeejz said:**
> Yes im trying to connect my laptop via wifi to my lynksis router. The light is on the laptop, its actually a button, it is red when wifi is not enabled, when you press it it turns blue saying that wifi is enabled. When i press it in Ubuntu it stays red, but in vista it turns blue and lets me connect to the internet.

OK, then do what I suggested above and give folks a shot at helping. Without more specific info there is little chance of anyone being able to guess what might work. Plenty of people here that are willing to help, but you have to be post enough specifics in order to give them a chance.

---

### Post by deeejz on 2009-02-16
are you saying to post the specs of my card? I dont think its a problem with that because it works fine in vista

---

### Post by jimrz on 2009-02-16
> **deeejz said:**
> are you saying to post the specs of my card? I dont think its a problem with that because it works fine in vista

exactly ... you probably just need to get the driver installed. also try, from the panel going to System > Administration > Hardware Drivers and see if there is a restricted driver available there.

---

### Post by stalkingwolf on 2009-02-16
You can also try clicking on the network icon ( double computer top right)
and see if your linksys connection is selected.  If there are other
wifi connections close you will need to choose the one you want to connect to.

---

### Post by deeejz on 2009-02-16
> **jimrz said:**
> exactly ... you probably just need to get the driver installed. also try, from the panel going to System > Administration > Hardware Drivers and see if there is a restricted driver available there.
Ok heres what terminal said:


dj@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

when i went to hardware it said no proprietary drivers are in use on this system. And one more thing, when it was booting up i saw 'firewall bypassed (wifi disabled) in the scrolling text..?

---

### Post by avtolle on 2009-02-16
[http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) is one way to try to get your Ahteros card recognized and working.

BTW, the light doesn't always change colors when not using the Windows drivers for a wireless card; to check, as has been suggested, once you have installed the Atheros driver as set out above, click on the two computer (Network manager icon) in your panel, and see if wireless is enabled.

---

### Post by 5BallJuggler on 2009-02-16
Try This, your problem is known in 8.10

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by deeejz on 2009-02-16
Sorry im kind of lost. 5ball, i followed the link and did everything but i forgot to enable the linux  backport packaged, how do i do that? and since i have already done it without enabling the backport package do i need to erase it and start over?

---

### Post by ____ on 2009-02-16
Hi, i also am dual booting ubuntu 8.10 and vista and my wifi button does not work either. do you need a driver for the button itself.

---

### Post by deeejz on 2009-02-16
Can anyone tell me SPECIFICALLY what to do? I would really like to get this up and running but if i can't connect then im going to have to uninstall it

---

### Post by stalkingwolf on 2009-02-17
Try this
go to System >Administration > Network.
click unlock , enter your password.

Does your wireless connection show up here?

---

### Post by ashwinhgtx on 2009-02-17
Even though your wifi light might not turn blue, wifi might still be working. After turning on wifi in vista shutdown your laptop and boot into ubuntu. Click the network manager icon in your system tray and see if any networks are available. Connect to the appropriate network if it's there.
The wifi light never lights up on my thinkpad even though wifi is working. But it lights up when if i use windows.

---

### Post by 5BallJuggler on 2009-02-17
> **deeejz said:**
> Sorry im kind of lost. 5ball, i followed the link and did everything but i forgot to enable the linux  backport packaged, how do i do that? and since i have already done it without enabling the backport package do i need to erase it and start over?

Open a terminal and type
[B]
gksu gedit /etc/apt/sources.list[/B]

Remove # sign in front of the lines that state:
#deb http//gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http//gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse


Close the file, you will be asked if you want to save it, click on "Save"

Then carry on from that step. in the [How to]

---

### Post by wally the duck on 2009-04-11
I also have a Compaq (CQ60 210US) laptop and am dual-booting Vista and Ubuntu.

The wireless card is an Atheros.

I have the Jaunty (beta) Ubuntu installed. I could not get the wireless card to work. What fixed it for me was to 1. go into the bios and set the network to be enabled at startup and 2. shut off bluetooth. No other settings, fixes, patches, changes, etc.

Now it works pefectly - except that the orange light never does turn blue.

---

