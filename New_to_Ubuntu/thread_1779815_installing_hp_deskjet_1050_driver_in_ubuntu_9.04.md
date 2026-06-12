---
title: "installing hp deskjet 1050 driver in ubuntu 9.04"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Murali VenkataKrishnan on 2011-06-11
namaste,
                I am trying to install driver for my new hp deskjet 1050 printer in ubuntu 9.04.  It seems there is no further support for 9.04. I can't upgrade to 10.04 directly as there is 'no level jump permitted'. Pls help me with this.(Note: I dont use a dual boot. Ubuntu is the only OS I am using).

---

### Post by jtarin on 2011-06-11
Most HP printers are supported normally. Tell us what you have done to try and install and any error messages? What version of driver?

---

### Post by Murali VenkataKrishnan on 2011-06-11
When I connect the printer, it says 'driver not found'. In the event of searching it, i understood that 'hplip' needs to be the latest to have the latest printers listed in it. So downloaded 'hplip-3.11.5.run' and when I execute in terminal, the terminal gets closed automatically. when I use the synaptic package manager, I understood that '9.04 jaunty' is no more supported and I gotta upgrade to higher version. It seems, I cant jump to 10.04 directly. I dont find a way to upgrade to 9.10 and then to 10.04 now. Hope I am not confusing you...

---

### Post by jtarin on 2011-06-11
This seems like what you need. Something to get your teeth into.-[Manual Build and Install Instructions for Ubuntu]("http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html")
Check through the Menu on the left and understand before you proceed.

---

### Post by jtarin on 2011-06-11
It seems that 9.04 is not listed. :(

---

### Post by jtarin on 2011-06-11
[Here's a exercise in getting HP to run on Mint, which at the time the writer equates to 9.04]("http://liam-on-linux.livejournal.com/18419.html")

---

### Post by Murali VenkataKrishnan on 2011-06-11
So is there a way I can upgrade to 9.10 now ?

---

### Post by jtarin on 2011-06-11
> **Murali VenkataKrishnan said:**
> So is there a way I can upgrade to 9.10 now ?
I think you can only upgrade to a current/supported version? If you don't want to follow that link I gave and want to upgrade you should make another post on that subject.

---

### Post by Murali VenkataKrishnan on 2011-06-11
> **jtarin said:**
> I think you can only upgrade to a current/supported version? If you don't want to follow that link I gave and want to upgrade you should make another post on that subject.
I went through the link and when I want to install the components listed in the link using apt-get install , I am getting errors like this

Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-wadllib/python-wadllib_0.1~bzr7-0ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-wadllib/python-wadllib_0.1~bzr7-0ubuntu4_all.deb)  404 Not Found [IP: 91.189.92.169 80] 


so this should be because 9.04 is not supported. so you want me to open a new thread in order to go ahead with upgrading problem of mine ?

---

### Post by jtarin on 2011-06-11
> **Murali VenkataKrishnan said:**
> I went through the link and when I want to install the components listed in the link using apt-get install , I am getting errors like this

Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-wadllib/python-wadllib_0.1~bzr7-0ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-wadllib/python-wadllib_0.1~bzr7-0ubuntu4_all.deb)  404 Not Found [IP: 91.189.92.169 80] 


so this should be because 9.04 is not supported. so you want me to open a new thread in order to go ahead with upgrading problem of mine ?
[URL="http://launchpadlibrarian.net/23993266/python-wadllib_0.1%7Ebzr7-0ubuntu4_all.deb"]Here's your file.
[/URL] Sometimes it won't be on your server you have chosen. [Here's a place to search.]("https://launchpad.net/ubuntu") You may need to adjust your software sources server.

---

### Post by Murali VenkataKrishnan on 2011-06-11
Thanks a lot for your help. But still I am getting problem because during the installation of the 'hplip' , the terminal gets closed automatically and Iam clueless about the reason

---

### Post by jtarin on 2011-06-11
Try it one more time as per instructions only this time when the terminal closes reopen it and issue this command and post the output of the last 20 lines.```
cat /var/log/syslog
```

---

### Post by oldos2er on 2012-03-13
Closed, necromancy.

---

