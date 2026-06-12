---
title: "i need pointers for setting up ubuntu server in my home"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by venkat24 on 2009-10-23
Hi All,
         I am new to Linux and want  to setup a server where in i have many plans to do such as cvs,ssh,......Currently i am having AMD 64 bit Athlon as Desktop machine.My query is can i make my desktop m/c server installing Ubuntu Server Edition?

Please provide me pointers...

Thanks in advance.

Venkat

---

### Post by amauk on 2009-10-23
You can install any "server" package on the Desktop edition of Ubuntu
(the only differences between the desktop & server editions is the graphical interface, kernel options and default installed software)

If you want to "truly" convert a desktop install to a server install (as in, a server install identical to the server ISO image), then in a terminal, do
```
sudo tasksel
```
select the server option, and deselect the desktop option

but as I said, you can install server packages on the desktop edition no problem

---

### Post by venkat24 on 2009-10-23
Thanks for response.Will work on this and let u know if any q's.

---

### Post by k3lt01 on 2009-10-23
If you have another pc download the Ubuntu Server Guide and have it open when your setting things up. It is very self explanatory and if there is anything you have difficulty with you can always ask questions.

---

### Post by linux-hack on 2009-10-23
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by MrWES on 2009-10-23
> **venkat24 said:**
> Hi All,
         I am new to Linux and want  to setup a server where in i have many plans to do such as cvs,ssh,......Currently i am having AMD 64 bit Athlon as Desktop machine.My query is can i make my desktop m/c server installing Ubuntu Server Edition?

Please provide me pointers...

Thanks in advance.

Venkat

Here's the link to the guide I used to setup my server:
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")


~Bill

---

### Post by freak42 on 2009-10-23
sorry, I couldn't resist ;-) 

[IMG]http://imgs.xkcd.com/comics/pointers.png[/IMG]
[SIZE="1"](from [xkcd.com]("xkcd.com"))[/SIZE]

---

### Post by venkat24 on 2009-10-23
Thanks will query if any.Thanks for that kind response.

---

### Post by ukripper on 2009-10-23
For setting up LAMP(Linux Apache MYSQL PHP) stack - check this link [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

And here is the best Postfix guide for setting up secure mail server - [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

For starters I would recommend you use ebox - [http://trac.ebox-platform.com/](http://trac.ebox-platform.com/)

---

