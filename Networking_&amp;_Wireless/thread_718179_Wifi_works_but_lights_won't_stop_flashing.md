---
title: "Wifi works but lights won't stop flashing"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by Jordanwb on 2008-03-07
I've (hopefully) successfully installed a Linksys WPC54G V7 Wifi card on Ubuntu Desktop 7.10 As a matter I fact I'm using it right now. However the Power and Link lights are flashing in sync. Also when Ubuntu starts up (loading screen) the lights alternate. I'm more concerned about the former rather than the latter light sequence. Anyone else had this problem?

---

### Post by Paris Heng on 2008-03-07
Some info: I think most probably is your driver problems, just look into the firmware for the driver.

---

### Post by Jordanwb on 2008-03-07
So you're suggesting I try another .inf file? I used ndiswrapper to "install" the driver would I need to uninstall the driver? I'm not pro at Linux.

---

### Post by rustybronco on 2008-03-07
I have a dynex pcmcia card connected as I type, it does the exact same thing and has since november. if you look at it when you first turn it on only the power light will be on, then they will alternate, then both will blink when the network is up.
You know what, don't worry about it.
if it keeps working fine, I say leave it alone. 
[http://ubuntuhcl.org/browse/product?id=308](http://ubuntuhcl.org/browse/product?id=308)

lspci -nn info.
> 02:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

---

### Post by Jordanwb on 2008-03-08
The exact same series of sequences are happening to me. So I'll take your word on it. If something goes wrong I'll know who to blame (kidding).

---

### Post by Jordanwb on 2008-03-08
I've got another problem. I get the grub boot menu (dual booting XP) I select Ubuntu and I get the loading screen. It get's to about 5% then the screen goes blank if the wifi card is in the pcmcia slot. If I start the laptop with the card out it boots okay.

---

### Post by rustybronco on 2008-03-10
try different boot options such as acpi=noirq... [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

have you checked the logs for any errors?

or try sudo gedit /boot/grub/menu.lst and remove quiet from to kernel line save and exit.
restart with the card inserted, at what point what does it stop loading?
> If something goes wrong I'll know who to blame (kidding). I'll take the blame.

---

### Post by Jordanwb on 2008-03-10
I contacted Linksys using LiveChat regarding the problem, and they said it was because the drivers were made for Windows. I then said that Linux is coming up from the outside and if they don't start making drivers for Linux they'll lose customers. The dude then hung up.

Regarding the hanging o_O?

It hangs after the loading screen. It gets to 100% goes blank (laptop is slow), then nothing, it doesn't go any further.

I'll try what you said regarding that list file.

[Edit]

I searched the file for "quiet" but I couldn't find the line.

---

### Post by rustybronco on 2008-03-10
> **Jordanwb said:**
> I contacted Linksys using LiveChat regarding the problem, and they said it was because the drivers were made for Windows. I then said that Linux is coming up from the outside and if they don't start making drivers for Linux they'll lose customers. The dude then hung up.

Regarding the hanging o_O?

It hangs after the loading screen. It gets to 100% goes blank (laptop is slow), then nothing, it doesn't go any further.

I'll try what you said regarding that list file.

[Edit]

I searched the file for "quiet" but I couldn't find the line.Where were you looking in the boot options when grub starts, or in /boot/grub/menu.lst ?
if it was boot/grub, the **kernel** line will be something like this 2.6.22.17 blah blah... ro quiet splash, i'll post what it looks like when I get home.
***should look like this***
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
**be careful**

---

### Post by Jordanwb on 2008-03-10
I was looking in the .lst file. Since I have something more specific to look for I may have a better chance of finding the link.

[Edit]

I found the line and took out quiet (and only quiet).

[Edit #2]

It stalled again after the loading screen but there was no output.

---

### Post by rustybronco on 2008-03-10
> **Jordanwb said:**
> I was looking in the .lst file. Since I have something more specific to look for I may have a better chance of finding the link.

[Edit]

I found the line and took out quiet (and only quiet).Boot it up and see what it says before it stops.
did you try any boot options first by hitting esc when grub starts, then selecting the kernel line and hitting e for edit, then adding things like this suggests? [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) starting with "For Installed Systems That Need Adjustment"

***edit*** again check things like dmesg,  /var/log/sys.log?, /var/log/boot.log for error messages.
 post the errors you find
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by Jordanwb on 2008-03-10
For those two links you posted I get HTTP 403 errors. The last thing it said had something to do with Display Adapters.

I found out why the screen goes blank. There's something wrong with the monitor or the drivers for the display adapter. I could logon because I heard the noise saying that I'm at the login screen.

[Edit] There was nothing in the logs.

---

### Post by rustybronco on 2008-03-10
> **Jordanwb said:**
> For those two links you posted I get HTTP 403 errors. The last thing it said had something to do with Display Adapters.

I found out why the screen goes blank. There's something wrong with the monitor or the drivers for the display adapter. I could logon because I heard the noise saying that I'm at the login screen.

[Edit] There was nothing in the logs.I could access them a while ago, try it again later.
(its located at the top of this page support>Documentation>Community Docs )

do you know what video chipset you use? **lspci**

---

