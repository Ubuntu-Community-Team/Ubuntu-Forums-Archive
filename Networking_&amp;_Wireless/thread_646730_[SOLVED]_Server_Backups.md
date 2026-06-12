---
title: "[SOLVED] Server Backups?"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by Rich930 on 2007-12-21
Hey guys.

My server has been running for ages now (on 7.4) and im just about to make it central in our house.
(so that everyone can access it  =] )

Is there a small script i can write to tell it to backup certain files onto a cd every few days? Ive heard of Zenity, but i was told it needs a gui to run?

Please could someone tell me of what i can use to run scripts on the server? And an example of one or some syntax would be really appreciated. 

Thanks!!

---

### Post by kidders on 2007-12-22
Hi there,

You could try something with **tar**, **mkisofs** (aka genisoimage) and **cdrecord**. The syntax for these commands is in their man pages. Once you're sure whatever you make works, you could add it to root's crontab.

You'd have one or two small issues to cover, such as what you'd like to have happen if there isn't a CD in your drive at the right moment. By experimentation, **head -c0 /dev/cdrom** seems like a reasonable, basic test for the presence of a disc.

---

### Post by Rich930 on 2007-12-24
thanks. umm i just come across a problem.. :s

I hooked my server up to my router (WLAN)
it was running on a wired LAN between just a couple of machines.

Now im trying to get it accessible by every machine in my house wirelessly.
I ran ifconfig and it comes up with 192.168.0.3, but when i typed it into any of my other machines it doesnt find it? :S

please help.

---

### Post by kidders on 2007-12-24
It'd probably be best to start another thread, but in the meantime...

Depending on what you mean by "find", you may need to configure whatever service you're trying to access to bind to your wireless network interface. Most servers allow you to enumerate the network interfaces they listen on, so you don't wind up having to do crazy things like running a firewall, just to prevent a private web server exposing itself to the internet.

There are lots and lots of other possibilities though. :-(

---

