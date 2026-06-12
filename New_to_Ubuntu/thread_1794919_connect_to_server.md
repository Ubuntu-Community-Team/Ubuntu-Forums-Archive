---
title: "connect to server"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-01
how do you connect to remote server on kde?

on gnome it is places > connect to server

how do I go about this on kde?

thank you

---

### Post by 007casper on 2011-07-01
bump

---

### Post by bettaproger on 2011-07-01
what sort of server are you trying to connect to, ssh, telnet, vnc?

if ssh or telnet use the terminal, but im assuming your talking about vnc, use KRDC

---

### Post by 007casper on 2011-07-01
I am connecting to debian server.  

Kubuntu to Debian.

On gnome, when you use connect to server - it gives you a gui file structure to the server, since you are sharing the disk.

I dont have vnc set up on the debian.  I can already ssh.  However, I just wanted to mount the server drive like on gnome.  

places > connect to server

service type: ssh
server: remote.server.com
port: 22
folder: http

then, you get sftp session and the server drive gets mounted.  You can open/edit/revise files.

You cant do that with kubuntu ???

I tried KRDC.  It cant find the server.  Then, again the server doesnt have vnc installed.

---

### Post by 007casper on 2011-07-02
I guess it is really simple, since I cant get any help on this. However, I seem to be stuck on this

does anyone know?

---

### Post by 007casper on 2011-07-02
Use either Konqueror or Dolphin. 

For Konqueror, just type the URL in the address/location bar, e.g. sftp://www.example.com, etc. 

I guess for Dolphin, you can select File->Create New->Create New URL and do the same. However, I cant find "Create New URL".

After using Konqueror, if I go to dolphin and write sftp://www.example.com on its location bar, then domain does load.  However, I cant make it load without going to Konqueror first.

How secure is sftp?  Is it as secure as ssh?

Also, when I do sftp on konqueror, I dont see any lock icon anywhere.  How do I know session is encrypted?

thank you

---

### Post by 007casper on 2011-07-02
On Dolphin File->Create New->Create New URL and do the same. However, I cant find "Create New URL".

???

---

### Post by SeijiSensei on 2011-07-02
Try entering "fish://servername/sharename" in the address bar in dolphin.  That will create an ssh connection to "servername" after prompting for a username and password and will display the files in "sharename."  If you need to connect to a share owned by another user, use "username@servername" in the URL.

---

### Post by 007casper on 2011-07-02
awesome!  thank you so much!

if I do fish://servername/sharename, it defaults to the local client name.  Since I need to use remote user, I tried fish://remoteuser@sremoteserver and it worked.  Thank you once agian.

Now, I am trying to figure how to close the session.  I closed dolphin, and then open it. I was able to login to the remote server without a login.

How do I close the connected session?

---

