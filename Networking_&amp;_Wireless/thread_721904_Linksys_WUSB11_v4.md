---
title: "Linksys WUSB11 v4"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by jacoblyles on 2008-03-11
Howdy Folks,

Ubuntu installation went fine, but I can't get my USB wireless card to work, linksys model WUSB11 v4.

Network manager does not have a wireless option listed. I have the windows drivers available if needed. I have been through many contradictory tutorials and I can't seem to get it to work. If anyone knows how to get this working, I would be most grateful.

Thanks,
Jacob

---

### Post by barney_xuf on 2008-03-11
Jacob,

I'm having the same problem ... WUSB300N wireless LinkSys card and a LinkSys wireless router.  Best I've found so far is to install NDISWrapper, but the install instructions assume a lot more knowledge (mostly paths, methinks) than is likely for a new user.  I'll keep close watch on your thread, and if I luck into something, I'll add it on.

Make a good day ...
                               ... barn

---

### Post by jacoblyles on 2008-03-11
I actually managed to install NDISwrapper and direct it to my driver. My computer still has no idea that there is a wireless device sitting on its USB port, as far as I know.

---

### Post by jacoblyles on 2008-03-11
OK. Fine. I give up. Anyone know a wireless USB card that works well with Ubuntu? I'll buy it. The money is worth less to me than the time.

---

### Post by markeee on 2008-05-02
jacob...[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper))

have you looked at that? I followed that and it works

I can connect-but not with wep

trying to resolve that atm

---

### Post by TriMenToR on 2008-05-02
Hi jacoblyles and barney_xuf,

I have a WUSB11 ver2.6 and I had problems as well. I saw the available networks sometimes but I couldn't connect to them. Also the NM asked WEP over and over again.

This worked for me:

sudo ndiswrapper -i (<XP_DRIVER_FROM_CD>.INF)
sudo modprobe ndiswrapper
sudo ndiswrapper -l (to list the dinstalled deviec and see if it is working)

If this is done you need to configure your wireless network by hand. Turn off roaming mode and use a static IP instead of DHCP. If you configure your wireless network on this manner your WEP should work too.

If you have any problems check if firefox is working in online mode! After a clean installation it was turned off. I noticed this because ping and wget worked.

I hope this works for you!

With kind regards.

---

### Post by markeee on 2008-05-04
TriMenToR

So specify static IP not via DHCP? I had been trying to obtain an IP via DHCP - which would work IF there was no security i.e. WEP enabled on the wireless router

The minute wep is enabled i just get 'No DHCP offers'

I shall try setting a static IP

cheers

---

