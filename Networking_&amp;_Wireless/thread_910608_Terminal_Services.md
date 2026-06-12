---
title: "Terminal Services"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by 9krpmrx8 on 2008-09-04
Can a desktop running Ubuntu access a Server running server 2003 through terminal services?  I want to try Ubuntu in a business environment but I need to run a Windows Medical Practice Management software suite residing on the server.  Thanks.

---

### Post by 9krpmrx8 on 2008-09-04
Anything?

---

### Post by jerome1232 on 2008-09-04
I've accessed my friends Windows Server 2003 with terminal services under Ubuntu 8.04. I'm not sure if he had to install anything extra or not, obviously it's not my server I didn't have to config it.

So my answer is yes you can access a windows server with terminal services.

I've also used VNC tunneled through ssh, with openssh and VNC installed on the Windows Server.

---

### Post by 9krpmrx8 on 2008-09-05
What program were you using in Ubuntu to access the server.  I don't want to use vnc, I want access through terminal services/rdp.  Thanks for the replies.

---

### Post by jerome1232 on 2008-09-05
> **jerome1232 said:**
> I've accessed my friends Windows Server 2003 with terminal services under Ubuntu 8.04. I'm not sure if he had to install anything extra or not, obviously it's not my server I didn't have to config it.

I used terminal services and I have used vnc/ssh. Both worked.

---

### Post by 9krpmrx8 on 2008-09-11
Okay, now how do I maximize the terminal services window?

---

### Post by 9krpmrx8 on 2008-09-11
OKay I can connect but I cant adjust the window to fullscreen.  Can anyone help?

---

### Post by wgarider on 2008-09-12
If your using the Terminal Services Client that comes with Ubuntu, there should be a tab called Display - look for the first section that says "Remote Desktop Size" - there's an option there to Operate in Full Screen mode.

FYI - I use this everyday to manage my Windows servers and once in a while, it will hang and I have to use Ctrl-Alt-Enter to get the TSC window to where I can minimize it to go back to the Ubuntu desktop....

Hope that helps.

---

