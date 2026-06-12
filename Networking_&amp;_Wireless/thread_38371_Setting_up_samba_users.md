---
title: "Setting up samba users"
date: 2005-05-31
forum: Networking &amp; Wireless
---

### Post by Haegin on 2005-05-31
Good morning!
I have been trying to set up samba and although I got past the problem with samba common being too recent (force it to downgrade using the menus, then re-install ubuntu-desktop afterwards) I now have another problem:

I have two windows boxes trying to connect to my computer to access a printer but they cannot connect to my pc (don't have permission). How can I set my computer up so anybody can access my shared folder and the printer? I'm reasonably new to linux so don't refrain from making it too simple, simple is good!

---

### Post by accmariano on 2005-05-31
Hi, 

I hope it help a little

Are u using security=share or security=user in smb.conf.?

If Are you using user security mode you have to generate smb passwords for users u want with smbpasswd command.

Also u have to allow access to smbd daemon in /etc/hosts.allow

Post more information about your smb.conf to help you better

Regards
Mariano

[QUOTE=Human Prototype]Good morning!
I have been trying to set up samba and although I got past the problem with samba common being too recent (force it to downgrade using the menus, then re-install ubuntu-desktop afterwards) I now have another problem:

I have two windows boxes trying to connect to my computer to access a printer but they cannot connect to my pc (don't have permission). How can I set my computer up so anybody can access my shared folder and the printer? I'm reasonably new to linux so don't refrain from making it too simple, simple is good![/QUOTE]

---

### Post by Haegin on 2005-05-31
my smb.conf is now online here : [http://www.harrymills.me.uk/images/smb.conf](http://www.harrymills.me.uk/images/smb.conf)

and yes, i know its not an image...

can i remove the security=users line (its users i think) and just let anybody on the network in? Its already got secured wireless and if somebody plugs in then I want them to have access to all the shares anyway.

---

### Post by accmariano on 2005-06-01
Hi, 

Your SMB is configured to every time someone want to connect to a resource ask for username and password

(this is the line security = user)

The easiest mode to configure access to everyone from your windows boxes without user an passwords is to change this line to:

security = share

but WARNING, this make accessible all your shares  as "Harry" to everyone as soon then can access your network interface. This is because the line public = yes. If you don't want to make some share accessible to everyone you have to change in each share the line to public = no and SAMBA ask for username and password when someone connect to it.

To assure that files in share resources can be read by everyone, you have to set some permissions in file system as: chmod -R a+r /home/harry/LocalShare, but I repeat WARNING !!!!

Also you can configure access to everyone in mode security = user using guest account but it is a litle more dificult to setup.

Hope it help
Mariano



[QUOTE=Human Prototype]my smb.conf is now online here : [http://www.harrymills.me.uk/images/smb.conf](http://www.harrymills.me.uk/images/smb.conf)

and yes, i know its not an image...

can i remove the security=users line (its users i think) and just let anybody on the network in? Its already got secured wireless and if somebody plugs in then I want them to have access to all the shares anyway.[/QUOTE]

---

### Post by Haegin on 2005-06-01
Thanks accmariano but im still having problems, think one of the windows boxes is messed up (no surprises there) as it is showing shares on computers that are offline. The other one seems to be normal and is showing shares from the other windows box that is on but not the linux box.

The main thing I need to share is the printer otherwise my dad is threatening to put it on my sisters machine which means I won't be able to access it easily. :( Currently I can't see myself sharing files much but my sisters and dad might (as I'm on linux all the file formats are different etc so converting them is a chore, maybe I should get them open office...)

Also how do I get swat working? I have installed it using apt-get but its not there when I go to [http://localhost:901](http://localhost:901)

---

### Post by Haegin on 2005-06-01
I have fiddled with the smb.conf file following some direction sin the documentation and now the computers can see the printer but they can't print to it. This is the new conf file:

```
[global]
	workgroup = MILLS
	encrypt passwords = yes
	security = share
	printcap name = cups
	disable spools= Yes
	show add printer wizard = No
	printing = cups
	wins support = no

[share] 
	comment = Harry's Share
	path = /home/harry/LocalShare
	read only = yes
	guest ok = yes
	guest only = yes
	available = yes
	browseable = yes
	public = yes
	writable = no

[printers]
	comment = All Printers
	path = /var/spool/samba
	guest ok = Yes
	printable = Yes
	use client driver = Yes
	browseable = Yes
	guest only = yes
```

All I need to be able to do is share a printer (Epson Stylus CX6600) (its on linux as a CX6400) on a network within one workgrouop. It can't be that hard to do can it?

---

### Post by accmariano on 2005-06-01
Hi, 

The problem you are talking about is browser service problem, that is independant of efective shares in the netowrk. I directly disable browser system in my windows boxes because is really bad and do a lot of broadcast in the network, is not necesary to use it. 

To see if really your shares are working you have to try access them from tools¦map network drive or Start¦Run and type full path to the share. It seems that your SAMBA server are not announcing its shares in the network, but they could be there. Or your browser service client in windows is not running.

Try to access them by typing full path where I said you above, and they should work.

If you have a domain maybe you can try to configure SAMBA to validate user in that domain. I prefer not to do that. 

Other problems maybe are encrypted passswords related and signed communications. Specially in pre windows 2000 versions.

Regards

[QUOTE=Human Prototype]Thanks accmariano but im still having problems, think one of the windows boxes is messed up (no surprises there) as it is showing shares on computers that are offline. The other one seems to be normal and is showing shares from the other windows box that is on but not the linux box.

The main thing I need to share is the printer otherwise my dad is threatening to put it on my sisters machine which means I won't be able to access it easily. :( Currently I can't see myself sharing files much but my sisters and dad might (as I'm on linux all the file formats are different etc so converting them is a chore, maybe I should get them open office...)

Also how do I get swat working? I have installed it using apt-get but its not there when I go to [http://localhost:901](http://localhost:901)[/QUOTE]

---

### Post by Haegin on 2005-06-01
ok, got some things working (finally!!!)

from each of the two wireless win xp boxes (im testing with these 2 and ignoring the others until they work) I can see the shared folder on the other computer and access it.

I have mapped the shared folders to different drive letters

The linux box can't even see the rest of the network... but the rest of the network can see it but not access it. I can't even see the damn workgroup, it just comes up with "windows network" then when I click on it I get naff all.

The win xp machines can see the printer and claim that its ready but when I go into ms word and click print it waits for ages to get to the print dialog box (they are slow computers but not that slow) and then when you click print it gets halfway through background printing then the entire program crashes.

The win xp machines cannot access the linux box

How do I set it up so that whenever somebody accesses my linux machine they automatically connect as a guest using no password?

---

### Post by Haegin on 2005-06-01
file sharing is now fine but i have no printcap file so printing doesn't work, what format are printcap files in and where are they on ubuntu?

---

