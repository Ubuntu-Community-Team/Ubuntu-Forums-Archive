---
title: "Can't upload to FTP anonymously. . ."
date: 2009-05-21
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-05-21
Hi!  I am trying to get vsftpd setup on my local server to replace samba, but I can't get anonymous uploading to work. (I know this has security implications, but I an behind a firewall).  I get the error: Operation failed from nautilus.  Here is my vsftpd.conf:

[ATTACH]114587[/ATTACH]

Anything I can do?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-05-21
I changed the permissions with :

sudo chmod +rwxX /home/ftp

But I still get the error. . .

---

### Post by pi.boy.travis on 2009-05-21
Bump?

---

### Post by pi.boy.travis on 2009-05-22
Bump

---

### Post by nandemonai on 2009-05-22
Had a quick look at your conf, seems ok (It's late though admittedly).

Tried logging in from term just to test?

Could be an issue Nautilus side.

---

### Post by albinootje on 2009-05-22
> **pi.boy.travis said:**
> I can't get anonymous uploading to work. (I know this has security implications, but I an behind a firewall).  I get the error: Operation failed from nautilus.  

From my working ftp-server in my home LAN :

$ grep -r -i anon /etc/vsftpd.conf
anonymous_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
# anon_world_readable_only=NO
anon_umask=002
anon_root=/home/ftp

And I just tested it with Nautilus, uploading worked, except that 
opening the pdf file that I copied gave a "damaged file", but after making a copy of that onto my desktop it worked fine.
So, I suggest to use a real ftp-client to test like gftp or ncftp.

---

### Post by pi.boy.travis on 2009-05-22
I tried using the terminal and gftp. gftp doesn't even give an error, but the file isn't uploaded. . .  It may have something to do with the fact that this is a virtual server, and I may have messed up when I set up network adapter bridging. . .

---

### Post by albinootje on 2009-05-23
> **pi.boy.travis said:**
> I tried using the terminal and gftp. gftp doesn't even give an error, but the file isn't uploaded. . .  It may have something to do with the fact that this is a virtual server, and I may have messed up when I set up network adapter bridging. . .

Are you using a firewall ? 
I think that in some cases you need port 21 and 20 open for ftp traffic.

What does "telnet your_ftp_server 21" ?

---

### Post by spiderbatdad on 2009-05-23
Tell vsftp which port to listen on in the conf file:
listen_port=222
forward that port via your router, and make sure the port is not in use already $neststat -tulpen and make sure ufw is not blocking the port on your machine. Restart vsftp.

---

