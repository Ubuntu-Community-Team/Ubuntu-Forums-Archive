---
title: "uShare and Xbox 360. What's the deal?"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by carltonincognito on 2011-02-17
So I'm posting in this forum because I want someone to walk me through this. I am, by no means, an amateur at this, but I can't for the life of me get sharing to work properly. 
I have 10.04 installed on my computer. I have uShare configured to share with my 360. Everything looks like it should work, right?
I turn on my 360, go to the music blade, and it sees my Ubuntu box. AWESOME!
I go to artists and it says no artists found.
Dammit.
So, after searching the forums for hours, reconfiguring ushare a number of times, and building up an unhealthy amount of frustration, I ragequit. 
I am now at work, and still trying to figure this out. 
Any ideas?

---

### Post by Keiran230 on 2011-02-18
This is just a wild guess, but since the Xbox was made by Microsoft, it's probably trying to use the SMB protocol to transfer the music files. Linux uses NFS to transfer files across the network, but will use SMB if you install and configure a program called Samba.

---

