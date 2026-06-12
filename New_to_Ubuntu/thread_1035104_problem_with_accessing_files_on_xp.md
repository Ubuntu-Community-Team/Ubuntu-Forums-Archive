---
title: "problem with accessing files on xp"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-01-09
Hi Ubuntu Community:

I am having difficulty accessing files on an xp machine from my ubuntu machine. Both of these machines are on my home network behind my router.

On my xp machine, I have turned the firewall off, created a folder on c: with that allow it to be shared.

On my ubuntu machine, when I do Places > network > windows network and then click on the WORKGROUP icon, nothing happens. I do not get access to the xp machine.

Can anyone suggest a solution to this problem?

I want to move files to and from that shared xp folder from ubuntu.

Thank you!
Phil Smith
Duluth, GA

---

### Post by Stefanie on 2009-01-09
can you ping the xp machine?

---

### Post by Michael.Godawski on 2009-01-09
Hi,

did you have a look at Samba?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by Oak37 on 2009-01-09
There is another excellent how-to for Samba [here]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by Old Jimma on 2009-01-09
Hi Sefanie:

Yes, I can ping it: 192.168.1.101 responds.

Phil

---

### Post by superprash2003 on 2009-01-09
try this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Stefanie on 2009-01-12
> **Phil Smith said:**
> Hi Sefanie:

Yes, I can ping it: 192.168.1.101 responds.

Phil

i used samba for a while when i was still sharing files between computers, and i remember i had a similar problem. i think i sorted it out eventually by trying another file manager (konqueror worked better than nautilus for instance). and using the internal ip instead of the computer's name. it may also help if you enter the complete network address of the folder directly into the address balk.

i had these issues when i was still on gutsy, so it is possible that your problem is different...

---

### Post by Old Jimma on 2009-01-17
Hi Ubuntu community:

Stefanie is correct. When I installed konqueror, I was able to browse directories on the Windows machine with no problem at all.

Thank you Stefanie!

Best regards,
Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2009-01-17
Hi Ubuntu Community:

To access shares on a Windows machine:

1. Intall samba: [https://help.ubuntu.com/community/Samba]("https://help.ubuntu.com/community/Samba")

2. from Nautilus: smb://192.168.1.101/ (if 192.168.1.101 is the ip address of the Windows machine on your network).

3. from Konqueror: smb:/192.168.1.101  (if 192.168.1.101 is the ip address of the Windows machine on your network).

I don't know why Nautilus requires the double forward slash and why Konqueror requires only a single forward slash. :confused:

I hope this helps someone!

Phil Smith
Duluth, GA

---

