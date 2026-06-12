---
title: "\\&quot;machine&quot; is not accessible"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by dureal99d on 2015-05-02
Hello!!

I have a ubuntu 15.04 machine. at first i was able to access the machine from a windows machine and see the shares on my buntu box but not access them, now I am not able to access my buntu box at all from a windows machine, nor a mac.

I did do the smbpassword -a blah blah blah command and enter a new user, but even that has not enabled me to access the machine.

I did do the config file.

Workgroup = Workgroup
netbios name = yady yah

so my machine is viewable to windows, mac and linux machines on my network & i can access any of their shares with  no issues from my buntu box, but i just cannot figure out how to make my machine accessible again so I can control shares.

any help would be appreciated. Thanks!!!!!!

---

### Post by dureal99d on 2015-05-05
After researching myself with no help which is amazing to me.

Anyway I found out what I did wrong, i used the sudo smbpasswd -a command
issue is when I typed in the password I typed in a password that did conform to the local samba password sync (local use account) and as a result, no one could logon who was attempting to from a outside machine.

i typed in the same use name and password I used to logon to my buntu box and walla now i can access my machine from windows machines and the like but now i must create a secure logon

---

### Post by dureal99d on 2015-05-05
Ok so im back where I began, lol

I guess that's what I get for speaking to soon, but it did work for a little while then all of a sudden out like a light.

---

### Post by dureal99d on 2015-05-06
ok so now I can again after some more configuration changes

---

