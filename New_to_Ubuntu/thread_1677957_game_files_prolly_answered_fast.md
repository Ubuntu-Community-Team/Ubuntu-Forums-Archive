---
title: "game files prolly answered fast"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by slixz85 on 2011-01-29
thanks for checkin this. i am trying to install some games onto a friends offline computer that cant get wifi or anything. she just plays games on it. so i have a ton of games installed on my system and just wanting to know where i can find the archived files downloaded from synaptic. so i can copy them to usb stick and put them on her ubuntu

thanks for any info and help

---

### Post by [Snc] on 2011-01-29
> **slixz85 said:**
> thanks for checkin this. i am trying to install some games onto a friends offline computer that cant get wifi or anything. she just plays games on it. so i have a ton of games installed on my system and just wanting to know where i can find the archived files downloaded from synaptic. so i can copy them to usb stick and put them on her ubuntu

thanks for any info and help

I found mine in 
```
/usr/share/games/..
```

Remember to create launchers for them too ;)

---

### Post by slixz85 on 2011-01-29
> **'[Snc] said:**
> I found mine in 
```
/usr/share/games/..
```

Remember to create launchers for them too ;)

i just looked at same location on my computer and i was hoping to find like one debian file for install. so if there is not such a simple way to get just one file, will the games work right by just copying the whole game folder and dropping into their games location... because for instance openarena is split up missions packs folder with .pk3 file names and base folder with the same .pk3 ones. 

thanks for quick response so far

---

### Post by Verbeck on 2011-01-29
they are in /var/cache/apt/archives
just copy over the files to the same location on the other computer and use synaptic/software center/apt-get to install what you want

---

### Post by Perfect Storm on 2011-01-29
Deb files are stored in /var/cache/apt/archives


EDIT: Verbeck beat me to it.

---

### Post by slixz85 on 2011-01-29
thanks to last two post thats great found the debians. you guys were in a race lol

---

### Post by slixz85 on 2011-01-29
thanks again anyone know a better tool than unetbootin actually for creating a persistent usb. to be able to save all documents and files when shutdown and there still on usb when boot up. for some reason regular unetbootin burns dont let it do this. when i save a text document for test to desktop then shutdown and reboot its not there

---

### Post by [Snc] on 2011-01-29
> **slixz85 said:**
> i just looked at same location on my computer and i was hoping to find like one debian file for install. so if there is not such a simple way to get just one file, will the games work right by just copying the whole game folder and dropping into their games location... because for instance openarena is split up missions packs folder with .pk3 file names and base folder with the same .pk3 ones. 

thanks for quick response so far

Well, maybe I was a bit too fast to post ... sorry!

I found the *actual* games in 
```
/usr/games/..
```
There are the binary files, you shoul be just okay, if you copy both 
```
/usr/games/..
/usr/share/games/..
```
Folder to the other computer

Anyway, as some games might run, some maybe wont ...

I'll try it out in a virtual machine and post back the results for "Secret Maryo Chronicles" (90Mb)

---

### Post by Perfect Storm on 2011-01-29
That is not entirely correct, [Snc]. Games are splitted into different directories (bin file, launcher, data, man,  log, etc.)

In this situation it's better to get the .deb package that solve the things for you.

---

### Post by slixz85 on 2011-01-29
> **'[Snc] said:**
> Well, maybe I was a bit too fast to post ... sorry!

I found the *actual* games in 
```
/usr/games/..
```
There are the binary files, you shoul be just okay, if you copy both 
```
/usr/games/..
/usr/share/games/..
```
Folder to the other computer

Anyway, as some games might run, some maybe wont ...

I'll try it out in a virtual machine and post back the results for "Secret Maryo Chronicles" (90Mb)



thanks for help and effort you aint gotta do that. i was directed to the debian files for one click install ^ so guessing it should work. dont see why it wouldnt

thanks again, let me know anyone if u know about making persistent usb. i tried finding another program but newer to linux and never sucessfull installing .tar and all others stick with debian.. so easy one click install

---

### Post by [Snc] on 2011-01-29
Slix: Well, the first thing where the symbolic links, etc ... its difficult, but i like to discover :)
AI: As i said, I like to discover, so I just tried ... and failed, and learned something new ;)

You can download games here
```
https://help.ubuntu.com/community/Games/
```

---

### Post by slixz85 on 2011-01-29
> **'[Snc] said:**
> Slix: Well, the first thing where the symbolic links, etc ... its difficult, but i like to discover :)
AI: As i said, I like to discover, so I just tried ... and failed, and learned something new ;)

You can download games here
```
https://help.ubuntu.com/community/Games/
```

yep thats why im here ha tryin to learn.

---

