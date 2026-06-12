---
title: "Help needed in installing software"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by net fun on 2011-07-29
I'm not a geek, so I need to install a dnrgarmin software on my laptop.  I need a step by step help please.   Anyone?

---

### Post by guilleme on 2011-07-29
Hi!
Have you tried installing with ubuntu software center?
The terminal code for installing stuff is: 
<code>
sudo apt-get install (the-program-you-want)
</code>
Then it will prompt you for your password. Note that when you write your password, you won't see the characters appearing in the screen. That is for security reasons.

---

### Post by net fun on 2011-07-29
thanks, I'll give it a try

---

### Post by net fun on 2011-07-29
G
this the reply I received:

 E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by net fun on 2011-07-29
I found the software that I want from here:[http://gps-software-hub.com/2008/06/download-dnr-garmin-application-to-transfer-data.html](http://gps-software-hub.com/2008/06/download-dnr-garmin-application-to-transfer-data.html)

I just need help to install on my laptop.

---

### Post by net fun on 2011-07-29
G 



I'm able to get this in the Downloads window, what do i need to do next?

---

### Post by Swagman on 2011-07-29
> **net fun said:**
> G
this the reply I received:

 E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

The reason you got that error message is because you tried installing using the terminal when you (probably) had Synaptic open at the same time

That's a No-No

Either one way or t'other !!

In regard to your downloaded file.. That' is a Zip file which (when unpacked) almost certainly will be a Windows exe

Your not using windows !!

If that file does turn out to be an exe then you will have to install WINE & Play on Linux to get it to run.

---

