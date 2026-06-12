---
title: "Need help, moving files to laptop"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by NET WT on 2008-04-23
Hi,

I want to move some files from my desktop computer to my laptop. My desktop is running Ubuntu 7.10 and my laptop has Xubuntu 7.10 on it. I have a wireless network and have already tried to share the folder through System>Administration>Shared Folders. I do not know how to get it working though. I have been using Xubuntu for only a couple of days, and I am not very familiar with it. I also don't know much about networking, and I need some help. In a short while I plan on doing a fresh install of Ubuntu 8.04 on my desktop. I want to move my videos to the laptop, then back again after I finish the install. What is the best way to do this? And how do I do it? 

Thanks

---

### Post by Monicker on 2008-04-23
> **NET WT said:**
> Hi,

I want to move some files from my desktop computer to my laptop. My desktop is running Ubuntu 7.10 and my laptop has Xubuntu 7.10 on it. I have a wireless network and have already tried to share the folder through System>Administration>Shared Folders. I do not know how to get it working though. I have been using Xubuntu for only a couple of days, and I am not very familiar with it. I also don't know much about networking, and I need some help. In a short while I plan on doing a fresh install of Ubuntu 8.04 on my desktop. I want to move my videos to the laptop, then back again after I finish the install. What is the best way to do this? And how do I do it? 

Thanks

Well, I would do it this way. Install the openssh-server package on the laptop: sudo apt-get install openssh-server.  

The service should get started automatically after the install.  

If not, then do: sudo /etc/init.d/ssh start.

At the desktop, tarball the files to be transferred.

tar -czvf /tmp/myfiles.tar.gz /some/dir


Then use scp to copy them to the laptop:

scp /tmp/myfiles.tar.gz username@192.168.1.1:/home/username

You will get a prompt to accept the key, say yes. Then enter the password for the account on the laptop.


Of course, change the ip to match the actual ip address of the laptop, and the username to your account on the laptop.

---

### Post by NET WT on 2008-04-25
I got it to work, thanks for the reply.

---

