---
title: "Belkin F5D5000ed Network Card"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by alpha on 2006-12-04
I have just installed Ubuntu 6.06 everything is working fine, apart from my Belkin FD5000ed network card is only showing the IPv6 protocol how do I add the IPv4 protocol?

---

### Post by alpha on 2006-12-04
No answers?

---

### Post by FrodoB on 2006-12-04
Are you sure that that is your card model. I see no references to it on the web?

---

### Post by alpha on 2006-12-04
> **FrodoB said:**
> Are you sure that that is your card model. I see no references to it on the web?

Yes it is its a uk model card so you'd have to look on the belkin uk site.

Here it is:

[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=107574](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=107574)

just the version number is slightly different.

---

### Post by FrodoB on 2006-12-04
What is the output of:

lspci -v

Can you see the device in the Networking Menu:

System -> Administration -> Networking

If you you can just configure it with the GUI tools.

---

### Post by alpha on 2006-12-05
> **FrodoB said:**
> What is the output of:

lspci -v

Can you see the device in the Networking Menu:

System -> Administration -> Networking

If you you can just configure it with the GUI tools.

No where to reconfigure it unless I have to be in root? Here is the part of the lspci for the card (it would take too long to write out every entry).

```

0000:02:06:0 Ethernet Controller Realtek Semiconductor Co Ltd RTL- 8139/8139C/8139C+ (rev10)
Subsystem: Belkin 5FD5000 PCI Card/Network PCI Card Flags: bus master, medium devsel, latency 32, irq 201
I/O Ports: at c800 [size=256]
Memory at:  feaffc00 (32-bit, non prefetchable) [size=256]
Capabilities <only available to root>

```

---

### Post by FrodoB on 2006-12-05
If you are using Ubuntu you don't normally have root. When the system asks for a password you enter the password for the person who installed the system.  In command shells you just preface every command with sudo if it would normally require root access.

---

### Post by alpha on 2006-12-05
Okay, now is there are a solution? I have picked something up from the ubuntu wiki, but I'm not sure whether it will work.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6)

---

### Post by FrodoB on 2006-12-05
It certainly will not hurt to disable ipv6, give it a try.

---

### Post by alpha on 2006-12-05
Would it automatically pick up IPv4 then?

---

### Post by FrodoB on 2006-12-05
I don't know, but you don't need ipv6, or at it is highly likely that you do not.

---

### Post by pak33m on 2006-12-05
I do not have all of the links to HOWTO's or other posts in the forum that I used to get my Belkin card working, but I can suggest to you in a nutshell how I got mine working...

I have an IBM Thinkpad T30 laptop & a Belkin 802.11G wireless card Model no. F5D7010.

1.  I copied my Belkin driver from the install CD to my laptop.
2.  Typed **lspci -v** (use sudo if not in the root terminal) to find out driver model (or number) for ndiswrapper.

3.  Installed ndiswapper.
4.  Installed the Belkin driver through ndiswrapper.

(You can find the aforementioned ndiswrpapper & command in the wiki)

5.  Typed **network-admin** (use sudo if not in the root terminal) to configure the Access Point & Encryption Key (if needed - well, I did) for my wireless connection & Activated the athX wireless interface (or wireless connection with Atheros chipset) in the Network Manager GUI.

Alternately...

1.  I read up the info contained in /etc/pcmcia/wireless.opts in order to properly edit in the configuration of my wireless connection parameters, i.e. Access Point, Encryption Key, etc. to start on bootup.  

2.  I also edited /etc/network/interfaces to comment out every auto connection except the lo interface (or loopback, which you need) & added in my wireless connection to start on bootup.  The addin looked like the following:

ath0 autio
iface ath0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXX
wireless-ap XXXXXXXXXXXXXXX

3.  Then I typed **ifconfig athX up**(use sudo if not in the root terminal) to activate the athX wireless interface

4.  That was followed by an **ifconfig athX** (use sudo if not in the root terminal) view the status of the athX wireless interface (You should see an IPv4 IP address if your access point is configured for DHCP.)

5. If you add the Network Admin applet to your panel you will be able to further configure your network connections & verify the status of each one.

I hope my info helps you out.  If not, make sure that you check throughout the community for answers.  That is what I did & have not had problems since.

---

### Post by FrodoB on 2006-12-05
In this case it is a wired card.

---

### Post by pak33m on 2006-12-05
alpha,

IPv4 is just a 32-bit IP address, i.e. 192.168.x.x.  

It can be configured statically (or manually) or by DHCP (if your access point allows it) in /etc/network/interfaces in the athX section.  (If it does not exist you can add it like I mentioned in my mini-HOWTO above).  The section that I am referring to is the following (which had a typo in my last post):

ath0 auto
iface ath0 inet dhcp

I have my wireless connection configured for DHCP, as described above.

---

