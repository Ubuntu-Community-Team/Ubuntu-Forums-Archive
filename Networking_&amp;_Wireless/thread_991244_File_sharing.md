---
title: "File sharing"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by chadrlz on 2008-11-23
I have been reading all over the forums and have not gotten what I want. I want to be able to share folders on a local network through Ubuntu. I want something that is fast and secure however after all the how-tos I still haven't been able to do so. I have to admit it but this is the only thing I miss about windows, networking was exceedingly simple, but since I have no desire to go back I just want to know how to accomplish this in Ubuntu. I have the latest release. It is 64-bit.

---

### Post by __Ryan__ on 2008-11-23
If you want to share between Linux + Windows you will need to use Samba.  NFS can be used if it is only Linux.

Both are very secure and fairly easy to setup.

---

### Post by ndefontenay on 2008-11-23
This might help you:

My colleague was seriously thinking about switching to Linux for a very long time but a few apps (photoshop) was holding him.
Until he changed his PC and he was force feeded vista.

He did the great move.

And to his big surprise, not only was it extremely simple to use but his laptop whose file sharing ability seemed "broken" (he couldn't be detected on the network by any windows machines) was detected on linux!

He shared a directory, and to his disappointment, he didn't see the said directory... Finally he thought it might be because it's empty. He added a file inside the directory, he clicked on the directory in linux, he inserted his winXP username and password (not on domain) and he got his file sharing.

I'm sorry for the novel style answer.

Note: I'm struggling sharing between mac and Linux and that's why I'm here (looking for an answeer too)

Nico

---

### Post by chadrlz on 2008-11-24
Well I have gotten as far as making the shares and each share on each machine is visible in Places>Network>Username-Desktop and Places>Network>Windows Network>Workgroup>Username-Desktop. However I can not see shares from other machines. This is really not cool. What I really need is a proven step by step way to do this that is simple and easy to understand. Both Ubuntu machines that I am talking about can see and access a winblows share on the network on a winblows machine.

---

### Post by grickaby on 2008-11-24
If you are looking for a GUI: (point-and-click interface)

[http://www.samba.org/samba/GUI/]("http://www.samba.org/samba/GUI/")

I personally, use Webmin. It has certainly helped me when configuring for Windows shares.

---

### Post by Coreigh on 2008-11-24
Are you sharing between Windows and Linux or Linux only?

Each machine can see its own share from Networking, but can not see the share of other computers?

Using Samba? 

Are all the machine in the same Workgroup? Before you see the share of the other computers you should see the other computers in Networking (Places >> Network)

Are you wanting a public share where multiple users can swap documents and files. Or are you looking to have a single user able to move documents from computer to computer? File and Folder Permissions become and issue.

It helps to know the intended goal to give helpful advice or links.

---

### Post by strueb on 2008-11-24
Coreigh,I'm not the originator, but I do have at least somewhat the same problem.  Just got my laptop configured with Intrepid and got it to recognize my wireless card.  My home network is (except for my laptop, now) a Windows network (one XP machine, the rest Vista).  If I open the system > networks window, I can "open" the networks icon and see the windows computers (I haven't figured out how to share anything on my laptop yet), but the folders that I know are shared on those computers do not show up.  In addition (OK, it's a two-parter - sorry), I have my HP printer shared, but I can't see it, nor can I print to it from Intrepid.  I have no idea what samba is (it appears I need to do something with it?).  Are these two issues related, and how do I solve them? (btw, the windows computers CAN see and access each others' shared files/printers with no issues)

Thank you in advance

---

### Post by Johnhg7 on 2008-11-24
I would try this site, it gives you a gig of storage space for free. I also heard that yahoo has something like this but I am not sure.

[http://www.box.net/](http://www.box.net/)

---

### Post by Iowan on 2008-11-25
strueb:

I'm kinda wearing this one out today, but
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Coreigh on 2008-11-25
STRUEB,

I suspect that they are related and that it is a permissions issue. I do not have Vista to test with but I have seen in XP especially when it is fully updated that the share permissions are restricted, a security measure.
The first thing I would try is to go to one of the shared folders on a Windows machine, righ-click, get the sharing properties and check permissions. If you are on a private nework (your home behind a router) you can choose everyone full access, the default is read only.

I just tried this on my setup (Ubuntu 8.04 and XP) I can see the XP mahine but not the shares. I can connect to the share with my windows logon if I know the share path, but the shared folders do not show up. This is also probably a setting because I also have a 2000 server and all those share show up in my Ubuntu networking.

EDIT:
Oh yes Iowan has a good point. Connecting directly by the IP address may help, but it did not matter on my setup.

---

### Post by strueb on 2008-11-30
> **Iowan said:**
> strueb:

I'm kinda wearing this one out today, but

Iowan;

Thanks very much (and sorry about the lateness of the reply - I've been away...<G>)

I'll give your suggestion(s) a shot and post back here to let you know.

Again, thanks!
:popcorn:

---

### Post by rhcm123 on 2008-11-30
> **chadrlz said:**
> I have been reading all over the forums and have not gotten what I want. I want to be able to share folders on a local network through Ubuntu. I want something that is fast and secure however after all the how-tos I still haven't been able to do so. I have to admit it but this is the only thing I miss about windows, networking was exceedingly simple, but since I have no desire to go back I just want to know how to accomplish this in Ubuntu. I have the latest release. It is 64-bit.

If you want to share the directory /share, follow these simple steps (this is what i do for my systems).

On the computer with the files you want to share:
```

1. sudo apt-get install samba
(that will install samba)
2. sudo apt-get install smbfs
(that will install the smb file system)
3. sudo apt-get install sshfs
(that will install the sshfs file system)

Now, /etc/samba/smb.conf contains the samba configuration file.
open it with: 
4. gksudo gedit /etc/samba/smb.conf
and delete the entire thing and replace it with this:

(this is my samba conf, btw) <- DONT COPY THIS IN!

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	map to guest = Bad User
	wins support = true
	dns proxy = No
	netbios name = (your hostname, find it with the hostname command)
	server string = Samba Server on (hostname) 
	default = Share
	local master = No
	workgroup = (your megasoft workgroup, by defualt MSHOME)
	os level = 20
	security = user
	preferred master = no
	max log size = 50

# Share Folder (/share) configs
[share]
	path = /path/to/the/folder/your/sharing
	valid users = (usernames that will be connecting to the server)
	read only = No
	browseable = yes
	comment = SAMBA directory on (hostname)
	create mask = 0700
	directory mask = 0700

5. Save the file
6. type testparm at the command line. That will check the file for errors
7. If no errors are reported, restart samba (sudo /etc/init.d/samba restart)

```

That's it. I can walk you through connecting and mounting it with /etc/fstab if you want. (this uses smbfs)

To mount this share, do the following on a client (mounting with sshfs) computer:
```

1. sudo mkdir /media/remote
2. sudo chmod 777 /media/remote
3. sshfs (username on server)@(server IP):(path to folder) /media/remote
You will be asked for your password. Type it in.
You should now see the /remote drive on your desktop as if it were local.

```

I typically make directories for the different users on my network (for instance, fred for my dad, elisabeth for my sister, ussr for me, mom for my mom. Then, on the server, i chown the different users and chmod 700 them so only the proper user can access them.
I can talk you through this if you like.

---

