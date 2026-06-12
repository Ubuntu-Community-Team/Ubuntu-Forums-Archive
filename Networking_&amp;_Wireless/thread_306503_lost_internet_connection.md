---
title: "lost internet connection"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by SirJYK on 2006-11-25
I have had Ubuntu 6.1 installed about one month now.  I just recently booted into it and found that my I was not able to install some packages(download had failed).  I then tried to use firefox and the connection was dead.  I have not changed anything since using Ubuntu last and it was working properly then.  I can boot into Windows and the internet works fine.  How do I troubleshoot this?  I checked the DNS server info and that looked fine.  I am using a Linksys router.  Any help would be appreciated.

---

### Post by dbbolton on 2006-11-25
wireless or wired to the router ?

---

### Post by SirJYK on 2006-11-25
> **dbbolton said:**
> wireless or wired to the router ?

wired, it was working fine before and still works fine in windows.

---

### Post by SirJYK on 2006-11-25
anyone?

---

### Post by jimbean on 2006-11-25
i just a newbie so do this knowing that i am guessing
it helped me!!!

go into firefox
type in        
about:config 
in address field
in the filterline
type in
ipv6
there should only be one line
doubleclick on the line that says ipv6 
it should toggle that one line from false to true
x out of firefox {quit}
then restart firefox

---

### Post by SirJYK on 2006-11-25
no luck with that.  I think it is something more generalized, because it was working once and there are a couple of things that aren't working that use networking, internet via firefox and downloading of packages to install.  Also, I tried booting from the CD and the internet was not working.

---

### Post by SirJYK on 2006-11-25
anyone???

---

### Post by ardvark71 on 2006-11-25
Hi SirJYK...

Do you get any results using ping? This should tell you if you still have a connection and your system can communicate. 

Best regards...

:KS

---

### Post by DaveBorealis on 2006-11-25
> **ardvark71 said:**
> 
Do you get any results using ping? This should tell you if you still have a connection and your system can communicate. 


Trying a couple pings sounds like a good start to rule out possibilities:
```
ping -c1 google.com
```
Then:
```
ping -c1 64.233.167.99
```

If the first ping to google.com does not work, but the second one to google's IP does work, then it's likely a problem with DNS.

Best regards,
Dave

---

### Post by SirJYK on 2006-11-25
I tried it from network tools, not from the command line, with no luck.  I am a bit confused where to start looking and how.

---

### Post by ardvark71 on 2006-11-25
> **SirJYK said:**
> I tried it from network tools, not from the command line, with no luck.  I am a bit confused where to start looking and how.

Try it from the command line to verify, if you would. 

Regards...

:KS

---

### Post by 82_28 on 2006-11-25
Man, same thing happenin' here.  My wired ethernet connection has been working great and then I tried to implement a wireless router into the mix to share the connection around the house and voila, now I got nuthin'.  Wired or wireless, with or without the wireless router.  Again, everything works fine in Windoze.  I have a static IP address and all the settings are fine, but no network connectivity.  

Anybody?

---

### Post by 82_28 on 2006-11-26
Well, I tried what is recommended in the second post in this thread:

[http://ubuntuforums.org/showthread.php?t=306293](http://ubuntuforums.org/showthread.php?t=306293)

and it seemed to work.  Apparently you need to disable "ipv6".  But then again, I also "disappeared" all of my static ip settings, rebooted and then re-entered the values again.  But yeah, something in there worked.  Good luck!

---

### Post by SirJYK on 2006-11-26
I performed a hard reset on the router, let it stay powered down for 10 minutes and everything works now.  I have to re-enter all of my port forwarding data.  What a pain in the @ss that will be.  I am really disappointed in this router.  It is a Linksys wrk54g.  I think it has been giving me problems downloading via bittorrent as well.  Thanks for your help.

---

