---
title: "Apache &amp;&amp; FTP"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by MontelEdwards on 2009-05-16
OK,  I am really confused. And embaressed that I asked this but....
I wanted to know how I can make my Apache with ftp access?
I really need this BADLY. 
thanks a lot.


-montel

---

### Post by Alterax on 2009-05-16
No way that I know of.  You might try installing vsftpd; it should be able to do what you want.

---

### Post by bodhi.zazen on 2009-05-16
> **m.deonte said:**
> OK,  I am really confused. And embaressed that I asked this but....
I wanted to know how I can make my Apache with ftp access?
I really need this BADLY. 
thanks a lot.


-montel

What is it you are wanting to do exactly ?

---

### Post by MontelEdwards on 2009-05-17
hi bodhi, glad to see ya.

Well i want FTP access to my computer because I would like to have my files on the go. 
I need a password of course i know.
But i thought that there was like an addon for Apache but i see that I was wrong.

Or is there?

---

### Post by txcrackers on 2009-05-17
FTP is insecure (sends passwords in the clear). You should look into using SSH and SFTP, which are typically installed by default anyway. And an SSH server is actually much easier to set up than an FTP server...

---

### Post by LeonBlade on 2009-05-17
Just use SSH.

---

### Post by irv on 2009-05-17
I use the plugin with FireFox called FireFTP. I set up my server, login and password and I have a graphic interface to my server. I can just drag files over to my server window. It just that easy.

---

### Post by MontelEdwards on 2009-05-17
what is SSH?
I am guessing SFTP is secure FTP.
I need instructions on how to do this

---

### Post by irv on 2009-05-17
Another thing you can do is go to your “Places” menu while in your desktop and >Connect to server>
FTP (with login). Fill in the Server, Port, Folder, User Name and put a check in the Add bookmark and give it a name. Then all you need to do to get to your FTP server is goto “Place” and click on the name you gave your bookmark
[ATTACH]114136[/ATTACH]

---

### Post by cariboo on 2009-05-17
to use ssh and sftp/scp you need to install openssh-server on the server, then on your desktop open nautilus and in the location bar enter:

```
sftp://username@server
```

This will open the file system on your server in nautilus.

---

### Post by irv on 2009-05-17
> **cariboo907 said:**
> to use ssh and sftp/scp you need to install openssh-server on the server, then on your desktop open nautilus and in the location bar enter:

```
sftp://username@server
```

This will open the file system on your server in nautilus.

This may sound crazy but I don't have a location bar to enter anything into. See my screen shots.
[ATTACH]114143[/ATTACH]

[ATTACH]114144[/ATTACH]

---

### Post by bodhi.zazen on 2009-05-17
click the little icon in the upper right , the one that looks like a note pad and a pencil ...

---

### Post by irv on 2009-05-17
> **bodhi.zazen said:**
> click the little icon in the upper right , the one that looks like a note pad and a pencil ...

Thanks, Even after you told me about this I still looked for it because it was to my left. It amazing little things mean a lot. Oh, I think that the title of a song! :p

---

