---
title: "Only root can get online"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by amdalex on 2008-01-04
I have the Juno program installed on my computer with Edgy, but Juno only connects to the Internet when logged on as root. Also I gave my account all the privileges but it still does not work.:confused:Is there anything I can do? thanks

---

### Post by amdalex on 2008-01-04
bump

---

### Post by amdalex on 2008-01-05
bump Doesn't anybody know???

---

### Post by amdalex on 2008-01-05
bump

---

### Post by sdide on 2008-01-05
What is Juno? 
What does it do?
How do you execute it?

---

### Post by amdalex on 2008-01-05
Juno is an ISP. Their program allows me to get online via the phone line. I execute it by clicking on the icon on my desktop.

---

### Post by amdalex on 2008-01-05
It seems like only root is allowed to use the modem. I gave all users permissions to access and modify /dev/modem and it made no difference. The Juno program works on all other accounts except for it doesn't dial out and gives me a connection error. this is very puzzling

---

### Post by sdide on 2008-01-06
What is the error message exactly?
and could you post output from the command:
$ ls -l /dev/modem

---

### Post by amdalex on 2008-01-06
The error message says it can't connect at the time with my selected numbers. On the other accounts the modem makes no noise where as in root I can here the modem dialing. The output from your command is "lrwxrwxrwx 1 root root 8 2008-01-06 11:15 /dev/modem -> ttySHSF0".

---

### Post by amdalex on 2008-01-06
bump

---

### Post by amdalex on 2008-01-06
bump

---

### Post by amdalex on 2008-01-06
bump

---

### Post by sdide on 2008-01-06
I'm not sure, easiest thing would probably be to execute the "icon on your desktop" whatever that executes with gksudo. That way you'll be prompted for your password and after that the program  will execute with root privileges.
(of course you need to be in the sudoer list)

---

### Post by amdalex on 2008-01-06
Thanks a lot. It worked.

---

