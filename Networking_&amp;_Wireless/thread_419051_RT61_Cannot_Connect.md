---
title: "RT61 Cannot Connect"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by computergee on 2007-04-22
I have a Belkin F5D70110 with an rt61 chipset and I can't seem to get it to work at all. I had it working with the RaLink drivers, but I don't having to edit the .dat file every time I want to connect to a new network. I thought the serialmonkey drivers should make this card work out of the box. I can't even connect to my network when it's open (no security enabled). I click on network manager, than on the name of my wireless network, but it stops at "Activation stage: Configuring device". What steps should I take to get this card to connect?

---

### Post by sblanzio on 2007-04-23
try looking up here:
[http://ubuntuforums.org/showthread.php?t=415693](http://ubuntuforums.org/showthread.php?t=415693)

hih

---

### Post by computergee on 2007-04-24
Thanks but that is for the RaLink drivers, which require you to manually type in the SSID of the network you want to connect to in a data file, and was a huge pain in the butt for me. Aren't the serialmonkey drivers included in 7.04?

---

### Post by whayong on 2007-04-24
Hey!  I have an MSI RT61 card in a fresh install of Feisty.  It seems to be working right now (knock on wood).  I am conected via static IP with WEP here at work.  I didn't install anything.  I just used "manual configuration" instead of the roaming feature.  Strangely, I couldn't for the life of me get this same card/computer to connect here at work when I was on Edgy.  Now I have to try it at home with dynamic IP and WPA (crossing fingers).

So my suggestion, try figuring it out with out installing anything.  At first, I couldn't seem to get connected but after a reboot, here I am posting.

---

### Post by computergee on 2007-04-24
I tried using a static ip on the Kubuntu live cd, but wouldn't work. Maybe because I didn't (couldn't) reboot. I'm going to try a full install, thanks for the tip.

---

### Post by u002697 on 2007-06-05
Ubuntu 7.04
wireless via  Linksys WMP54G V4.1 (RT61)

after playing with this all weekend, installs, re-installs, etc.
determined that everything was working, i was connected to router, was assigned IP address (via DHCP), .... but still couldn't ping internet addresses

finally gave up  and went with workaround - restarted network from  /etc/rc.local

$ sudo gedit /etc/rc.local
#
ifdown ra1
ifup ra1
exit 0
# note:  following works too
#/etc/init.d/networking restart
#


it works.  doesn't delay startup too much.

so,  if you're using RT61, unless you want to install new drivers, etc
try
$sudo /etc/init.d/networking restart

if that works, (you can access or ping internet), add commands to /etc/rc.local file

not elegant.  But works consistently.

---

