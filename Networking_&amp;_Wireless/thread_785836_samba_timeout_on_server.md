---
title: "samba timeout on server"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by veganrailpunk on 2008-05-07
Hi

I'm trying to copy files from my desktop to laptop. They both run kubuntu 7.10. They use a BT Home Hub router with the laptop using wireless and the desktop using a cable. I set up samba yesterday and shared the folders I want to copy from my desktop. I could access the files but was tired so went to bed. 

When I came back to it today to copy the files I keep getting a "timeout on server" message at the bottom of Dolphin... Does the same with konqueror.

Can anyone help?? It worked fine and now it doesn't :(

---

### Post by Footer on 2008-05-08
I wish I could say I know the answer to your problem but I don't.  :(

In fact, I'm using Kubuntu 8.04 but even before I upgraded, I started experiencing this problem.  It's kind of been hit-or-miss in my situation.  I have XP machines on my network and they see the workgroup computers just fine (even the Linux boxes).  But I'm getting 'timeout on server' from an 8.04 machine as well as a Kubuntu Dapper Drake machine.

Any insight or suggestions would be GREATLY appreciated.

Thanks!

---

### Post by rally4life on 2008-05-09
I am having this same problem. However, if I connect using the internal IP then it connects fine. So, instead of smb://workgroup, I used smb://192.168.0.***

---

### Post by veganrailpunk on 2008-05-10
fantastic! worked like a charm :-)

thank you very very much!

---

### Post by Footer on 2008-05-10
> **rally4life said:**
> I am having this same problem. However, if I connect using the internal IP then it connects fine. So, instead of smb://workgroup, I used smb://192.168.0.***

Yeah, using an IP connects up just fine.  But you should be able to use WORKGROUP (or whatever you have it called in smb.conf) and the name of your machine rather than IP.  This USED to work!  So I don't know if something has changed in Samba or if it's a bug or what.

But it BUGS me!  It's working for me at the moment (see attached) but as mentioned earlier, it's hit-or-miss and could cause a 'timeout on server' error at any moment.

:(

---

### Post by Doominite on 2009-06-03
I got a similar problem and since most of my searches showed this thread I'll add my reply.

**Problem:**
I installed Kubuntu 9.04 about a two weeks ago.  It seems to have samba integrated?  I click Network in the places tab in dolphin and click Samba Shares and it shows Workgroup.  I click that and it shows my other computers and I can connect to them just fine.  This worked fine until a few days ago.  When I clicked Workgroup, it would hang for half a minute and then say "Timeout on server Workgroup".

**Troubleshooting:**
The only things I remembered changing was removing Network Manager in favor of using a static IP, and replacing ufw with Firestarter.  I added SMB protocols and IPs from my other PCs to Firestarter and even with it turnned off, it still didn't fix the problem so it was the network configuration?  I could connect to my other computers through samba by typing the IPs in as previously mentioned.  I booted up from my Kubuntu CD and I could see my computers in Workgroup so I tried removing Network Manager and set up the interfaces file to match my current installation's settings.  I restarted networking and samba still worked but the internet didn't.:(  I forgot to add DNS entries in resolv.conf but once I did, samba didn't work.:mad:  I played around with it a bit, trying different DNS entries and sometimes it would work and other times it wouldn't.

**Fix that worked for me:**
I checked some files from the CD boot to see if they had any differences than my Kubuntu installation.  The "host:" line in /etc/nsswitch.conf was "files mdns4_minimal [NOTFOUND=return] dns mdns4" from the CD and just "files dns" on my install.  From the daemon log file, it showed avahi daemon use mdns after Network Manager was done setting up the card, so this could have fixed it. Or... there were several differences in my /etc/samba/smb.conf file.  

CD:
log file = /var/log/samba/log.%m
passwd program = /usr/bin/passwd %u

Install:   Going off memory here, these might have been a little different.
log file = file:///var/log/samba/log.%25%m
passwd program = file:///usr/bin/passwd%25%20u
restrict anonymous = no
domain master = no
logon home = %5C%5C%25N%5C%25U
smb passwd file = file:///etc/samba/smbpasswd
pid directory = file:///var/run/samba
logon path = %5C%5C%25N%5C%25U%5Cprofile
private dir = file:///etc/samba

In my samba log, there were a few errors from the log file and passwd program lines so I changed those two and rem'ed out the other seven.  After that there are no more errors in the samba log and it works perfectly.:D

---

### Post by dmizer on 2009-06-03
To fix this problem, please see the 6th link in my sig.

---

