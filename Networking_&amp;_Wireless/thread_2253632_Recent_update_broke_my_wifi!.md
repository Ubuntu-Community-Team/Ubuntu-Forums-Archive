---
title: "Recent update broke my wifi!"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by kazakore on 2014-11-21
Updated my system a couple of days ago (18th I think, first internet connection I'd had for over two weeks) and today I've just discovered I can't connect to any wifi! (Don't think I had restarted after the update to discover beforehand.)

When I click on any access point is just says Authorisation Required (when I hover over it) and never even gives me the opportunity to enter a password. There is one Open access point visible from here and it doesn't appear to connect to that either. I am travelling and thus have no way of checking if I can connect to a previously working connection or not.

Luckily I still have the Doze7 install the laptop came with, from which I am posting at the moment, but obviously this will make it very hard to makes any tests, post results, back and forth. No wired connection available either for update over cable!

Please assist me with getting my wifi under XFCE/Ubuntu Studio working again! I don't like Windows!!!

---

### Post by kazakore on 2014-11-21
Anybody?? Some pointers that might help me provide you more useful information?? Some packages which have recently been upgraded for which I can download the debs in an attempt to fix it??

It has been working fine until this update and I have been using 14.04 since the week the .1 release came out (so that should be about 4 months) with no problems until now. All other reported issues seem to be longer standing, ie with all versions of 14.04, and have different symptoms to mine so are of no help.

Wireless is on the N6205 cipset.

My laptop Ubuntu components list:
[http://www.ubuntu.com/certification/hardware/201206-11273/components/](http://www.ubuntu.com/certification/hardware/201206-11273/components/)

---

### Post by kazakore on 2014-11-22
Not solved but I have a work-around to some extent and it has shown the problem is definitely with the XFCE networking modules.

As well as the default XFCE network tools/modules I have also installed in the past kde-nm-connection-editor as the XFCE editor not work with setting up my wireless as an access point which was visible to my mobile phone, whereas the KDE version worked with no problems.

If I click an access point and go to edit it in the XFCE connections editor everything is greyed out and thus there is nothing I can edit! If I try and open it in the KDE editor it takes a couple of minutes to display but appears to find some settings and eventually I get an editable conncetion. If I then add in the password details here it appears to work fine.

So I can also conclude connections to existing networks should continue to work if they did previously. I can not guess why connection yo supposedly open networks also failed.

Hope this gets fixed properly soon as I am travelling and so usually on a different network every 2-3 days and sometimes multiple times every day! Guess it's a bit of a specific usercase so not sure how many people it would have affected. I hope somebody can take these details and work out where the specific bug is to get it fixed in a new update soon :)

---

### Post by kazakore on 2014-11-22
Sod knows what's happening now! I tried running an upgrade once I had managed to connect with the above kde-nm method and now, upon restarting, I can apparently connect to the router but not actually browse anything. In fact I can't even ping the router's IP address!! (192.168.1.1) so something is clearly wrong! Still working fine from Windows so definitely not a network issue!

---

### Post by kazakore on 2014-11-22
Really starting to bug me!! How the flipping heck can it work flawlessly under Doze yet be unable to even ping the router it claims I am connected to under Ubuntu?!?! Makes zero sense to my limited networking knowledge!!! :(

---

### Post by kazakore on 2014-11-24
Strangely it appears to be IP address related. If I'm issued 192.168.1.15 by DHCP the Ubuntu wont connect to the internet and wont even let me Ping the router! (Which seems very strange to me!!)

If I'm issued the same IP while logged into Windows then I ping the router and browse the internet and everything just fine!

Other IPs I've seen myself issued are 192.168.1.3 and 192.168.1.5 and these both work fine on both Ubuntu and Windows when I've tested.

I tried forcing the connection with to take one of these IP addresses with Manual configuration but when doing that it still wouldn't connect to the internet! Not sure if that means maybe there was a IP conflict though...

---

