---
title: "Ubuntu laptop as a Wireless Access Point"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by isenalim on 2007-04-01
Hi,
I would like to use my ubuntu laptop, which is connected to the internet through an ethernet router, as a Wireless access point for other laptops in my house.

I have found a couple of howtos and software but they seem to work only with wireless cards based on a Prism chipset. The laptop that should be used as WAP is an HP Pavillon DV1000.

I am an almost newbie in linux and networking, so please suggest me some simple soolution or howto.

Thanks a lot everybody!

i.

---

### Post by jorno on 2007-04-02
Hello.

Are you running Ubuntu Fiesty?

From what I can see at my own laptop running Ubuntu Fiesty, containing one NIC and one WIFI-card, I can use the "NetworkManager Applet" to Create New Wireless Network. After this is done, other computers could connect to this wireless network I've created.

If you get that going, you've accomplished the first step. After that, we'll need to get a DHCP running, so that the other computers will receive an IP-adress.

The last step is to your Ubuntu to share the connection (MASQUERADE'ing with iptables - could try google when getting this far).


I can't really try this out fully on my own network right now, but feel free to ask if I need to further explain some of the details - or maybe point you in the right direction. I'm sorry I can't give you a complete howto of this right now, but as I'm pretty new to the Ubuntu distribution myself as for now, I feel a little lost... ;-)

---

### Post by isenalim on 2007-04-02
Thanks!
That seems to be a very good hint. Indeed the hard part was to create a Wireless network. Once this is up, I guess I should be able to proceed following one of the many howtos written for similar configurations but with two ethernet cards instad of an ethernet and a wireless.

The only problem is that I am not running Feisty but Edgy and I wouldn't like to upgrade soon, that it's always a little dangerous...

So, any idea for Edgy?

Thanks
i.

---

### Post by jorno on 2007-04-03
Hello again.

Well, it was only a wild guess from my side that maybe Edgy didn't have the same NetworkManager-applet as Fiesty has.

But may be, if you search the package system, that you could install the NetworkManager applet into Edgy also?

If not, I've heard rumors that Fiesty is going stable any moment now. And then it shouldn't be that much hussle to dist-upgrade. =)


Hopes this helps. :)

---

### Post by isenalim on 2007-04-03
Hi,
indeed the applet is in the Edgy repository too. So I am gonna try if I manage doing it later on.
Thank you for your help!

---

