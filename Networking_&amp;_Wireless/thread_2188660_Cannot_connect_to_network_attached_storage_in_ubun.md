---
title: "Cannot connect to network attached storage in ubuntu 12.04"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by yackmaster2 on 2013-11-18
Just did a clean install of 12.04 on my HP laptop. Now I cannot see and I assume cannot mount my GoFlex NAS.The NAS is connected directly to my router. I've downloaded Samba, smb client. but I cannot see the NAS. I even  unplugged the NAS so it would get a new IP but that did not help. I red thru some posts and installed Samba, Samba Client but still could not see the NAS. Fianly I downloaded SMB4K. With that I can see the NAS but cannot mount it. I'm not sure how I connected in the past or how I'm connecting now (ssh, sftp, smb, nfs, or something else). 

This should not have any effect on the issue but I did not like the Unity desktop so I downloaded the Gnome Classic desktop. I did try mounting the NAS via Unity but came to the same roadblocks

With my Dell laptop  running 11.04 I am still able to connect right out of the box, did not have to download/configure anything. I still have the Dell running and thought i could gain some insight to how it is connecting but I've come up dry. 

With 12.04 I  cannot see/mount the NAS. Nothing has changed in my network. My NAS is assigned it's IP by  the router and it is not static. Never has been and I have never had  connection issues in 11.04, even after power outages & ect issues  where the router reassigns IP's.

I don't know how 11.04 connected to the NAS. It just  did out of the box. With 11.04 it just connected (I could view,  add/save, delete files). I’m not sure why I can't connect to it running  12.04.



Thanks in advance.

---

### Post by yackmaster2 on 2013-11-19
Well after 96 views and no movement I kept digging and found a solution. Having found many threads that refrence this same issue I thought the solution would have come more quickly. But moving on... I found this solution at [http://askubuntu.com](http://askubuntu.com). 
The whole thread is here. There are several solutions so look thru and see if one works for you. 
[http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)

Before I tried any on these suggestions I comparied my installed Samba and SMB files on 12.04 to my working 11.04 install. maade sure they matched, rebooted my 12.04 and did the below steps. Rebooted my 12.04 and BINGO. Everything works as it should and as my 11.04 is working.

"I've had very good results in mixed network environments (Windows/Ubuntu) with this method:

  
[LIST=1]
[*]Press Alt+F2 and type: gksu gedit /etc/nsswitch.conf

[*]Look for this line:
  hosts:  files mdns4_minimal [NOTFOUND=return] dns mdns4

[*]Add wins so it looks like this:
  hosts:  files mdns4_minimal [NOTFOUND=return] wins dns mdns4

[*]Install the "winbind" package: sudo apt-get install winbind
  (Or via [Software Center]("https://en.wikipedia.org/wiki/Ubuntu_Software_Center") or [Synaptic]("https://help.ubuntu.com/community/SynapticHowto").)


[*]Reboot or restart your network." 






[/LIST]

---

