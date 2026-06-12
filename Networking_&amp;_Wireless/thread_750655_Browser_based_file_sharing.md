---
title: "Browser based file sharing"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by bohboh on 2008-04-09
I have a machine set up with 6.06 desktop. It has a static IP. I want to be able to have access to files on the machine remotely. What is the best (easiest) way to achieve this? Are there any browser based file sharing applications?

---

### Post by superprash2003 on 2008-04-09
FTP?you can install protftpd and gproftpd(gui for proftpd) and setup an ftp server

---

### Post by Eiríkr on 2008-04-10
Another, possibly easier, setup is to install ssh on the machine that will be the server.  Then, from another Ubuntu machine, just open your handy Nautilus file browser, click in the location bar (hit Ctrl+L or click View -> Location Bar to display it if it's hidden), and type:
```
sftp://IP.ADD.RE.SS
```
Replace the caps with the IP address of the server machine, and Bob's your uncle.  

Cheers,

Eiríkr

---

### Post by bohboh on 2008-04-10
Ah, should have said. This needs to be easily accessible for users who have no idea or where with all to set up and use ftp. Ideally, i would like to distribute a username, password and no-ip address and allow them to gain access that way.

It currently already has ftp set up and in use (for me only) but other users keep having issues which is starting to test my patience! :)

---

### Post by Eiríkr on 2008-04-10
With SFTP using the **ssh** package, all you need is the username, password, and some means of addressing the server.  IP address is the most certain, but you could definitely use hostnames instead if you have a DNS server installed and configured on your LAN, or if you've got properly configured hosts files.  

If that's not your preferred flavor, your next best bet could be NFS or maybe Samba, but which one depends somewhat on your operating parameters.  Are your clients always on other Unixy machines, or is Windows in the mix?  Do you need to have communally-accessible shared directories and files, or will each client access their own private share?

Cheers,

Eiríkr

---

