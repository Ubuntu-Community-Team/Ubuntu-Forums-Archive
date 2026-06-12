---
title: "RaLink RT2500 system freeze"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by rockrhino27 on 2006-12-29
Hello All, 

     I am trying to install a fresh copy of edgy on an Averatec 3260 laptop for a friend who wants to start learning linux.  I chose the alternate CD image, to install in text mode because that is more comfortable for me.  The install went fine, I did everything by the wired internet connection.  I got everything working and customized to my liking.  I then tried to activate the wireless card and the whole system froze.  I then reboot the system, when it came back to GDM it was still almost frozen.  There wan an extreme lag in anything I did.  I immediately went to a CLI tty and ran "ps auxw".  I saw that "events" pid number 5 was at 95%.  I then ran "top", then found that the same process was in the 90's% utilization over time.  

If anybody has experienced this before and may have a fix please let me know.  I am trying to deactivate the wireless adapter now, then i'll repost to this thread with an output of "lspci".  

Any help would be greatly appreciated.  

Thanks, 

Rich

---

### Post by jamesstansell on 2006-12-30
There is a bug that sounds similar:

[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34902](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34902)

It doesn't sound like you're having the hard lock-up though.

---

### Post by TheWizzard on 2006-12-30
how did you try to activate the card? did you follow the howto's on rt2500?

---

### Post by rockrhino27 on 2007-01-02
Thanks for the hint TheWizard.  I didn't find any HowTo's in my prior searches.  I saw your post and dug a bit deeper into the forums.  I found the following link in another thread:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29#head-afca59bb303accf7d6ee9144facd385f7c55fde3](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29#head-afca59bb303accf7d6ee9144facd385f7c55fde3)

I'm going to try what this suggests probably tomorrow.  If that don't work I was thinking of installing a beta release candidate of Feisty Fawn.  It may have better support for the RT2500 wireless NIC chipset.  

Thanks again for the help.  I'll update this thread with what happens.  

Rich

---

### Post by TheWizzard on 2007-01-04
> **rockrhino27 said:**
>  If that don't work I was thinking of installing a beta release candidate of Feisty Fawn.  It may have better support for the RT2500 wireless NIC chipset.  


if it doesn't work, you'd better try dapper. dapper is Long Term Support and very complete. edgy was a try-out release and feisy is still in early development.
newer is not always better!

---

### Post by rockrhino27 on 2007-01-04
Hey TheWizard, 

     Thanks again for your input.  I just got finished installing the latest driver for the rt2500 wireless card.  I got no love from the latest beta drivers.  I installed the latest beta drivers and also the latest rev of the utility.  Rutilt I think it is called.  When I tried to bring up the ra0 interface the whole system locked up again.  I went to a command line to see if the same process was at 99%.  I ran "top" and just as before the events process, pid #5, was at 99%.  ](*,)   I got a copy of dapper somewhere from when I originally installed it back in June.  I'll try that route in a few days when I have some more time.  

Thanks again for the input.  

Rich

---

