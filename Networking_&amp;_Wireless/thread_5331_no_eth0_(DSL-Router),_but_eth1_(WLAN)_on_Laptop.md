---
title: "no eth0 (DSL-Router), but eth1 (WLAN) on Laptop"
date: 2004-11-17
forum: Networking &amp; Wireless
---

### Post by Manu on 2004-11-17
Hi folks,
I'm very glad I foud Ubuntu. It's the first distribution, which got my wlan working and has no problems with laptop and screen resolution.

But it's also the first distribution, which won't work with my normal dsl router.
When I navigate into "network control centre" I can only see eth1, eth0 is nowhere.

Some people said, I may be realted to ipv6 and linked the following thread:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=2443](https://bugzilla.ubuntu.com/show_bug.cgi?id=2443)

But this workaround (sudo sed -i -e 's/^alias *net-pf-10 *ipv6/alias net-pf-10 off/'
/etc/modprobe.d/aliases) gave an error to me. (Can't write, can't find)

Is there anyone, who could help me?

Funny thing: Ubuntu Live CD works with eth0 (dsl-router), but doesn't recognize my wlan-card.

Best regards and thank you guys in advance,
Manu

---

### Post by randy on 2004-11-17
You may have to setup pppoe in order to connect over dsl.  I don't know if that's configured by default on the installation.

---

### Post by dataw0lf on 2004-11-17
Could you give us the output of ifconfig ? Perhaps you're eth0 isn't getting written to /etc/network/interfaces.
Cheers, 
dataw0lf

---

### Post by Julius on 2004-11-17
This is a bit confusing. I don't know how linux handles adsl modems, but as far as I know, eth(x) is for ethernet cards.

Routers are not part of your computer's hardware, but your ethernet card is. Then I guess you have an ADSL router connected to an ethernet card in your PC. 


1) If eth1 is beeing used by the wlan card, that's because Ubuntu somehow recognizes eth0 (because, logically, the first ethernet card will be listed as 0 :P)
2) Do an ifconfig. You should get 3 blocks of information. eth0, eth1 and lo. Is it showing the correct data (IP, default gateway...) for eth0?
3) If ubuntu from LiveCD can use eth0 but not eth1, and ubuntu installed from HD can use eth1 but not eth0, I'm 90% sure it's because an IRQ conflict problem. I had the EXACTLY the same problems with my soundcard/ethernet card. They both worked great in Knoppix, but only the Ethernet OR the sound worked when linux was installed (depending on the distro :P). If the sound card was bios disabled, then the ethernet would work perfectly.


When I first installed ubuntu I had problems with my sound card. Both eth/snd cards worked perfectly on Windows and Knoppix from liveCD. I run something on the console that said something like "not listening in IRQ10". I knew IRQ10 was soundcards irq (set in bios), so I went to bios and changed it: it works now!

If your ethernet card is motherboard-integrated, I think it will be easy to configure its IRQ port. You can try :P

---

### Post by FLeiXiuS on 2004-11-17
You need to setup PPPoe for adsl.

```
sudo pppoeconf
```

That should help you out on your way.

---

### Post by Manu on 2004-11-18
Guys, you're fabulous! Great, such a huge amount of answers.
I'm right now in university, where I can only get online with [Cisco VPN-Client](http://www.google.de/search?hl=de&q=Cisco+VPN+Linux&btnG=Google-Suche&meta=), which is quite to hard for me at the beginning.  :-# 
I will try later, when I'm at home.

Just to clearify this:
I *can*  see my ethernet card (Realtek) in Control-Center, but eth0 isn't shown in network-admin.
All tips sounds helpful, so we'll see later...  :) 

Thank you!

Best regards,
Manu

---

### Post by Manu on 2004-11-18
So, now at home, I can test everything.

Viewing /etc/network/interfaces shows me, that eth0 doesn't exist.
```
# This file...
#and how...

# The loopback network interfaces
auto lo
iface lo inet loopback

# The primary n i
iface eth1 inet dhcp
           #wireless-* options are implemented by the wireless tools package
           wireless-mode managed
           wireless-essid any
           name Ethernet LAN-Karte



auto eth1
```


When I try sudu pppoeconf, 2 Devices are found: eth0 and eth1.
Then the search for PPPoE-Access-Concentrator begins and ends up with nothing found.

So, Julius, perhaps it's your third point, but please don't be upset.
I don't know, how to deal with that.

So, hopefully you could send me some tipps...?!

Best regards,
Manu

---

### Post by mr_ed on 2004-11-18
This won't solve your problem, but you have a DSL Router, yes?

You may or may not need pppoeconf, then, because you're most likely getting DHCP from your router.  If the router has pppoe software on it, you can just set it up and leave it.

Can you modprobe the driver... ?

Somebody up there has a good point.  Shouldn't the wireless be some other interface type?

Can you do a quick test and comment out the "auto eth1" in /etc/network/interfaces?  Also the wireless comments in the eth0 section...

---

### Post by Manu on 2004-11-18
[QUOTE=mr_ed]Can you modprobe the driver... ?

Somebody up there has a good point.  Shouldn't the wireless be some other interface type?

Can you do a quick test and comment out the "auto eth1" in /etc/network/interfaces?  Also the wireless comments in the eth0 section...[/QUOTE]
Sorry, to say so. This upper code-section is wrong. It's eth1, not eth0 in there.
Loop up, I corrected it. Sorry!

Yes, I *have* a DSL-Router. As I said before, everything's fine with live-cd concerning eth0.

So, modprobe "the driver" does mean what?

Is it necessary, after knowing that code was wrong, to uncomment "auto eth1"?

Thank you very much.

---

### Post by jdong on 2004-11-18
warping to networking forum...

---

