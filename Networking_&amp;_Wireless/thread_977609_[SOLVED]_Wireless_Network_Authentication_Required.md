---
title: "[SOLVED] Wireless Network Authentication Required"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Scunnered on 2008-11-10
I bought a laptop and had to call the supplier to be guided through the wireless installation.  The laptop came with 8.10 pre-installed and I was informed in the documentation of a password to enable me to access the system and advised to change it immediately to suit my needs.  This I did and then found out that I was unable to access my Virgin Media wireless network.  On speaking to Virgin I was informed that the WPA password that I required would be that I entered when installing the wireless network.

I followed this advice and found that I could access the network and was able to check my mail and the forum.

Closed down the system and on return a few hours later found that Wireless Network Authentication Required but on attempting to enter the password nothing happened.  No connection was made despite various attempts.  I had hoped that once the initial connection was made that it would be automatic thereafter.

Can anyone offer a solution to this problem.

Thanking you in anticipation.

PS I am being forced to use Doz to send this.  Please rescue me!

---

### Post by Scunnered on 2008-11-10
Once again the threat of having someone assist me has worked.  Left system to post original message and rebooted 8.10 only to find that it automatically connected and I am now up and working again.

Thanks to all who new the right prayers to say.

---

### Post by Vinnyd on 2010-02-03
Hi everyone, My problem is little different..... i get the same message after inputting network name and password.... i click connect and it just pops up again i don't get it. I'm running Ubuntu 8.10 for Ppc (PS3) i get no internet connection what so ever just the same message. I go to add and remove and it wont let me load any programs because it needs to up date and being that there no internet i can't. what do i need to do to connect wireless with my PS3 using Ubuntu 8.10? Please explain in detail im new with Linux.

Vinnyd

---

### Post by Scunnered on 2010-02-12
**Vinnyd**

I have just noticed that you posted against my old posting.  I see you are using 8.10 on a PS3 so I don't feel too confident about offering guidance.  I am using 9.10 on a laptop where wireless connection works a treat.

One question I would ask is what are you doing when you attempt to start the wireless connection.  What I found was that when I was having difficulty if I used RESTART it very often would not access the connection.  What I had to do was after entering the name and password if it did not take the first time I would re-enter the information but then I would SHUT DOWN the system.  Normally after re-booting it would connect OK.

If this does not work my only suggestion would be to load 9.10 and see if things would work after that.

Sorry I can't be of more assistance

---

### Post by Vinnyd on 2010-02-21
Hi and thanks but the problem is now different..... i found out that its WPA that ubuntu wont connect to. I Switch the setting on my router to WEP and it connects wireless now. So no the question is how do i get Ubuntu to except my WPA connection. When i try the error message is " Wireless Network Authentication Required "  and it keeps saying that. anybody please i need help.

---

### Post by northd_tech on 2010-02-21
I'm not sure if this terminal command works in 8.10 or not (I'm using Jaunty 9.04), but this verified that my WPA/WEP/WPA2 stuff was current:

```
sudo apt-get install wireless-tools
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
wireless-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

You can read more about that here:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Vinnyd on 2010-03-22
Thanks but i tried and says im already updated.This really sucks i cant believe no one can help with this.im about to put Yellow Dog 6.2 i had enough.

---

