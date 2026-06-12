---
title: "Thunderbird outgoing mai"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-12-03
Okay, so I receive mail in my thunderbird from both my gmail, and verizon accounts. But, I can't send any. It asks for the password, but then asks again? Not sure where I need to look or what for to make necessary changes. I am sure it is something simple, but.......

---

### Post by wjp.reg on 2008-12-03
You need to specify secure connections for POP using port 995 (SSL) and SMTP server using port 587 (TLS) settings.  If you go to your gmail account settings there is help which explains this.

cheers.

---

### Post by evilkastel on 2008-12-03
ok, it should be an port issue. 

[http://ubuntuforums.org/showthread.php?t=445043](http://ubuntuforums.org/showthread.php?t=445043)

also, check in the extension preferences that the ports are open. (it should appear as three green balls. if one of them or two are red, you have to change or enable the port. Sometimes port numbers under 1024 get blocked, so i'll recommend to use numbers btween 1025 and 1099.

---

### Post by babloo75 on 2009-01-23
> **Andrew79 said:**
> Okay, so I receive mail in my thunderbird from both my gmail, and verizon accounts. But, I can't send any. It asks for the password, but then asks again? Not sure where I need to look or what for to make necessary changes. I am sure it is something simple, but.......

I am facing this same problem, but with and addition. First of all, I am using yahoo mail i.e ymail.com (instead of gmail). it is able to recieve emails but cannot send outgoing mail and keeps on asking for password.

2nd problem is that when i download my emails from yahoo server to my thunderbird email client, it downloads these mails but then these mails get deleted from the server and inbox becomes empty on yahoo mail. how can i prevent this from happening.
please help....

---

### Post by hyper_ch on 2009-01-23
> **babloo75 said:**
>  how can i prevent this from happening.
please help....

does yahoo support imap?

---

### Post by babloo75 on 2009-01-24
Ya, it does.
i got the solution and am posting it for others so that no body else faces this problem.

open thunderbird. go to Edit> Account settings. Select server settings. and fill the details as depicted in Yahoo mail options for POP & mail forward. In addition select "leave messages on server" in the list below. this was for incoming mail.
For outgoing mail, select "outgoing server (SMTP)" on the left. select the one shown in the box on right and then edit. You need to fill the correct settings here too, as shown in yahoo mail server (including both port and SSL)
select "OK" You are done.

---

### Post by hyper_ch on 2009-01-24
if it supports imap, then it should keep the mail also on the server.

---

### Post by babloo75 on 2009-01-24
yes after selecting that option "leave messages on server", it doesn't delete them.
now alls fine.

---

### Post by hyper_ch on 2009-01-24
then you don't use imap

---

### Post by mkvnmtr on 2009-01-24
To the orginal poster. Make sure when it asks for a password you click on save the password.

Thanks for  the information about Yahoo I have been having a hard time getting them set up 
.

---

