---
title: "3com Wireless LAN Card OfficeConnect"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by davebradford on 2007-02-11
hey people, i'm having some really big problems just interested to know if anybody has gotten a 3com office connect PCIMA to work on 6.10? i can't seem to get ubuntu to reconise the new card. Ubuntu used to reconise my Netgear wireless card straight away :(

---

### Post by davebradford on 2007-02-11
any body around who knows anything how wireless cards? really wud be chuffed if someone cud help me out :D

---

### Post by chrish670 on 2007-02-23
> **davebradford said:**
> hey people, i'm having some really big problems just interested to know if anybody has gotten a 3com office connect PCIMA to work on 6.10? i can't seem to get ubuntu to reconise the new card. Ubuntu used to reconise my Netgear wireless card straight away :(

Hi Dave, 

Whats funny, Is I came here looking for help with the exact same card. I went to 3Com's GNU Linux driver site online, and looked up an rpm file of drivers for 3CRGPC pcmcia 'office connect' card and came up empty handed.  Seems theres only a few builds of linux that are supported there. e.g Red Hat... SuSE. The driver needed isn't even listed. I plan to call the place I recieved my card from and ask why I was shown a D-link card when I ordered -  but wound up with a 3Com card instead.

UPDATE: 
Apparently, this card is only supported through windows. (XP, 2000,ME and 98SE) Well shucks.  I sense an RMA forthcoming.

---

### Post by ericdegen on 2007-09-14
I can confirm still no love for this nic, under feisty. After about an hour of trying, I'll just chuck another one in.

---

### Post by Ctrl-Z on 2007-12-07
Got this card (3COM Wireless PCMCIA OfficeConnect 3CRGPC10075) working under Ubuntu 7.04 with ndiswrapper (WPA2 with Linksys WRT54GS router). Followed general steps, but can post if anybody interested.

---

### Post by Ctrl-Z on 2007-12-15
So, on second thought, I decided to post my steps anyhow - even for my own later references.

As I have said above, I have 3COM Wireless PCMCIA OfficeConnect 3CRGPC10075, Ubuntu 7.04 (and now 7.10) with ndiswrapper; my router is Linksys WRT54GS with upgraded to latest official firmware and WPA2 on; at work I have open unencrypted wireless network with very limited abilities (so I prefer wired connection).

Drivers I got from a CD that came with the card, although you can find latest one on their website (currently - [http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3CRGPC10075&order=desc]here]("http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3CRGPC10075&order=desc")). These files are regular zip-files and can be simply unpacked, to find inf-file for ndiswrapper. Then I installed latest ndsiwrapper from repository and loaded the driver.
[INDENT]sudo apt-get install ndiswrapper[/INDENT]

Then reboot and start ndiswrapper manually
[INDENT]sudo modprobe ndiswrapper
iwconfig[/INDENT]

My card was found and I added ndiswrapper to the list of automatically loaded modules.

Then I needed WPA2 for my home network. I found an article about setting up of WPA2 here:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

[INDENT]To update the source list run the following command

sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant[/INDENT]

After that they suggested to do
[INDENT]sudo /etc/init.d/dbus restart[/INDENT]
or reboot. I decided to be quite paranoid, played safe and used reboot. :)

Should work after that.

---

