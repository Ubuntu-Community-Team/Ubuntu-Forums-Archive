---
title: "i can get windows to see my ubunutu computer"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by ljonesj on 2007-02-08
so i have ubuntu installed on another computer but my windows computer just has me log into it when i try to use my samba server but it just comes back to the log in how do i fix it and sorry if this is in the wrong spot

---

### Post by Iowan on 2007-02-08
Please forgive my being dense, but a period or two (.) might help me understand what you're asking. I get lost somewhere between > my windows computer just has me log into it when i try to use my samba server and > but it just comes back to the log in  I'm wondering if the username you're using  has an account on the server AND Samba - but I'm not sure if "it" is the Windows box or the server.

---

### Post by ljonesj on 2007-02-09
sorry for that. my windows machine is a laptop. the linux samba machine is a old dell optiplex gx 110 that i have a 160 gb usb harddrive setup as a file server. i have gotten everything up and running and windows sees the ubuntu file samba server but when i try to access it has me log in but when i put in my user name and password either one i use it just goes back to the log in then.

---

### Post by gradedcheese on 2007-02-09
You need to add yourself to smbusers, setting your password.  To do that:

sudo smbpasswd -a your_user_name

Now restart samba:

sudo /etc/init.d/samba restart

and try logging in from Windows gain.  If the first command complains that you already exist, do it without the '-a' (ie: 'add') to just set your password.

---

### Post by ljonesj on 2007-02-09
ok tried what you said and it just gives me the options when for samba user adding it wont take it

---

### Post by ljonesj on 2007-02-09
finnaly got it thanks for your help on this everyone

---

### Post by ljonesj on 2007-02-09
ok got my samba server working now how do i share my printer

---

### Post by Iowan on 2007-02-09
[https://wiki.ubuntu.com/PrinterSharing]("https://wiki.ubuntu.com/PrinterSharing")
Here's one place to check.

Sorry I couldn't be more helpwith original problem.  I think I have an Optiplex gx110 about to become a (media) server.

---

