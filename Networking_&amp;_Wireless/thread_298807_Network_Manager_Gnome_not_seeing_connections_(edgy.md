---
title: "Network Manager Gnome not seeing connections (edgy)"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by CheeseEatingBulldog on 2006-11-13
A long term peeve of mine has been that the network-manager applet does not see the connection that I evidently do have (in system-admin-networking there is a connection, and I can connect to the internet). So why does the damn applet say there is no connection?

I googled and found that it may not like static ips, so I changed to a static and still no joy. Any ideas?

---

### Post by dcrowder32 on 2006-12-14
Anybody?  I have same problem.  Wireless working fine, but network manager only looks at wired connection (which I disabled).

---

### Post by mathgru on 2006-12-19
> **dcrowder32 said:**
> Anybody?  I have same problem.  Wireless working fine, but network manager only looks at wired connection (which I disabled).

do this:
sudo gedit /etc/network/interfaces

remove all but

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

It should work after this.  Hope this helps.

---

### Post by timmay on 2006-12-20
I ended up reinstalling after I couldn't work out why my Wi-Fi stopped working. After reinstalling Ubuntu for the second time today Wi-Fi still didn't work. I was completely stumped, I couldn't work it out and resorted to replacing the mini-PCI card with another one. This to my horror had no effect!

Now I've fixed it and I'm feeling really silly now coz it was something so stupidly simple yet I had wasted my whole day installing Ubuntu and then reinstalling Ubuntu. I really don't want to say this but "Windows saved the day" (I'm gonna cry now). I booted back into Windows after my frustration to check to see if Wi-Fi was working there. It wasn't. An Icon in the notification area said it was disabled! I pressed Fn + F2 to turn on the Wi-Fi and hay presto it was working again. I then booted back into Ubuntu to find that I could detect my network again and connect! Whoo!!!

PS I has tried the Fn + F2 key combination in Ubuntu but this had not worked.

I've now disabled the Fn + F2 enable/disable function in the BIOS and set it to application controlled.

As for Gnome Network Manager that gave me a very nice surprise to day which has made my happier again. This nice surprise was the ability to connect to my home WPA secured network. All I had done was install network-manager-gnome. I'd done none of that faffing about that is normally required to get WPA working!

... Oh and the laptop I'm using is a bog standard (min spec) Inspiron 6000.

---

### Post by Yenny on 2006-12-21
Well, when Ubuntu Edgy came out, my friend and I jumped at it. And at first Network Manager worked beautifully, changing profiles and activating my Wi-Fi (I have a hardware switch for it so I made sure it was on.) I would click into my Networking and pick my home profile, which had the network name and network password. Once I usually clicked okay, it would pop up saying it was activating erm, (it's been so long I forgot what it actually said). After that, it was internet city, but then, it stopped doing that one day about 3 weeks later. 

My wireless connection (ath0) no longer connects. so my friend told me to download dhcpcd.

> sudo apt-get install dhcpcd

after this, I plug in:
> 
sudo iwconfig ath0 essid 2WIRE001 key 1234567

replace the 2WIRE with your network name and 12345 with network key. After that:

> sudo dhcpcd ath0

which gives me this:

> JenJen@tynik:~$ dhcpcd.exe: wrong interface name "ath0"

Either way, I can connect to the Internet wonderfully afterward. I don't understand why it keeps seeing ath0 as wrong. It's rather annoying...
Any help with this would be much appreciated, I'm going to try a few of the suggestions up there, though I think my friend already tried it all first. 
-Yenny

---

### Post by eexpress on 2006-12-25
network-manager-gnome need you clear all except lo setting within /etc/network/interface. 

i also have a problem, seems can not solved by author's design way:
you also must enabled your dhcp in your wireless router.

my office router just need a ip, so nm-applet can not connect(for it only support essid/key mode).

otherwise, nm-applet is works well at my home router.

---

