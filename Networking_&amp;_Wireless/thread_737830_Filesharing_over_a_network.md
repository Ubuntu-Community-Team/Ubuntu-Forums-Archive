---
title: "Filesharing over a network?"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by pankirk on 2008-03-28
I made a file on my desktop and set it to "sharing" or whatever. So i go on my windows xp computer downstaris and i find my computer its called patrickroom(sambba, network) or something along the lines of that. So then I click on it and it asks for a username and a password. So I enter my username and password i use to login to ubuntu when I turn the pc on, but it doesnt connect it just refreshes and adds whatever i typed after a slash and it says my name and what not. I just want to know, how can I set up a folder on my ubuntu computer and have it shared across my netowrk. and i just want to know, when it asks for a password on windows, what is that username and password for it?

---

### Post by process91 on 2008-03-28
The problem is that samba users are not the same as Ubuntu users. If you've just set up samba, chances are you don't have any samba users enabled. You'll need to add a samba user. 

You should check out this post about [Samba Sharing between Ubuntu and Windows.]("http://ubuntuforums.org/showthread.php?t=202605")


The basic code is

```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

---

