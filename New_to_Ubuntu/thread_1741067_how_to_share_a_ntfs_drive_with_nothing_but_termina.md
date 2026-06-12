---
title: "how to share a ntfs drive with nothing but terminal"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by mrgreaper on 2011-04-27
ok i got my mates pc to ubuntu 64 bit
he then phoned me up to say that he cant access his external drive from any windows pcs 

so i used putty and this guide [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)

to set up samba omiting gedit for nano and creating a new user for samba

i then added the media folder to a share

[media]
 comment = media folder
 read only =no
 locking = no
 path = /media
 guest ok = yes 
 browseable = yes

my mate couldnt see the computer on the network so i got him to go to //192.168.0.5 in the address bar of a folder, he got a log in screen and signed in using the name and password i set up on the guide

he could see media folder
went inside and he could see both drives attached

world
The Drive

he cant access either and they show as empty folders if he mouse over them and if he tries to access he is told he does not have permission 

so i added this

[Drive]
 comment = the drive
 read only =no
 path = /media/The Drive/ 
 guest ok = yes
 browseable = yes 

and after he refreshed he tried to access it and it immediatly errored 

im now kinda stuck i have exhusted my knowledge of ubuntu, i did suggest he lug a monitier up to the computer but aparently with its placement and his back injury thats not an option 

im open to ideas people :) 

any help greatfully recieved 

oh in the mean time i installed mediatomb on there so he has partial and wierd access to his files lol


**please note im not just sat here waiting for a reply i am looking too... i did find two people also having problems sharing an external drive mounted in /media

one said "nvm its solved" 
the second said " tag as solved i figured it out"

ARGHHHHHH how ???? ...mumbles and wanders off ranting about people that dont take the time to say how they fixed it grrrr

---

### Post by mrgreaper on 2011-04-28
still cant figure it out

tried force user = username 
tried writable = yes
all no joy im officialy stumped

---

### Post by Azdour on 2011-04-28
Hi,

This may be incorrect, but its the underlying file system permission that is used before any Samba permission. So if you have a read-only directory on your file system, but in Samba you say its writeable, it's the file-system permission that will win each time. That is my wild stab in the dark :)

---

### Post by mrgreaper on 2011-04-28
this is wierd, i just got a phone call from my mate thanking me for getting it to work, i thought he was being sarcastic at first but no it suddenly started to work, the server pc hasnt been rebooted or anything..... well im not looking a gift horse in the mouth (wierd saying that, surely the trojan horse would of been less efective had the others looked that gift horse in the mouth?)

---

