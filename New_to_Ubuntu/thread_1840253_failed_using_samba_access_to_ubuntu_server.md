---
title: "failed using samba access to ubuntu server"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by samuel5767 on 2011-09-07
Hi
As the sub forums title. I am an absolute beginner on ubuntu server
I have a Ubuntu 8.04.4 server and recently I just installed samba version 3.0.2.8a on the server

 I have configured the smb.conf and it looks like this

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

Somehow from Windows XP cant connected to the server; error : "The Network Path Not Found. "

Ping and SSH to the servers works fine. Firewalls are DISABLE on Windows XP but on the Ubuntu i cant completely disable it becoz it will block the internet access for everyone connect to this server


Pls advise
Thank you

---

### Post by samuel5767 on 2011-09-07
Hello

Any experts out there can give me a hand on this?

Thank you

---

### Post by vkrische on 2011-09-07
I am extremely new to Ubuntu, and although I don't have an answer I have been working on this as well, and didn't want you to hang without a response. 

So far I have installed SAMBA and SWAT
```

sudo apt-get install SAMBA
sudo apt-get install SWAT

```

Then I typed [http://localhost:901](http://localhost:901) in a browser but was having problems getting SWAT to show the all the options. I set my root password
```

sudo passwd root

```
Then logged into SWAT with user:root password: root password. That fixed the button problem. Now I am reading Ubuntu Unleashed to configure SWAT. 

Maybe you can try SWAT if you haven't already and that will help. Like I said, I am walking through this as we speak.

Good luck, 
Vince

---

### Post by vkrische on 2011-09-07
UPDATE:

I added a printer and a share from SWAT and initially I could not view them under network on my WIN7 laptop. I went to \\vks in an explorer window and when it prompted me for a password I used vks\user (the name of my ubuntu computer\ubuntu user) and the Ubuntu password. Now I can navigate to the Ubuntu machine and access my shared folder and printer.

I am sure I can do much much more with SWAT and SAMBA, but this is what I needed for now. Hope it helps.

---

### Post by samuel5767 on 2011-09-08
Thanks for the suggestions vince

However I've found the solutions

Need to enable TCP ports 139 and 445 and UDP ports 137 and 138 @ubuntu server

And make sure the windows box firewall are disabled.

Problem resolved.

---

