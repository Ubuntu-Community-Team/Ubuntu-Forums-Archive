---
title: "Buffalo Linkstation s-l-o-w"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by dajashby on 2007-07-01
I have three PCs that run Ubuntu Feisty Fawn dual booted with a variety of Windows flavours.  I am currently making my umpty-third attempt in the last several years to make linux my desktop os of choice.  I have a Buffalo Linkstation plugged into my internet router to which I periodically make some large ClimatePrediction.net backups (anything from 300 MB to 1 GB in size.)  I have no problems doing this in Windows - the NAS box appears in Network Places and I can copy the files to it at a respectable speed.  The same thing occurs with two of my linux  boxes, but the third one, the one that I am using as my primary desktop, is horribly slow.  It can copy the same files to another linux box via samba in around 5 minutes, but suggests that the process will take anything from 30 minutes to over a day to the Linkstation.  The process is somewhat improved if I'm running Gnome, except that I get timeouts on particular files. (I prefer KDE).  I've tried setting up a permanent connections to the box via both smbfs and cifs, but the performance under those circumstances is worse.

I'm not really sure where to start looking for the solution.  The management software on the Linkstation doesn't offer any clues - each machine I copy to it from has its own directory, but none of them have any sort of username or password security.  I would suspect the Linkstation except that it works ok with other computers, but where should I start looking on the PC for which it doesn't work?

---

### Post by bclinton on 2007-11-13
Same thing here. The window goes grey and it sits there. Windows worked fine. I can reboot and its fine for a few seconds. It seems when I read a long directory or a lot of files it goes to no where land.

---

### Post by bclinton on 2007-11-14
Well after a few tries with different formats here is what worked for my problem. I found this in anoher post but I would be interested as to why the SMBFS mappings are real slow and get lost all the time. The ones below work like they should.



//192.168.5.3/Photos    /media/Photos        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/Music    /media/Music        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/Video    /media/Video        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

