---
title: "Home networking problems - help needed please"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by mthakur2006 on 2007-04-29
I really hope someone can help me out here.

Here is my situation:
I have three computers - 1 Fujitsu-Seimens Desktop (running XP Home), 1 Toshiba L30-101 Laptop (running Vista Home) and another Lenovo 3000 C100 0761D7A Laptop (running Fiesty). Before I had the Toshiba, I had an ad-hoc connection between Fujitsu and Ubuntu and that worked flawlessly, i.e. I could share files and printer very easily. Then one day, I bought the laptop and on the recommendation of the salesman at the PC superstore, bought a router (Linksys WRT54GS Wireless Router).

I setup the router, i.e. I could share internet, but not files or printers. I tried half-heartedly for a bit but then gave up. In the end, I could see Toshiba from my XP box but not the otherway. That was as good as it got.

Now, today on 29 Apr 2007, I was on ubuntuforums.org and I found someone who was having a similar problem and followed some instructions - e.g. installing samba and smbfs (can't believe I overlooked that!) on my ubuntu box. I could now see my Fujitsu box from my Ubuntu laptop and vice versa and share some files between them, to some extent, i.e. I could share files on my XP box that were being shared BEFORE I had the router, but if I wanted to share some more files NOW, i couldn't. XP says that sharing is enabled but I can't see it in Samba (may be a little refresh trick or something I am missing). 

As for printer sharing, if I print from ubuntu to the XP box, the printer makes the noise as if its is going to print something but doesn't. I have a HP Deskjet F380 All-in-one. The printer dialog in XP says that the file from ubuntu is 7.26 MB in size (it's just a test page btw) and that the ink is low. I tried installing new ink, still the same problem. I can print from XP allright.

The XP box can see my ubuntu Laptop but if I want to see what is being shared, it asks for a password (which I didn't set in the first place, although I have tried all the passwords and usernames I normally use, but no joy).

The XP box can also see my Vista laptop but when I see what is being shared on the Vista laptop, It says it can't open the destination directory. My Vista box sees nothing but itself (so selfish!)

So, my XP box can see everything but cannot open anything. My ubuntu laptop sees itself and XP and shares files and printers. My vista does nothing.

Can anyone help?
I apologize for the long post, but there was no way round it.

---

### Post by mthakur2006 on 2007-04-29
14 views, 0 replies.
anyone?
thanks

---

### Post by mike2357 on 2007-04-29
Could be several problems.

1.  On your Ubuntu system, did you set up samba logins/passwords?  The command is:
sudo smbpassword -a <username>
After you enter the administrator password It will then prompt for a password for the user account.  On your Windows machine, you enter this login/password when you want to connect.  Make sure the user is authorized in /etc/samba/smb.conf on the "valid users" line.  If you change the smb.conf file, you'll need to restart samba:
sudo /etc/init.d/samba restart

2.  Are you sure the samba programs are running?  Run the command:
ps -eaf | grep mbd
There should be at least one process with nmbd and at least one with smbd.  Apparently there were some changes in the samba program in Ubuntu 7.04, so an old smb.conf file might not work.

Good luck.  I've been there and it's frustrating.  It seems like the sun, the moon and the stars have to line up to get things to work.

---

### Post by mthakur2006 on 2007-04-29
cheers, mike!
u r a legend...that solved one problem and somehow the other problems got solved by themselves....as if controlled by stars!
thanks!!!!

EDIT: although smbpassword shoulb be smbpasswd ;)

---

