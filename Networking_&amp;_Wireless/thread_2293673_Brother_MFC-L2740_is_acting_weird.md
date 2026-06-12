---
title: "Brother MFC-L2740 is acting weird"
date: 2015-09-06
forum: Networking &amp; Wireless
---

### Post by Matthew_Skillman on 2015-09-06
Hi all. Thanks in advance for any help anyone can provide.

I have a brother MFC-L2740 printer connected to my wireless home network. Sometimes it works, and sometimes it doesn't. From my printer's settings I can see its IP address:** 192.168.1.5**
When accessing my router from the browser I can ping it:

[IMG]http://fastspiff.com/images/Screenshot%20from%202015-09-06%2018:22:00.png[/IMG]

When I run from the terminal

> **nmap**** 192.168.1.5**

I get:

> **Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2015-09-06 18:13 EDT**
**Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn**
**Nmap ****done****: 1 IP address (0 hosts up) scanned in 3.03 seconds**

However when I add the** -Pn** I get:

> **Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2015-09-06 18:13 EDT**
**Nmap scan report for BRW90489A96620A.home (192.168.1.5)**
**Host**** is up (0.10s latency).**
[B]All 1000 scanned ports on BRW90489A96620A.home (192.168.1.5) are filtered


[/B]
Any suggestions anyone?

---

### Post by Matthew_Skillman on 2015-09-06
I should also mention that uninstalling and then reinstalling the printer using the brother script** linux-brprinter-installer-2.0.0-1 **will fix the problem for about a day.  Then it will stop working again.  

This is very annoying, because it is also happening to my mother's computer (who is debating switching to ubuntu, YAY!) but she needs to be able to print and if I am not around to uninstall and re-install, she is helpless.  Though she loves how fast ubuntu is on her old laptop.

---

### Post by kurt18947 on 2015-09-06
I've been using networked Brother printers for some time on various flavors of Ubuntu and other Debian based distros. I had trouble with printers going M.I.A. and finally settled on assigning a static I.P. address outside the D.H.C.P. range. It's pretty easy to do with Brother MFDs because they have a numeric keypad. When you use the installer script one of the connection choices should offer 'socket' so the printer's URI will look something like: socket://xxx.xxx.xxx.xxx:9100 (Presuming the printer uses default port 9100.) There are various means to edit printer connections and properties. I'm kind of partial to a package found in the repositories, "system-config-printer-gnome". Once installed I launch it via an app launcher without the 'gnome' at the end. This works with Ubuntu-Gnome and Xubuntu, I'm not sure about Unity. I'm sure there are other ways around this, what I've outlined works for me.

---

### Post by Matthew_Skillman on 2015-09-06
> **kurt18947 said:**
> I've been using networked Brother printers for some time on various flavors of Ubuntu and other Debian based distros. I had trouble with printers going M.I.A. and finally settled on assigning a static I.P. address outside the D.H.C.P. range. It's pretty easy to do with Brother MFDs because they have a numeric keypad. When you use the installer script one of the connection choices should offer 'socket' so the printer's URI will look something like: socket://xxx.xxx.xxx.xxx:9100 (Presuming the printer uses default port 9100.) There are various means to edit printer connections and properties. I'm kind of partial to a package found in the repositories, "system-config-printer-gnome". Once installed I launch it via an app launcher without the 'gnome' at the end. This works with Ubuntu-Gnome and Xubuntu, I'm not sure about Unity. I'm sure there are other ways around this, what I've outlined works for me.

Two questions. First, I thought that what might be happening is that the DHCP is changing my printer's IP randomly, so I might need to assign it a static IP, but I don't know how to do so. I'm not much with networking, but I assume I should do that from my router's settings, as there is no way I can see to do it with ubuntu under system-config-printer, which when I run from the terminal just pops up ubuntu's Printer Settings. The router's settings are arcane to me:

I would think that I would go to DNS on my router:

[IMG]http://fastspiff.com/images/DNS.png[/IMG]

Then edit BRW (that's the printer), but when I click on it I only this screen with nothing about assigning it a static IP:

[IMG]http://fastspiff.com/images/Brothername.png[/IMG]

The other thing is (once again given my limited networking experience) it seems like there is some kind of port setting for the printer which, when the IP changes, will still allow ubuntu to detect it when I use nmap -Pn (which apparently means "Treat all hosts as online -- skip host discovery")

Clueless what that means.

---

### Post by Matthew_Skillman on 2015-09-07
bump

---

### Post by kurt18947 on 2015-09-11
Matthew, I'm sorry to be late getting back to you. On my Brother printers, I assign a static I.P. address via the front panel. I'm not at a machine right now but if you have a 'menu' button, press that then look for 'network'. Somewhere in that menu structure should be entries to select D.H.C.P. or static I.P. address. Brother has a downloadable networking PDF that might be useful to you. It of course doesn't mention Linux.

[https://www.brother-usa.com/VirData/Content/en-US%5CPrinters%5CConsumer%5CNetworkUsersManual%5CNUM_HL_2270DW_EN_2639.PDF](https://www.brother-usa.com/VirData/Content/en-US%5CPrinters%5CConsumer%5CNetworkUsersManual%5CNUM_HL_2270DW_EN_2639.PDF)

I assume there is mention of how to set an I.P. address in your printer's manual.

---

