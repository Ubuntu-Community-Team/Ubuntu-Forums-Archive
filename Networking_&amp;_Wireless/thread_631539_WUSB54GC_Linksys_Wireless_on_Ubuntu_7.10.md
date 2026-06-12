---
title: "WUSB54GC Linksys Wireless on Ubuntu 7.10"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Magoffire on 2007-12-04
I just ugraded to a duel boot with Ubuntu 7.10.

This is my first time useing linux and so far I LOVE IT.

However, I wish to be able to make Ubuntu my primary OS.

The problem is, my wireless card wont connect to my router.

I'm useing a WUSB54GC Linksys Wireless card with WEP 128-bit 26 Hex Digits.  Association Mode is Auto.

The Gnome network thingy at the top of the screen finds the network (the network name is Linksys).

After that it asks for encryption stuff and i pick 128bit Hex and enter one of the keys I got from accessing the router.

Then a graphic appears ontop of the computer representing the network and it just sits there spinning for like 2 minutes before it stops and the window asking for encryption pops back up.

My friend has dealt with this same problem as we both use the same wireless card.

He says that he's fix only works for Linux distros like PCLinuxOS.

PLEASE help me guys.  ANd please try to be easy on me...I'm just getting into this linux thing.

PS. I have full access to the router so if you need more info or have a fix (other than removeing WEP encryption or changeing those thigs) then just tell me.

~ Magoffire

---

### Post by redhatoscar on 2007-12-04
You are almost there. Let me ask you . Did you enable WEP on your Lynksys ? 

Once you enter the wireless configuration info ( SSID , Encryption , KEY , etc ) 
 you need to restart the network service via command line .  Trust me this works . I have 4 laptops all using different wireless cards .

---

### Post by redhatoscar on 2007-12-04
[http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubnet_m/ub_wirless]("http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubnet_m/ub_wirless")

Follow the steps on this link .  Let me know how that works .

---

### Post by Magoffire on 2007-12-06
Hey all, I got it to work :).

Sorry, I should have read the sticky...

---

