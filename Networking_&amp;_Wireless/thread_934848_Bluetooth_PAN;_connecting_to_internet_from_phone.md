---
title: "Bluetooth PAN; connecting to internet from phone"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by peddy on 2008-10-01
I want to set up a Bluetooth PAN to share my internet connection from my phone (Sony Ericsson w950, which supports Bluetooth PAN). So far, I've paired the phone, and I can get the bluetooth interface, bnep0, to appear in ifconfig. I did this using pand. 

Are there any other steps to take, or should the phone be able to access internet?

If I connect to the PAN from my phone, I cannot access the internet. I'm pretty sure I've configured my phone correctly (it's pretty straightforward), so the I probably need to configure internet connection sharing on my ubuntu box.

Please can anyone help? I'd love to be able to go on the net from my phone.

Thanks

EDIT:I phrased my question incorrectly. I was wondering if I could connect my phone to my computer, and use the computer's internet connection to browse the web *on my phone.*

---

### Post by Kevbert on 2008-10-01
Please take a look at [COLOR="Red"][this]("http://www.geekishblog.com/2008/06/connecting-to-the-internet-via-your-cellphone-in-linux/")[/COLOR].

---

### Post by peddy on 2008-10-01
Thanks for the link, however I phrased my question incorrectly. I was wondering if I could connect my phone to my computer, and use the computer's internet connection to browse the web *on my phone.*

Sorry for the confusion.

---

### Post by peddy on 2008-10-04
Ok, I got the PAN sorted; bnep0, my BT iface, has an pingable IP. But it can't access the internet!

Help me please :D

---

### Post by Brigrat on 2009-01-12
Well here goes.  Maybe I am over doing this or missed the boat completely.  I am using a stinkpad T42, wth a BlueSoleil BS002 mini dongle.  In windows i was able to do a PAN connection with the BlueSoleil software with no issues.  I have tried the following in Ubuntu hardy

A.  NM I could bond the phone, start pan on the phone but never get any kind of connection.  I could see a Bnep0 but never get a connection.  

B.   I located and installed the Linux/Ubuntu software from BlueSoleil, but never even see the dongle - they are working on that.  

C.   I switched from NM to WICD, now i can not even see the D*%$ phone.  good thing my hair is short would be pulling it out by know. 

    I am using a Samsung Blackjack2 (i617) and the phone is great runs like a champ on WM6, I am sure that the phone is not the issue.  So the real question is has anyone anywhere at anytime ever gotten a BT PAN setup to work, or got a DUN connection to work?  I have seen more discussions on this than I care to try and remember.  HELP PLEASE!!!!!!!!

---

### Post by eee1000huser on 2009-02-23
Hi did anyone manage to set this up with Ubuntu 8.10? It seems hcid.conf is missing...

I can see pan0 but not bnep0...

Any ideas?

Thanks

---

### Post by Brigrat on 2009-02-23
I am having great success with the embedded connection manager.  I use it for both blue tooth and tethered with no issues.  Let me go back and check all my notes and i will get back to you.  Blue Soleil has a great package, but no current support for intrepid, just hardy.

---

### Post by eee1000huser on 2009-02-24
Which embedded connection manager?

So does this mean you don't have it running on Intrepid? Only on hardy?


Cheers,

-e

---

### Post by Brigrat on 2009-02-24
The network manager should load automatically.  it is under:
/system/preferences/network configuration/  Net manager 0.7.0.  It includes support for tethering your phone, wireless connection, wired connection etc.  Works very well.  Blueman is an outstanding utility for handling all of your Bluetooth needs as well.

---

### Post by walmis on 2009-02-25
> **peddy said:**
> I want to set up a Bluetooth PAN to share my internet connection from my phone (Sony Ericsson w950, which supports Bluetooth PAN). So far, I've paired the phone, and I can get the bluetooth interface, bnep0, to appear in ifconfig. I did this using pand. 

Are there any other steps to take, or should the phone be able to access internet?

If I connect to the PAN from my phone, I cannot access the internet. I'm pretty sure I've configured my phone correctly (it's pretty straightforward), so the I probably need to configure internet connection sharing on my ubuntu box.

Please can anyone help? I'd love to be able to go on the net from my phone.

Thanks

EDIT:I phrased my question incorrectly. I was wondering if I could connect my phone to my computer, and use the computer's internet connection to browse the web *on my phone.*

Blueman supports this, it will automatically enable the dhcp server and setup iptables.
Make sure you have dnsmasq-base installed, click "Network access point", click "enable routing" and click apply :)

[IMG]http://blueman-project.org/images/stories/screenshots/1.0/screenshot_02.png[/IMG]

---

