---
title: "Samba ubuntu and xp shares"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Ursidae on 2008-09-23
I'm having pretty much the same problem as everyone else who is trying to create a share between ubuntu and xp.
I was able to configure samba on my pc running ubuntu to the point where I can access it's shared directories from my laptop running xp.
Now I'm attempting to do the opposite. I want to access a shared folder on my xp machine from my pc running ubuntu. 
I've gone through this forum and went through quite a few of the how to's, but I am not having any luck.
I suspect my problem is a result of 3 things. My main problem is I'm new to linux/ubuntu. Other than that the first problem is I'm not sure I have the smb.conf file setup correctly. When I run smbtree all I see is //ubuntu which is the name of my pc running ubuntu. The other problem pertains to name resolution, or lack there of. I obviously have a dns issue. I figure if I can get everything working with ip addresses, I'll look into the dns problem after that.
One thing I find kind of weird is when I go into Nautilus and press ctl+l and enter smb://xpipaddress/share, I am prompted for my user name and password (My xp machine requires authentication). I enter my credentials and I am prompted again for my user name and password. This goes on until I cancel out. Not sure what the problem there is, but I was at least excited to see the authorization prompt. 
All my ip addresses are static. I am using a wireless router and I have ip address reservations setup for each computer.
At this point I'm not sure what I need to do. 
I've edited .smbcredentials and added my windows user information and then edited fstab and added what I think is the necessary information to create a permanent mount with cifs. When I run mount -a after that I get the error mount error 13 = Permission denied. I verified the firewall is off on the xp machine. I have Norton installed and I set my ubuntu pc as fully trusted there. I wonder if that's not enough though. I tried running mount -a when my xp machine was turned off and I received the message mount error 113 = No route to host. 
That leads me to believe that my ubuntu pc at least knows my xp machine is there but something on the xp machine or router is restricting it. Sadly I don't know much about wireless routers, but it doesn't look like there is anything there that would prevent access.
One thing I know for sure is I'm stuck.
Can anyone offer some suggestions as to where I can start trouble shooting? 
I think ubuntu kicks ascii.

---

### Post by Ursidae on 2008-09-25
Solved my problem. 
I wasn't sharing the folder in Windows correctly.

---

### Post by froghunter on 2008-10-04
I am posting on this, not because you still have a problem, but because this was a huge deal for me, well, mount error 13 from my linux box mounting XP shares. In my case I could access the shares fine from smb://xxx.xxx but couldn't mount. I tried all the hints online, such as making my username=WORKGROUP/USER and did the mount within fstab and also as a soft mount.

I am not a member on other forums and have no urge to join, but the problem definitely lies in sending the credentials. So, as root:
```
mount -t cifs -o username=User //xxx.xxx.xx.x/Share /mnt/Share
```
I am sure you could mount it where ever, just make sure you have the write credentials. I hope this helps and not sure why this works, but is easy to set as a script.

---

