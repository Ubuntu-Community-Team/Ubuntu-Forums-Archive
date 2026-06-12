---
title: "Setting up Samba, Network path not found."
date: 2010-12-16
forum: New to Ubuntu
---

### Post by ScytheX10 on 2010-12-16
Hi. I followed the ubuntu docs for setting up samba. As an initial test, i put guest = yes.. however, I cannot connect from my laptop to the samba server.

I'm running Ubuntu server ( headless)

workgroup = SCYTHE in the conf.

[share]
    comment = Ubuntu File Server Share
    path = /media/secondary
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

i try to connect to the server by going into map network drive and \\192.168.1.100\share
but i get network path not found.. what is going on here?

Note: Firewalls are down, and i port forwared 137-139 and 445

---

### Post by ScytheX10 on 2010-12-16
Doing research as i let this thread sit.

More info:

I can ping, SSH, FTP, SFTP and everything else to my server.

---

### Post by steve7777777 on 2010-12-16
Can you ping the ip address?

---

### Post by ScytheX10 on 2010-12-16
> **steve7777777 said:**
> Can you ping the ip address?

Yes. I have full remote access to the server in question. From my local network and from the internet. 

I just just tried following[ this]("http://ubuntuforums.org/showthread.php?t=202605") tutorial. I have the same result.

---

### Post by Morbius1 on 2010-12-16
And what are the permissions on the target folder:
```
ls -dl /media/secondary
```BTW, I don't think you'll ever get guest access to work using that howto because he's using user level security ( which is preferred ) but is missing a line in the global section:
```
map to guest = Bad User
```

---

### Post by ScytheX10 on 2010-12-16
> **Morbius1 said:**
> And what are the permissions on the target folder:
```
ls -dl /media/secondary
```BTW, I don't think you'll ever get guest access to work using that howto because he's using user level security ( which is preferred ) but is missing a line in the global section:
```
map to guest = Bad User
```

I just reinstalled samba and tried to follow this tutorial:
[http://www.oregontechsupport.com/samba/connect.php](http://www.oregontechsupport.com/samba/connect.php)

When i get to the second page, where you type net view \\192.168.1.100 in windows cmd

i get: The server service is not started

as for permissions:
```
drwxr-xr-x 10 root root 65536 1969-12-31 19:00 /media/secondary
```

---

### Post by ScytheX10 on 2010-12-16
also, this is my smb.conf file 
[URL="http://pastebin.com/LbmvBNCZ"]
http://pastebin.com/LbmvBNCZ[/URL]

want to try and provide as much info as possible.

My laptop is wired to a router, just as my ubuntu server is wired into the same router. I'm port forwarding 137-139 and 445 to 192.168.1.100.
There are no fire walls in place.
I have full connectivity to the ubuntu server, other than samba. So it has to be my configuration either on the ubuntu server or the windows 7 laptop.

---

### Post by ScytheX10 on 2010-12-16
This is driving me absolutely nuts. It there an alternative to samba? I just need to share media files and documents with my laptop.. I primarily just want the media sharing..

---

### Post by cariboo on 2010-12-16
Do you get any results when you type:

```
smbtree
```

The above command is a text based network browser. When you type the command you should see a list of servers and shares, similar to this:

```
smbtree
Enter cariboo's password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
		\\WILLY\TV2            	TV shows part 2
		\\WILLY\TV1            	TV shows part 1
		\\WILLY\Images         	iso images
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Documents      	Documents
		\\WILLY\Music          	Music
		\\WILLY\Movies         	Ripped DVDs
		\\WILLY\print$         	Printer Drivers
	\\RISKY          		XP Computer
		\\RISKY\C$             	Default share
		\\RISKY\ADMIN$         	Remote Admin
		\\RISKY\EPSONSty       	EPSON Stylus Photo R340 Series
		\\RISKY\All Users      	
		\\RISKY\SharedDocs     	
		\\RISKY\print$         	Printer Drivers
		\\RISKY\IPC$           	Remote IPC
		\\RISKY\John
```

---

### Post by Morbius1 on 2010-12-16
Go into your smb.conf file and change this:
> encrypt passwords = noTo this:
>  encrypt passwords = [COLOR=Blue]**yes**[/COLOR]And restart samba:
```
 sudo service smbd restart
```

You still won't have write access to guest because your linux permissions will not allow a write by "others" but that's another matter.

---

### Post by ScytheX10 on 2010-12-16
> **cariboo907 said:**
> Do you get any results when you type:

```
smbtree
```The above command is a text based network browser. When you type the command you should see a list of servers and shares, similar to this:

```
smbtree
Enter cariboo's password: 
APLUS
    \\WILLY                  willy server (Samba, Ubuntu)
     ...
```

```
scythe@scytheserver:/etc/samba$ clear
scythe@scytheserver:/etc/samba$ smbtree
Enter scythe's password:
SCYTHE
        \\SCYTHESERVER                  scytheserver server (Samba, Ubuntu)
cli_start_connection: failed to connect to SCYTHESERVER<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
scythe@scytheserver:/etc/samba$ sudo smbtree
Enter root's password:
SCYTHE
        \\SCYTHESERVER                  scytheserver server (Samba, Ubuntu)
cli_start_connection: failed to connect to SCYTHESERVER<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
scythe@scytheserver:/etc/samba$

```

first try is without sudo

---

### Post by ScytheX10 on 2010-12-16
> **Morbius1 said:**
> Go into your smb.conf file and change this:
To this:
And restart samba:
```
 sudo service smbd restart
```You still won't have write access to guest because your linux permissions will not allow a write by "others" but that's another matter.

didn't change anything. ( connectivity i mean)

Also, testparam says

```
No command 'testparam' found, did you mean:
 Command 'testparm' from package 'samba-common-bin' (main)
 Command 'testparm' from package 'samba4-common-bin' (universe)
```

sudo apt-get install samba-common-bin
```
samba-common-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by ScytheX10 on 2010-12-16
So... is there any lightweight media ( Music/movies/video ) and document sharing services that can interact with windows 7? Like an alternative to samba..? But that won't necessarily
impeed performence? 

( I run a game on this server ( minecraft) but i would like to use it as a file sharing/media server.. but samba is just hating me right now.

Any ideas?

---

### Post by ScytheX10 on 2010-12-16
[[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")

Do you have any idea why the smbtree returned that error..?

I REALLY want to /need to get this working..

---

### Post by ScytheX10 on 2010-12-16
Screw it. Giving up on Samba. 5 hours wasted for nothing.

Does anyone know of an alternative for media file sharing to windows..?

---

### Post by BbUiDgZ on 2010-12-16
> **ScytheX10 said:**
> Screw it. Giving up on Samba. 5 hours wasted for nothing.

Does anyone know of an alternative for media file sharing to windows..?

samba works fine for me.
I would put money on windows7's over paranoid nature being the problem.

try this:
backup your current config
```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.old

```

make new one
```

sudo nano /etc/samba/smb.conf

```

and add,
```

[global]
    security = share
      client lanman auth = Yes
      lanman auth = Yes

[ShareName]
    comment = your comment in here
    path = /path/to/your/share/
    read only = yes
    public = yes

```

so change "/path/to/your/share/" to whatever the path to the folder you want to share then save.

restart smbd
```

sudo stop smbd
sudo start smbd

```

now in the run box in win7 (windows key+R)
```
\\ip.of.your.server
```

---

### Post by ScytheX10 on 2010-12-16
> **BbUiDgZ said:**
> samba works fine for me.
I would put money on windows7's over paranoid nature being the problem.

try this:
backup your current config
```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.old

```make new one
```

sudo nano /etc/samba/smb.conf

```and add,
```

[global]
    security = share
      client lanman auth = Yes
      lanman auth = Yes

[ShareName]
    comment = your comment in here
    path = /path/to/your/share/
    read only = yes
    public = yes

```so change "/path/to/your/share/" to whatever the path to the folder you want to share then save.

restart smbd
```

sudo stop smbd
sudo start smbd

```now in the run box in win7 (windows key+R)
```
\\ip.of.your.server
```

May I ask how you installed samba?
Just sudo apt-get samba or sudo apt-get samba smbfs, did you install samba4?

Also, how do I do a complete purge of all samba related files? I want to try and install again.

I did, sudo apt-get autoremove samba smbfs and then sudo apt-get remove --purge samba.. but when I go to reinstall it it tells me there are samba files that were not overwritten and it causes errors.

---

### Post by BbUiDgZ on 2010-12-18
I just done ```
sudo apt-get install samba
```
as for removing samba, I dont have an answer for you sorry.

---

### Post by ScytheX10 on 2011-01-06
Bringing this thread back up. Tried samba again. Same f'ing issue.

```

[global]
netbios name = scytheserver
workgroup = SCYTHE
security = share
client lanman auth = Yes
lanman auth = Yes
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
interfaces = 192.168.1.1/24

[scy]
comment = scylol
path = /media/secondary
read only = yes
public = yes
```running the ```
smbtree
``` command brings up nothing now.

Note, I also tried path = /something/not/mounted

I'm on the verge of pulling all of my hair out over this..
Was going to spend 200 bucks on a 3tb external to use to transfer data.. but that is unnecessary if I get this to work.

I want to reiterate the following
I can SSH to the server.
I can ping both ways.
I can access the computer outside of the network.
It is a webserver/minecraft server.
It is hosted inside of my lan
Ubuntu server 10.04
Firewalls are off.

[SIZE=1]I'm also just inclined to say "screw windows" completely and bring all my machines over to Linux. Getting tired of the bull from MS. I've even switched from C# to Java recently.. Now I'm ranting. Here's to hoping someone can fix this problem.[/SIZE]

---

### Post by Morbius1 on 2011-01-07
> interfaces = 192.168.1.1/24Are you sure that's right. It looks more like the ip address of your router than the ip address of your server box. Comment it out by placing a # in front of the line, save the file, restart smbd:
```
sudo service smbd restart
```Restart nmbd:
```
sudo service nmbd restart
```And run smbtree again.

You are deviating more and more from the default smb.conf that ships with Ubuntu. See if you have a copy of the original smb.conf at:
```
 /usr/share/samba/smb.conf
```It does have one mistake in it - encryption is set to No when it should be set to Yes.

---

