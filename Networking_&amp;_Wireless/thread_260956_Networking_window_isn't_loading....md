---
title: "Networking window isn't loading...?"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by Areken on 2006-09-19
I have a problem with my version of Ubuntu.  Well, technically I'm using Xubuntu, but from what I understand they should be almost identical.

Anywho I've tried opening the network window several times now.  It seems like it starts to load, but then just doesn't.  I've tried restarting my computer, and even letting it sit for a while, then turning it back on.  Nothing.  I have no other copies of any operating system installed.

As a side note, I'm not able to open up any of the system windows as well.  But the main thing I'm concerned about is getting my network window working so I can easily configure what I need to get my network running.

Also, earlier this morning I was able to use the window, as well as all the other system windows.  I'm pretty sure I didn't edit anything in between.

Any help would be appreciated.

---

### Post by Areken on 2006-09-19
I just realized that I'm apparently not admin anymore, as I'm going through the terminal now.  Is there any way to get admin rights back?

---

### Post by tbonius on 2006-09-19
Your questions are general.  The networking Window?  The Network Browser in Nautilus?  Admin rights?  Who are you loggin in as?  Can you sudo?  

T

---

### Post by Areken on 2006-09-19
My apologies.  When I say the networking window, I mean when I right click, then go System-->Networking.

As for logging in, I've logged in as myself, the only admin that I put on there.  There are no other users, just myself.

When I try to type in sudo in the terminal I get the following:

sudo: unable to lookup (none) via gethostbyname()

---

### Post by tbonius on 2006-09-19
The system cant resolv itself.  Try checking /etc/hostname and /etc/hosts to verify you have entries for the hostname in there.

T

---

### Post by Areken on 2006-09-19
hostname has nothing in it, and when I try to type something in and save, it says "Can't open file to write".


hosts has the following and I'm also unable to edit and save it:

127.0.0.1 localhost
127.0.1.1 Arekslaptop

# The following lines are desirable for IPv6 capable hosts 
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by tbonius on 2006-09-19
make sure you sue "sudo" when editing a file

Open /etc/hostname and put in the hostname you want the computer to be called.

T

---

### Post by Iowan on 2006-09-19
If your admin rights are actually gone, you may need to boot into the "rescue mode" to be able to edit anything.

---

### Post by Areken on 2006-09-21
Well, thank you for the advice, but I have more questions... >_<

How do I use the command 'sudo' to edit something through the terminal and/or through a normal text editor?

And also, how would I boot into 'rescue mode'?

---

