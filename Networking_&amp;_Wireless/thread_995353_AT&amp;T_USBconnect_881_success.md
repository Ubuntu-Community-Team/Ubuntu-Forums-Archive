---
title: "AT&amp;T USBconnect 881 success"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2008-11-27
I finally got my Sierra USBconnect 881 device working with my AT&T account.  OS version = 8.04.  I started with the instructions on the Sierra Wireless web site and used the kppp route.  After following instructions, I had to adjust the parameters in the nm-applet 0.6.6 to get a working connection.

Someone who knows what he/she is doing needs to write a Howto.

John

---

### Post by cigtoxdoc on 2008-11-28
Best download speed I can get with Aircard under kpp and Ubuntu is about 20 kB/sec according to kppp statistics.  When same aircard is running off my Dell Vostro 2510 using AT&T software, which is right next to Ubunbtu PC, get download speeds around 200 kB/sec.  Is there a reason for the difference?

John

---

### Post by cigtoxdoc on 2008-11-28
Best download speed I can get with Aircard under kpp and Ubuntu is about 20 kB/sec according to kppp statistics.  When same aircard is running off my Dell Vostro 2510 using AT&T software, which is right next to Ubunbtu PC, get download speeds around 200 kB/sec.  Is there a reason for the difference?

John

---

### Post by cozmicharlie on 2008-12-01
> **cigtoxdoc said:**
> I finally got my Sierra USBconnect 881 device working with my AT&T account.  OS version = 8.04.  I started with the instructions on the Sierra Wireless web site and used the kppp route.  After following instructions, I had to adjust the parameters in the nm-applet 0.6.6 to get a working connection.

Someone who knows what he/she is doing needs to write a Howto.

John

It would be helpful if you added a link to the instructions, explain what you did and show the adjustments you made.  

thanks

---

### Post by cigtoxdoc on 2008-12-03
On getting aircard to work with 8.04, I followed instructions given on Sierra Wireless web site.  I have yet to get them to work with 8.10.

John

---

### Post by cozmicharlie on 2008-12-03
I was working with another member to get his broadband working.  It came down to a very simple fix.  Check this out - it may help you also.
[http://ubuntuforums.org/showthread.php?t=997941](http://ubuntuforums.org/showthread.php?t=997941)

---

### Post by cigtoxdoc on 2008-12-29
A slip of the hand and all of a sudden things started working when I put AT&T USBConnect881 device in a different port of a four-port PCI USB card.

I don't think I did anything other than use network manager although I had a devil of a time with something called keyring.

All is I know it is working.  Here at my FL home I am in a 3G area and updates are downloading at about 100kB/s.

It would be really nice if one of the forum gurus would explain what I did right.

John

---

### Post by cozmicharlie on 2008-12-29
Not exactly sure why the other port worked.  For some reason it was not picking up your device on the other port.  

Glad to hear you got it working.

---

### Post by cigtoxdoc on 2009-01-01
After being able to get a working connection with the AT&T USBconnect881 wireless device on all four ports on my (Belkin?) USB 2.0 PCI card, I am beginning to think I overlooked the apparently simple setup.

This is with 8.10 which apparently has the latest Sierra Wireless drivers.  So, all one needs to do is go to NetworkManager Applet 0.7.0, and go to the Mobile Broadband tab.  Under the "Basic" section, enter *99***1# for number, enter [email]ISP@CINGULAR.GPRS.COM[/email] for username, and enter CINGULAR1 for password.

The above was done on a fresh install of 8.10 on a newly formatted hard drive.  I did not have kppp installed at the time the device started working correctly.  I did have to set up a generic(?)  keyring password, however.

I hope I will get some feedback on this post.

I also want to thank all those who helped me find the correct answer.

John

---

### Post by cozmicharlie on 2009-01-03
> **cigtoxdoc said:**
> After being able to get a working connection with the AT&T USBconnect881 wireless device on all four ports on my (Belkin?) USB 2.0 PCI card, I am beginning to think I overlooked the apparently simple setup.

This is with 8.10 which apparently has the latest Sierra Wireless drivers.  So, all one needs to do is go to NetworkManager Applet 0.7.0, and go to the Mobile Broadband tab.  Under the "Basic" section, enter *99***1# for number, enter [email]ISP@CINGULAR.GPRS.COM[/email] for username, and enter CINGULAR1 for password.

The above was done on a fresh install of 8.10 on a newly formatted hard drive.  I did not have kppp installed at the time the device started working correctly.  I did have to set up a generic(?)  keyring password, however.

I hope I will get some feedback on this post.

I also want to thank all those who helped me find the correct answer.

John

The new version of Network Manager (now in 8:10) has really simplified broadband.  Most should be supported without having to go through lots of configuring.  This was the last thing I needed working to get completely rid of Windows.

---

### Post by olyander562 on 2009-09-23
> **cigtoxdoc said:**
> After being able to get a working connection with the AT&T USBconnect881 wireless device on all four ports on my (Belkin?) USB 2.0 PCI card, I am beginning to think I overlooked the apparently simple setup.

This is with 8.10 which apparently has the latest Sierra Wireless drivers.  So, all one needs to do is go to NetworkManager Applet 0.7.0, and go to the Mobile Broadband tab.  Under the "Basic" section, enter *99***1# for number, enter [email]ISP@CINGULAR.GPRS.COM[/email] for username, and enter CINGULAR1 for password.

The above was done on a fresh install of 8.10 on a newly formatted hard drive.  I did not have kppp installed at the time the device started working correctly.  I did have to set up a generic(?)  keyring password, however.

I hope I will get some feedback on this post.

I also want to thank all those who helped me find the correct answer.

John
Hello. I'm a little confused. And forgive me for asking, but are you saying you connected with the credentials below without paying for an account? Was this used at a wireless hotspot? Or was this simply a test to see if you received signals that displayed? 

Curiously, Olyander

---

