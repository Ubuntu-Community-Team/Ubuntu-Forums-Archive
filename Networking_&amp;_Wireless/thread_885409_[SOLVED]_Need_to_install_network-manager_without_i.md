---
title: "[SOLVED] Need to install network-manager without internet connection"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by Sp4cedOut on 2008-08-10
I put the installation cd in, added it as a repository with: "sudo apt-cdrom add" and tried "sudo apt-get install network-manager" and it said it has no installation candidates.  apt-cache search didn't turn up anything either.

The same thing happened with ndiswrapper, which is a program I've already installed from the CD, so I guess I messed up the repos cache somehow.  I tried apt-get update, but it didn't change anything.

Any help appreciated.

---

### Post by cdtech on 2008-08-10
I'm looking.

---

### Post by cdtech on 2008-08-10
did you uncomment the cdrom within your /etc/apt/sources.list

---

### Post by cariboo on 2008-08-10
Network-manager is installed by default, you shouldn't have to install it. If you need to reinstall it because you think you messed up, that won't help. If you post your problem here, there probably is a way we can help you solve it. Remember Linux is not Windows, just because something doesn't work the way you expect to reinstalling won't fix it.

Jim

---

### Post by Sp4cedOut on 2008-08-10
cdtech: Thanks for the suggestion, I tried uncommenting the cdrom, it didn't fix it.

cariboo907: I'm aware network-manager is installed by default, that's why I'm trying to get it off the CD.  I uninstalled it however when I installed WICD.  WICD is hanging when it tries to obtain an IP address, several google searches found other people with a similar problem on several forums with no one posting a solution.  Instead of trying to fix it, I'd rather just go back to network-manager which was working just fine for me.  Frankly, I asked a very strait forward question, so if you know the answer to it, I'd appreciate it if you tell me.

EDIT: Never mind.  I forgot I could just connect on the command line and reinstall network-manager the normal way.

---

### Post by praveenpious on 2008-08-13
I am facing the same situation now. I want to reinstall network-manager. Please help me do the same..

---

### Post by superuser84 on 2008-08-16
Hi .

I tried "sudo apt-cdrom add" and tried "sudo apt-get install network-manager", but it was stil looking for [http://ch.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://ch.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/) and not in CDROM. So I downloaded network-manager on my other pc, transfered to ubuntu machine and did a dpkg --install network-manager*.deb and it said network-manager is successfully installed.

Now how can I get internet connection from  I used to get a bar on the panel showing internet connection. Pls advice on how to proceed.

Thanks.

---

### Post by Whizam on 2009-01-18
I encountered the same problem as Sp4cedOut.

In order to fix this, I ran the following command:

```
sudo dpkg -i /var/cache/apt/archives/network-manager_*.deb
```

After restarting Gnome it worked fine.

---

