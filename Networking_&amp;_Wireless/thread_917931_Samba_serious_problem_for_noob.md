---
title: "Samba serious problem for noob"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by RobbieP on 2008-09-12
Hello. I want to apologize if such a thread already exists but i've searched and i couldn't find anything like this even in google.

So i've got a laptop which acts like a server and functions with ubuntu and my studio workstation computer which runs windows vista.

 _Info:_
1.The administrator username of the laptop is robbie and the administrator username of the studio workstation is robbiestudio.

2. I've already added robbiestudio as a network username using the terminal and i ve also successfully set a password.

3. This configuration used to work and it stopped working recently.

4. The ip addresses are correct as i've run ifconfig and double checked them.

5. I noticed that the samba graphic interface never shows up in a window or in the tray. I reinstalled it and reconfigured it several times but with no success.
[U]
The issue:[/U]

When i try to access the only working file of the network which is the Robbie directory it asks me for a username and a password. The robbiestudio set that used to work doesn't work anymore. Neither does the robbie username/password set.

[U]
SMB.conf[/U]

[global]
     General server settings
	netbios name = robbie-laptop
	server string = samba server
	workgroup = workgroup
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = yes

	printing = cups
	printcap name = CUPS

	syslog = 1
	syslog only = yes
	encrypt passwords = yes
	guest ok = no
	guest account = nobody


[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

[netlogon]
    path = /var/lib/samba/netlogon
    admin users = Administrator
    valid users = %U
    read only = no


[Profiles]
    path = /var/lib/samba/profiles
    valid users = %U
    create mode = 0600
    directory mode = 0700
    writeable = yes
    browseable = no


[print$]
	path = /var/lib/samba/printers
	browseable = yes
	guest ok = yes
	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

 Uncomment if you need to share your CD-/DVD-ROM Drive
[DVD-ROM Drive]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes

[MyFiles]
	path = /media/samba/
	browseable = yes
	read only = no
	guest ok = no
	create mask = 0644
	directory mask = 0755
	force user = 
	force group = 





I wanna thank you for you patience with us, the noobs!

---

### Post by superprash2003 on 2008-09-12
in your terminal type cat /etc/samba/smbusers and see if your username is entered in there..also try adding the samba username and again and reboot samba

---

### Post by RobbieP on 2008-09-12
Unfortunately this command line doesn't work. the terminal doesn't pop up a error message but it just ignores it and proceeds to the next line.:confused:

---

### Post by superprash2003 on 2008-09-13
that is because your smbusers file is empty.. you have to add samba users to that file.read this [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by RobbieP on 2008-09-13
Thank you for the reply. I ve followed the guide step by step and by typing the command you've instructed me to type i get this:

robbie@robbie-laptop:~$ cat /etc/samba/smbusers 
sysusername = "robbiestudio"

And unfortunately i still can't log in from the windows pc.:confused:

Ps. I've also tried to save the username without the " marks and the outcome was the same.

---

### Post by superprash2003 on 2008-09-22
did you reboot samba after saving?? are the two pcs able to ping each other?

---

