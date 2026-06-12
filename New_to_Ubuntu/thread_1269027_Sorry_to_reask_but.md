---
title: "Sorry to reask but"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by themarker0 on 2009-09-17
A while ago i posted a thread saying i couldn't connect to a server with any ftp program. It seems none of them work. Connecting to the server works with Nautalis (Sorry for the spelling) But i can't live with that, i need a bit more. Anyone know why it is.


I get an error saying. Could not change local directory to /home/tm0/Desktop/wp-config.php: Not a directory 

And filezilla doesn't install anymore, saying it doesn't work on a 1w/e interface.


Any fixes?

---

### Post by bryceowen on 2009-09-17
I think a little more information is in order. Is the FTP server on your LAN or offsite? Are you able to connect to it with Firefox? Have you tried connecting to the root folder?

---

### Post by themarker0 on 2009-09-17
Localhost connection doesn't work either. But i don't care. I want to connect to my website host. Which doesn't work. the data is correct. I can connect with Fireftp but it sucks really. So i think i did something bad... I can also view the site, but it just send files...

---

### Post by bryceowen on 2009-09-17
So, in terminal, when you type:
```

ftp ftp.hostname.com

```
Do you ever get a prompt for your username/password or does it throw the error before that even happens?

---

### Post by themarker0 on 2009-09-17
> **bryceowen said:**
> So, in terminal, when you type:
```

ftp ftp.hostname.com

```Do you ever get a prompt for your username/password or does it throw the error before that even happens?


That just started my computer as an FTP server... Also i need SFtp so.. thats my reason behind Filezilla or another ftp program..

---

### Post by gordintoronto on 2009-09-17
> **themarker0 said:**
> 
I get an error saying. Could not change local directory to /home/tm0/Desktop/wp-config.php: Not a directory 

Any fixes?

What FTP program said this?

The complaint is about the setup on *your* computer, not the computer you are trying to contact.  I suspect you could edit a config file to fix it.

---

### Post by themarker0 on 2009-09-28
Sorry for the gaint necropost but sorry was away. School you know?

Its gftp that gives me an error. The rest just crash or won't connect.

---

### Post by cariboo on 2009-09-28
If you can connect using sftp in nautilus, you should be able to connect with gFTP or Filezilla. Remember you have to set the port to 22.

---

### Post by missmoondog on 2009-09-28
> **cariboo907 said:**
> If you can connect using sftp in nautilus, you should be able to connect with gFTP or Filezilla. Remember you have to set the port to 22.


port 22? is that for running a server?

otherwise, shouldn't it be port 21?

---

### Post by themarker0 on 2009-09-29
> **cariboo907 said:**
> If you can connect using sftp in nautilus, you should be able to connect with gFTP or Filezilla. Remember you have to set the port to 22.
Filezilla doesn't support Ubuntustudios for some reason. Its really weird. (Do a V-Box and you will see)) Gftp won't allow me to do sqat (That was the error),Nautilus doesn't just offer enough or tickle my fancy and i need a better of a ui.

Correction I can connect all i want. I can't send anything though. Thats my issue. And filezilla has this error

FileZilla FTP client cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type

---

