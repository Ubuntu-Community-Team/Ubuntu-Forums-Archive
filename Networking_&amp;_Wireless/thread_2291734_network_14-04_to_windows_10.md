---
title: "network 14-04 to windows 10"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by m3t3ors on 2015-08-22
just installed ubuntu 14-04 on my laptop and have windows 10 on my pc, im wanting to network them and share my epsom printer. i have installed samba but when i try network is says not authorised even after ive entered the passwords
any help appreciated

---

### Post by TheFu on 2015-08-22
Which system is the printer connected?

---

### Post by m3t3ors on 2015-08-22
windows machine, i need to access documents on both machines

---

### Post by TheFu on 2015-08-22
For the printer, did you install the printer driver for Linux?  Did you "share the printer" from the Window machine?

Just installing samba is NOT enough to make a CIFS share for windows. You must configure it for the specific directory locations and for users you want to share with. Linux is **always** a multiuser OS - ALWAYS. There is a GUI way, that I've never used. HowToGeek has a how-to guide for setting up samba shares. I suspect the "[Ubuntu Desktop Guide]("https://help.ubuntu.com/stable/ubuntu-help/http://")" probably has this too. Nope, but I left the link for all the other great things it covers.

[http://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](http://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/) shows the non-GUI way on Linux, but GUI way on Windows.
[http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/) shows the GUI way on Linux. Probably what you want.  

If you want to make these mount permanent and always available, there are better ways, IMHO.

If you need/want to access the files on the Linux machine from anywhere in the world, use sftp which is installed as part of the openssh-server package.  Best to use ssh-keys to access this over the internet, never passwords. Also, install fail2ban to block brute-force attacks.  fail2ban settings are good for ssh if you don't change any of the default for ssh.

---

### Post by m3t3ors on 2015-08-22
ok thanks, il give it a go

---

