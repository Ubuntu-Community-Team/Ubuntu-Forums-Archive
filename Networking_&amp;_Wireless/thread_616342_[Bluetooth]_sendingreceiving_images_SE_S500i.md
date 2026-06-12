---
title: "[Bluetooth] sending/receiving images SE S500i"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by liniaal on 2007-11-18
hi folks,

recently i bought a sony ericsson S500i. love it. only bluetooth support could be a tiny tad better on ubuntu (or i'm just walking the right road in the wrong direction.. :p). sending files to my phone is ok, i already sent some stuff over. only problem is that i really want to send some of my phone's pictures back to the pc (one reason is because i have no more than 16 mb on the celly right now.) i kind of followed a bit of the guides i found with google, but still the 'computer' seems to refuse every file. with the command ```
sudo obexpushd -B -d
``` ('receive files via bluetooth and display all debug messages') i get the following when trying to send one or multiple files:
```
Listening on bluetooth channel 9
OBEX_EV_ACCEPTHINT, OBEX_CMD_CONNECT
0: OBEX_EV_REQHINT, OBEX_CMD_CONNECT
0: OBEX_EV_REQ, OBEX_CMD_CONNECT
0: OBEX_EV_REQDONE, OBEX_CMD_CONNECT
0: OBEX_EV_REQHINT, OBEX_CMD_PUT
0: OBEX_EV_STREAMAVAIL, OBEX_CMD_PUT
0.1: Got header 0x01 with value length 26
0.1: name: "DSC00010.JPG"
0.1: Got header 0xc3 with value length 4
0.1: size: 645859 bytes
0.1: got 984 bytes of streamed data
```
after that my phone stays waiting with "Waiting for the other device to accept item". with ```
gnome-obex-server
``` it's even faster done because it seems to refuse the connection. sometimes, for example when i want to "add the pc to my devices", i am asked to type in a passcode but i have no idea what it should be. my SE phone then says something like "the same passphrase should be submitted on the other device".

i'm ok with linux&ubuntu but not so familiar with bluetooth. can anyone help me? ;) thanks in advance

---

### Post by liniaal on 2007-11-18
well, i finished fixing my problem. a great step forward was installing bluetooth-applet, a program for setting up bluetoot devices via gui. this is a very handy program. only thing is, i still get "file transfer done" windows for every file transferred :P. so what i did is i ran```
bluetooth-applet&
``` and after that ```
gnome-obex-server&
``` and now i can finally send files back to my pc. :)

---

### Post by Blutack on 2007-11-18
Install gnome-vfs-obex or something otherwise, then you can browse your phone's filesystem with nautilus by right-clicking the bluetooth icon in the system tray and choosing Browse Device...

---

