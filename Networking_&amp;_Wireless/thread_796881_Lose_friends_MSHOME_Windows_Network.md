---
title: "Lose friends MSHOME Windows Network"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by eAi-T0ky0 on 2008-05-16
i have lose my friend windows network called "MSHOME" it was worked and it's gone i don't know how?? it just was there and gone

when i go to the network>>> Windows Network >>> I Just Find network called "WORKGROUP" and "MSHOME" Not There

How can i get MSHOME Network back again please??????


and when try to share my folder after MSHOME Gone it give me error : 


i don't know why i can't share my folders and why i have lose Mshome network please i want to get it back??????



PLEASE HELP :confused: :( :( :( :(

---

### Post by mfaust731 on 2008-05-16
just change the workgroup name from workgroup to mshome

---

### Post by eAi-T0ky0 on 2008-05-16
Sorry, couldn't rename "WORKGROUP" to "MSHOME": Operation not supported by backend :(:(:(

---

### Post by mfaust731 on 2008-05-16
what version is this, 8.04?
what else is on the network?

---

### Post by eAi-T0ky0 on 2008-05-16
yes it's 8.4 


There on network

EAI-ONLYONE << I Think that my name on networked

ANd

Windows Network

And when i go on the windows network i losed my friend network "MSHOME" and it was there just "Workgroub"!!

---

### Post by mfaust731 on 2008-05-16
well, what your talking about is the workgroup name of the windows network.
It has nothing to do with your ubuntu 8.04 machine, the workgroup name that is set on the windows machine your trying to look at has changed from "MSHOME" to "WORKGOUP" in the network setting on your XP machine...
You can not change that from ubuntu.......at all.....

---

### Post by eAi-T0ky0 on 2008-05-16
i think that no one change "MSHOME" Network on XP Machins .. i think i change it from my ubuntu bec it was work with me well ... and i have try to share my files and do some commands to try share it but i don't... and when i opened network to see my friends pc's i lose MSHOME!!!


i think i do that from my ubuntu ... remove MSHOME and do WORKGROUP!!!!! :(


How can i install MSHOME again????

---

### Post by mfaust731 on 2008-05-16
the only way that could have happened is if you were shareing a folder on your ubuntu box with samba, and you changed the workgroup of that share.
are you using samba

---

### Post by fmartinez on 2008-05-16
> **eAi-T0ky0 said:**
> i think that no one change "MSHOME" Network on XP Machins .. i think i change it from my ubuntu bec it was work with me well ... and i have try to share my files and do some commands to try share it but i don't... and when i opened network to see my friends pc's i lose MSHOME!!!


i think i do that from my ubuntu ... remove MSHOME and do WORKGROUP!!!!! :(


How can i install MSHOME again????

You don't install "MSHOME". MSHOME is just the name of the network your trying to connect to. If your trying to share files between windows and ubuntu try install samba. This will make a lot easier. 
in ubuntu go to system and choose the "connect to server" option and type the ip address and the folder your trying to connect to.

---

### Post by eAi-T0ky0 on 2008-05-16
hey i have fix it by resstart my pc and i find MSHOME Back Again :)


and YES my dear i think i use samba!!!


But There Was Problem "when i put right click to that folder i want to share and proparties and share and great share it give me error dude"

```
'net usershare' returned error 255: net usershare add: cannot share path /media/disk-2/Film's/1408[2007]DvDrip[Eng]-aXXo as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.
```

can u help me with this??

---

### Post by mfaust731 on 2008-05-16
type sudo before all that:

sudo net usershare

---

### Post by eAi-T0ky0 on 2008-05-16
i think Samba is already installed i found it on my FileSystem /usr/share And Samba


But When try to share folder it give me error!!!!! :(:(:(

---

### Post by eAi-T0ky0 on 2008-05-16
sorry but i'm new i don't know what i have do!!!

i go to my terminal and put

sudo net usershare


it give me alot of things i don't know what i have do :(

can u tell me by steps what i have to do :( please 

i'm so sorry i'm new and don't know what that :(:(

---

### Post by mfaust731 on 2008-05-16
explain to us what you are trying to do.

share a folder on your ubuntu box, or access a shared folder from your friends xp machine?

---

### Post by eAi-T0ky0 on 2008-05-16
i want to share folder in my ubuntu pc to my friend's windows that they can see it in that local network MSHOME :(

---

### Post by eAi-T0ky0 on 2008-05-16
the local network "MSHOME" is back and i can see them pc's and go to they folders ... but i can't share my folders to them :(

---

### Post by mfaust731 on 2008-05-16
[http://www.google.com/url?sa=t&ct=res&cd=9&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAd17kma8rNM&ei=XCsuSOqsIpHogAT2vZUP&usg=AFQjCNEm-H3newtik5A2NGgCtJfagpmS2A&sig2=Dn3C6yA4nqxuwNXbBGQbjg](http://www.google.com/url?sa=t&ct=res&cd=9&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAd17kma8rNM&ei=XCsuSOqsIpHogAT2vZUP&usg=AFQjCNEm-H3newtik5A2NGgCtJfagpmS2A&sig2=Dn3C6yA4nqxuwNXbBGQbjg)

---

### Post by eAi-T0ky0 on 2008-05-16
Thanks Alot

---

### Post by eAi-T0ky0 on 2008-05-16
Thanks Alot 

it write with Ubuntu!! i think want sharing with windows!!

---

### Post by eAi-T0ky0 on 2008-05-16
can't find Shared Folders 

where i can get it??


it's not in System >>> Administration >>> .........


I Use ubuntu 8.4

---

