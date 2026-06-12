---
title: "link to another file on linux box"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by u_kraze on 2007-10-26
Hey there,

The sittuation is: i have two linux boxes, (ubuntu 7.10) one is a laptop and another desktop

one is  a test webserver(the desktop) and the other is for my personal use(laptop)

i do vnc over the lan to do sum stuff because i cant do everything command line style. 
I want to be able to view shared files on the webserver (basically to copy over files to the www folder) Do i have to install samba still?

The other thing is ive been reading up on soft links but i dont understand how to do this over the two systems. 

The webserver has ssh and i can log in to it from the laptop but i do not know how to copy i tried using mv /home/name/Desktop/bus(file i want to move) /var/www --> of course i got an error because when i do  pwd on the remote system obviously ill onyl see files on the remote system (the webserver). Is there a way to modify that command (the mv command) so that i copy from one system to the other. 

thank you in advace for your kind help. 

By the way got webserver installed and my laptop rocks with compiz im luvin it.:lolflag:

I switched all of my boxes except one from windows to ubuntu

---

### Post by kah00na on 2007-10-26
Since you have SSH installed, you can "scp" the file to the remote box. This is good because it will also transfer it encrypted.  Here's the syntax:

```
scp ./bus remote_server:/home/name
```

... assuming 
1.  the filename is "bus" and it is in the local directory.
2.  The "remote_server" is replaced with the remote server's IP or hostname.
3.  You have the same user ID setup on both boxes.

If you have a different ID on the server, you'll have to add a little more to the command:

```
scp ./bus remote_user@remote_server:/home/name
```

Same assumptions as before except for number three.  Replace "remote_user" with the user ID you use on your server.

---

### Post by u_kraze on 2007-10-26
ook i tried that and the output is that it says its not a regular file .. i tried googling this and its supposed to work with the whole folder/directory and i also check the scp --help to see if i needed to add a flag to it but i didnt see anyhting.

---

