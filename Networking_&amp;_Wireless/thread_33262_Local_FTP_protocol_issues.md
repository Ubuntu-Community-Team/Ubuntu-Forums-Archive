---
title: "Local FTP protocol issues"
date: 2005-05-10
forum: Networking &amp; Wireless
---

### Post by slundal on 2005-05-10
I have problem when downloading from a local ftp server. I get very slow speeds (7 - 9 kb/s). Whats even more confusing is that the upload is just fine, no slow speeds there. I don't belive that there is a problem with the server it self since it works just fine with my other computers. Also neither the router or cables are the problem as I have tested FTP transfer with other cabels and prots with the same computer and ended up with the same problem.

This cause for this is most likely some kind of limitaion set up on ftp downloading. I'm very new with Ubuntu and Linux so I don't know were to look.

OBS! This problem ONLY occurs with LOCAL ftp downloads transfers.

The computer in question is a Toshiba Tecra8100 with an Xircom PCMICI 10/100 mbit network card.

The server is a Blue and White PowerMac G3 400mhz running OS X Phanter 10.3.7

The FPT worked just fine with the previous version of Ubuntu.

---

### Post by sksbir on 2005-05-10
you should give more technical stuff in order to get some help : what is your FTP client ? can you put here the log of a download try ?

---

### Post by slundal on 2005-05-10
I use gFTP.

I don't know how to get the log form that application but i do know that the problem is not appliction specefic since when I try to "Connect to server" from Ubuntus own ftp protocol I get the same issue.

---

### Post by slundal on 2005-05-10
Here is the log btw:

USER G3

331 Password required for G3.
PASS xxxx
230-
    Welcome to Darwin!
230 User G3 logged in.
SYST

215 UNIX Type: L8 Version: tnftpd 20040810
TYPE I

200 Type set to I.
CWD /Volumes/Hurricane 75GB/DL_BT_mov:apps

250 CWD command successful.
Loading directory listing /Volumes/Hurricane 75GB/DL_BT_mov:apps from server (LC_TIME=sv_SE.UTF-8)
PORT 192,168,0,103,4,144

200 PORT command successful.
LIST -L

150 Opening BINARY mode data connection for '/bin/ls'.
226 Transfer complete.
PORT 192,168,0,103,4,145

200 PORT command successful.
RETR /Volumes/Hurricane 75GB/DL_BT_mov:apps/numb3rs.112.hdtv-lol.[BT].avi

150 Opening BINARY mode data connection for '/Volumes/Hurricane 75GB/DL_BT_mov:apps/numb3rs.112.hdtv-lol.[BT].avi' (366759936 bytes).
Redigera: Du måste ange en redigerare i dialogrutan med alternativ
Stoppar överföringen på värden 192.168.0.101
ABOR

Kopplar ner från platsen 192.168.0.101
Successfully changed mode of /home/slundal/Movies/numb3rs.112.hdtv-lol.[BT].avi to 644

---

### Post by slundal on 2005-05-11
Bump

---

### Post by slundal on 2005-05-13
Bump!

I'm never giving up!

---

### Post by sksbir on 2005-05-18
I don't understand this:```

Redigera: Du måste ange en redigerare i dialogrutan med alternativ
Stoppar överföringen på värden 192.168.0.101
ABOR
```

You should try to do the same with a command line ftp client...

---

