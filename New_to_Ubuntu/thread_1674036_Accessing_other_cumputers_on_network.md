---
title: "Accessing other cumputers on network"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by boldhoof on 2011-01-23
Hi

I want to access a share drive on another computer, which is running XP. But I can't seem to find out how to do it. Any simple easy to follow help appreciated.

---

### Post by cavh on 2011-01-23
Places, Connect to server, insert the other machine's IP address (if you have it) or machine name

---

### Post by boldhoof on 2011-01-23
> **cavh said:**
> Places, Connect to server, insert the other machine's IP address (if you have it) or machine name

Under Places I do not have connect to server, can't find that option at all.:-s

---

### Post by [Snc] on 2011-01-23
> **boldhoof said:**
> Under Places I do not have connect to server, can't find that option at all.:-s

you can run

```
nautilus-connect-server
```

instead, make sure to sudo if you have permission problems ;)

---

### Post by NightwishFan on 2011-01-23
He might be on Xubuntu.

---

### Post by Morbius1 on 2011-01-23
Gigolo. That's not an accusation it's a utility. The advantage of gigolo is that you can also use it to automount remote drives. Give it a shot: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

I may be missing something but you're using XFCE not Gnome, right?

---

### Post by boldhoof on 2011-01-23
> **Morbius1 said:**
> Gigolo. That's not an accusation it's a utility. The advantage of gigolo is that you can also use it to automount remote drives. Give it a shot: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

I may be missing something but you're using XFCE not Gnome, right?

Yes XFCE Xunbuntu 10.10 install.

I installed Samba which gave me the Samba Server Configuration and on the other machine in My Network Places I can see and access Home/downloads, but I can not see from Xubuntu to the XP machine.

I will try gigolo, tried the nautilus-connect-server it installed and then ran, but no luck in finding the other machine.

---

### Post by Morbius1 on 2011-01-23
>  I will try gigolo, tried the nautilus-connect-server it installed and then ran, but no luck in finding the other machine.     The reason I suggested gigolo is because Thunar doesn't have a built in network browser. Unfortunately both gigolo and nautilus-connect-server rely on the same packages so if one failed it's likely so will gigolo.

From a terminal post the output of the following command:
```
smbtree
```It should show you all the shares on your network or post errors if something is amiss.

---

### Post by boldhoof on 2011-01-23
> **Morbius1 said:**
> The reason I suggested gigolo is because Thunar doesn't have a built in network browser. Unfortunately both gigolo and nautilus-connect-server rely on the same packages so if one failed it's likely so will gigolo.

From a terminal post the output of the following command:
```
smbtree
```It should show you all the shares on your network or post errors if something is amiss.

Thanks for your help, followed the gigolo link mentioned and followed the instructions, I now have access to the shared drive and printer. I did the ```
smbtree
``` and it came out with the following:
```
MSHOME
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
cli_start_connection: failed to connect to UBUNTU<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\PINKFLOYD      		
		\\PINKFLOYD\F              	
		\\PINKFLOYD\D              	
		\\PINKFLOYD\EPSONSty       	EPSON Stylus Photo R300 Series
		\\PINKFLOYD\print$         	Printer Drivers
		\\PINKFLOYD\SharedDocs     	
		\\PINKFLOYD\IPC$           	Remote IPC
		\\PINKFLOYD\Backup Drive

```

I have no idea what IPC is and the error regarding NT_STATUS.

---

### Post by Morbius1 on 2011-01-23
Well that's interesting.

You can now access the Windows machine from Linux.
You can also access the Linux machine from Windows.
Yet smbtree gives you an error when it tries to access the Linux shares from it's own Linux machine.

Don't have an answer for that one but I guess it doesn't matter since everything seems to work.

---

### Post by darkmode on 2011-01-28
I have a better solution  it simple you just need to install fusesmb its works like that

sudo apt-get install fusesmb

mkdir -p Network

fusesmb Network

but you need to have samba instaled .

---

