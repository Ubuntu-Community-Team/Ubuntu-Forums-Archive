---
title: "Wireless USB - Unknown Device :("
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by AnotherMuggle on 2006-08-27
Hi,
I posted a very similar post to this some time ago but I still have not resolved the problem and I'm hoping the situation will fall upon fresh eyes if I repost.

I am trying to use a Safecom SWLUT-54125 USB wireless adaptor to access the internet using Kubunu 6.06.  I think I stand a chance of using ndiswrapper to get it work but I can't even make the computer detect the device correctly.  It comes up in KinfoCentre as Unknown device.

Can anyone help with this?

Thanks, Tom

---

### Post by funchords on 2006-08-27
I have a couple of leads for you...

Your card appears on this list: [http://acx100.sourceforge.net/matrix.html](http://acx100.sourceforge.net/matrix.html)

Which indicates that the ACX111 project may be of some help for your card.  It also indicates that your card uses the TNETW1450 chipset, and other solutions for that chipset should work for you as well.  

See [https://help.ubuntu.com/community/WifiDocs/Device/Fritz%21WLAN_USB_Stick](https://help.ubuntu.com/community/WifiDocs/Device/Fritz%21WLAN_USB_Stick) for one that I found.

I only searched briefly, so you should definitely search more before you dive into one solution or the other.

Hope this helps.

---

### Post by NetworkGuy on 2006-08-27
This is for a Linksys card, but it also uses the ACX111 chipset

[http://www.ubuntuforums.org/showthread.php?t=233565](http://www.ubuntuforums.org/showthread.php?t=233565)

It got me on-line in just a couple of minutes.  Should do the trick for you too if it's the right chipset.

---

