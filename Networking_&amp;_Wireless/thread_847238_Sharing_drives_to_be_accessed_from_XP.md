---
title: "Sharing drives to be accessed from XP ?"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by len1x on 2008-07-02
What's up,
I can see my XP shares just fine ( and access them ).. but now I have no clue how to share my drives on ubuntu so I can access them from my xp machine, any ideas?
I'm still new to all of the stuff, still learning..

Thanks :)

---

### Post by rbc on 2008-07-02
Pick a folder inside your home directory, or create a new one. Right click and choose Sharing Options. Tick off the Share this Folder option, then a window will come up, where you select Install Service. This will install Samba. You will need to have internet access for this. Also, watch this YouTube video for a step-by-step. It's for Ubuntu 6.10, but still appropriate

---

### Post by rbc on 2008-07-02
Once again, I forgot the link:
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by len1x on 2008-07-02
Thanks a lot, I managed to see the share on XP.. but when I try to access it, it asks for a username/password.. Any idea how can I disable the need for a user/password ? As the share will be read-only and only 1 person is on my lan.

Or maybe how to create a simple user/pass so I can give them to the guy that wants to access the share?

Thanks a lot

---

### Post by rbc on 2008-07-02
It's been a while since i watched that video but I'm pretty sure it's discussed towards the end. Anyway, you need to set up a samba account. Go to terminal and type:
sudo smbpasswd -a "username"

You'll be prompted for your sudo password, then it will ask you to type in a samba password. The next time you access the share from XP, type in that Username and password.Windows will cache the information, so you should only have to do it that first time

---

### Post by len1x on 2008-07-02
I suppose I can't add any username I want through "sudo smbpasswd -a username".. the username should already be created on my system? Although I don't know how to do it.

root@JUST-TRY:/home/lenix# smbpasswd -a server
New SMB password:
Retype new SMB password:
Failed to modify password entry for user server

**edit: Nevermind I fixed it, did adduser then added it to samba worked fine... Thanks for the help man :D**

---

### Post by rbc on 2008-07-02
System --> Administration --> Users and Groups, to add a user. Also, read this:
[http://huinck.net/samba_install.html](http://huinck.net/samba_install.html)

It discusses the error you mentioned

---

### Post by rbc on 2008-07-02
Wonderful. Happy to hear of the success

---

