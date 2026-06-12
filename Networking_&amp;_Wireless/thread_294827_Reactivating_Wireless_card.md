---
title: "Reactivating Wireless card"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by Belisarius on 2006-11-07
Hi,

I'm using Breezy (it's working fine so why change:) ) on my laptop. However, at least once or twice a day the wireless goes down (Intel 2200 onboard). It just loses the signal. I don't know if this is happening at the PC end or the router end. 

Now, all it takes is to open a console and do 

sudo ifdown eth1
sudo ifup eth1

and all is fine again.

Problem is I need to enter my password for the first sudo. is there any easy way I can set this as a script so I can just click an icon on the desktop and it will execute the above 2 commands without promting for a password and reset my link a bit quicker?

I tried creating file with the commands in, making it executable, and then setting suid (chomod +s) however it still prompts me for a password.

Any suggestions please?

Cheers

Andy

---

### Post by girishv on 2006-11-07
Edit the file /etc/sudoers and add the following lines

user_name ALL = NOPASSWD: /sbin/ifdown, /sbin/ifup

user_name is your user name (or to whom you want to give the permission

Editing sudoers is risky. So always use visudo, 

sudo visudo


Girish

---

### Post by Belisarius on 2006-11-07
Hi Girish,

that seemed to work although the script still kept prompting me for a password when I ran from the desktop link. Ended up putting the script in /usr/local/bin and adding it to the line you showed above and it seems to work now. Can you see any problems with that, security wise?

Thanks for the help

Andy

---

