---
title: "Thinkpad connection problems"
date: 2005-10-28
forum: Networking &amp; Wireless
---

### Post by rbrugman on 2005-10-28
Fellow Ubuntuers,
I am having trouble getting my IBM Thinkpad R51 to connect to the internet.  There are a couple of things I'm concerned about.  First off, the wireless works, or at least I think it works.  The ESSID is set to "any", and I know it connects at my house, but I haven't tried roaming anywhere with it yet.  I would also like the ability to have both my eth0 (wireless) and eth1 (wired) connections be activated on startup, just in case I am plugged in.  When I made eth1 auto, it hangs the startup until it eventually times out.  Is there way to change the timeout time, to say 10 seconds?

My other problem/concern is that for some reason, after I am in linux using wireless and I go back to Windows XP (my machine is dual booted), the wireless in XP is all screwed up and claims the wireless radio is off.  Is there some way linux is writing a config to memory somewhere turning off my wireless nic?


Thanks for any responses.  I'm in the process of trying to migrate my family from Windows to (K)ubuntu because the hate for viruses and spyware has finally taken over, and I will need some help along the way.

---

### Post by rbrugman on 2005-10-29
Alright, I have fixed the problem with the wireless radio being off.  It turns out that the wireless access point in the building where I work was broken, and I kept thinking it was my laptop.

I still would like to set the timeout during boot though.  If anyone has any information on that, please pass it along.

Robert

---

### Post by rbrugman on 2005-10-29
I think I'll rephrase what I'm asking.

I would like to have both my wired and wireless network interfaces load automaticly at startup, but since I am not always connected to both, I need them to be able to time out realitivly quickly so the system boots faster.  I would also like to have it automaticly pick the faster of the two connections (11Mb/sec vs. 100Mb/sec) if both wireless and wired connections are present, very similar to the way Mac OS X works.  If anyone has any idea, please let me know!

Robert

---

### Post by rbrugman on 2005-10-29
I've been looking through manpages, but I still haven't figured anything out.  I did come across a "hotplug" option in the interface manpage though which is of interest - can anyone tell me what this option is?

Thanks!
Robert

---

### Post by Tim___ on 2005-10-31
Install network-manager. 

Make sure the "nm-applet" is in you're session startup.

---

### Post by rbrugman on 2005-10-31
Tim,
Thank you for the reply.  Network manager is EXACTLY what I was looking for, and getting it working couldn't have been any easier.

Thanks!!!

Robert

---

