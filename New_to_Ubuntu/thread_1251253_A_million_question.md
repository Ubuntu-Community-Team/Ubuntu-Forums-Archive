---
title: "A million question"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by KarKess on 2009-08-27
First let me say "Hi" I am new to these boards, and new to Linux. I have a lot of questions but I'll start with a couple. 
 
1. Can I dual boot with Vista 64 without problems?
 
2. Does this version of Linux support RedHat drivers?
I ask this question because I am in the process of obtaining my CCNA and have bought Cisco gear and have no way of accessing because it uses serial port to communicate.
I bought a pcmcia card that has a serial port, but it does not support Vista 64, and I have not been able to find anything that does. But the card I bought does support Linux and the drivers are for Redhat 8, 9, & 73. Not that I have a clue what that means.
 
If anyone has any suggestions that would be great!
 
Thanks

---

### Post by fela on 2009-08-27
You can _definitely_ dual boot with vista without a problem, if you do it correctly (there are countless guides on google).

As for the redhat drivers - they're probably in rpm format. If they are you can convert them to deb (ubuntu/debian packages) with software called alien - don't ask me how as I've never done it before. Again, google is your friend. I'd be very doubtful that they're only compatible with red hat linux (which is a distribution like ubuntu is, in case you don't know).

---

### Post by KarKess on 2009-08-27
Thanks for the quick reply.

---

### Post by Simian Man on 2009-08-27
> **KarKess said:**
> 2. Does this version of Linux support RedHat drivers?
I ask this question because I am in the process of obtaining my CCNA and have bought Cisco gear and have no way of accessing because it uses serial port to communicate.
I bought a pcmcia card that has a serial port, but it does not support Vista 64, and I have not been able to find anything that does. But the card I bought does support Linux and the drivers are for Redhat 8, 9, & 73. Not that I have a clue what that means.

Those are very old versions of Red Hat (dating back to 2003 or so).  Those drivers will likely be supported under most versions of Linux these days.  If they don't work under Ubuntu, you can try Fedora which is the successor to Red Hat Linux.  Most likely you should be able to get it working under any version though.

---

### Post by Mark Phelps on 2009-08-27
> **KarKess said:**
> First let me say "Hi" I am new to these boards, and new to Linux. I have a lot of questions but I'll start with a couple. 
 
1. Can I dual boot with Vista 64 without problems?
Yes, but be sure to use the Vista Disk Management utility to shrink the Vista OS; don't rely on the Ubuntu installer to do that.

> 2. Does this version of Linux support RedHat drivers?

While you CAN use alien to convert .rpm files to .deb files, from personal experience, I have found that does not always work.  I found situations where libary package names were different between the two and while the .deb got built OK, installing it failed due to inability to find wrongly-named dependencies.

You would do better looking for the .deb packages and installing them.  They will have the correct dependency names.

---

### Post by scratman on 2009-08-27
This may be a touch reckless, but you could always just try plugging it in and see if it works.  I've been pleasantly surprised by Ubuntu in the past, supporting immediately things that would have taken hours to get working in Windows.

---

