---
title: "Secure sharing of folders and network"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by ingvald on 2007-06-19
I need some help in order to setup my network at home. (newbie in linux and network setup)

I have to computers running ubuntu 6.10 (one wired and one wireless), and one running win XP or maybe soon VISTA. The wired computer will be on continously, and will have a external harddive connected that I want to share on my network. 

So I want to be able to read/write to shared folders from windows to ubuntu and from ubuntu to windows. 
BUT I am also sharing my adsl with my neighbour so it is very important for me that the shared folders have some sort of security. I dont want my neighbour to be able to open my shared folders, eventhough he has received my WEP password for my wireless router connection. 

How should I setup my network to accomodate all this??? 

I also want to safely remote control my ubuntu computer (the one that works as a "server", if that is what it is).

T

---

### Post by bluetracer on 2007-06-19
Probably the best thing to do is to use Samba, and not allow anonymous access, so that in order to access the shares you must provide a username and password.

You can accomplish this in System / Administration / Shared Folders

Usernames and passwords can be configured in System / Administration / Users and Groups

There's a good guide on the [Wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service").

---

### Post by ingvald on 2007-06-19
Thanks, 
But I thought Samba was only for windows to linux. You are suggesting using samba also for ubuntu to ubuntu, correct?

---

### Post by bluetracer on 2007-06-19
It'll work, since Ubuntu has both a samba client and server.  NFS would be more elegant, but if you're running more than one sharing protocol on the same folder you could end up with weird sharing issues, so best just stick to one.

---

### Post by ingvald on 2007-06-22
I have tried.....and failed....to get my network running, but I have most likely followed the guide on wiki ( How to install Samba Server for files/folders sharing service) on both my server and my client. Ubuntu still confuses me:-) 

How shall I configure mye client laptop (my other ubuntu machine)? 

I have uninstalled both samba and NFS from Synaptic, and will try one more time to get this right.  

Thanks for your answers,

---

### Post by dardack on 2007-06-23
I'm a newbie myself.  I have a mythtv box and 2 ubuntu, with 1 of those dual boot to xp.  I used to use samba alot with mythtv until i upgraded the hdd's in there.  So this is myexperience;

I use WebMin to set up samba, basically a web based interface for setting up services and such.  Allows you to change permisions and what folders to share in samba, on the server.  Of course samba needs to be running  on the server.

Than you need to have samba running on your client.  Then i think you need these two packages:

apt-get install smbclient
apt-get install smbfs

(not 100% sure, i know i need it on my mythtv box, cause i was mounting a samba share from my ubuntu computer, but never used the client on my other ubuntu computer)

now to connect i believe you run something like

smbclient \\\\server-name\\shared-folder-name -U username
should then prompt you for password, and than will put you at:
smb -> prompt or something like that
Type help for commands.

However, if you want to mount that share you edit your /etc/fstab and add this to end i think:

//server-name/shared-folder-name /linux/mount/point smbfs username=username,password=password 0 0

then:  mount -a 
to mount it, now it should be like any other drive.

Hope that helps.

---

### Post by airtonix on 2007-06-30
Also use firestarter to modify your firewall(the one part of the ubuntu-server) to not allow connections from the neighbours ip addresses to ports 135,136,137,138,139 and 445.

preferably. you want to have two network cards in the server, one that goes to a wifi adaptor that your neight bours connects to and the other card connects to your internet device.(preferably one that is also a four port WIRED router)

this way you use firestarter to share the internet connection between eth0(lan cable to your internet connection device) and eth1 (the lan cable to four-port wifi device).

you then loginto you internet device and prevent internet access from the IP ranges on the neighbours connection(the four ports on the wifi)....why? so you can shape their internet access speeds...

how? with squid proxy cache. and delay buckets.

You would have to force them to use your proxy server.....

i have a working home network that shares samba shares full of media to my houstmates, at full 10/100 speeds, but their internet access is shaped to 3kb/s for normal sites and 1kb/s for myspace. 

My ISP provides quota-free content for me...abc.net.au, oftheworld.tv, etc etc etc.

the best is the ubuntu repos....seems to be synced quite often.  [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/)

so these are at a more generous speed of 60kb/s 

leaving the rest of the adsl for myself.....this setup also ensures that if i go away for a month, the housemates will never bleed the 40gb a month quota  i have...thus keeping a constant 160kb/s potential access speed the entire month.

It is only my second week  of using squid....but  it seems like it will serve all my shaping requirements...might even be able to serve as a porn filter?

---

### Post by ingvald on 2007-07-03
Thanks for your responses to my post. 
have some questions to last reply:

- It is suggested to restrict access to Ports 135,136,137,138,139 and 445. What ports are these, what does this actually mean, and how can this be done? 

- about my network. I have one wireless router. So my "server" is a old computer wired to my router with external hard drives connected where I have all my music, videos folders "shared" on my domain.  My other laptops (running both ubuntu and windows) also have files that should be shared on this network. All my network machines have static ip adresses. Also my neighbour. When I was using only windows OS I restricted acess to all other IP adresses except for my machines. However, I felt this was unsecure since my neighbour could have changed his IP adress under TCP/IP settings in Windows,without telling me,  and possible cause a IP adress conflict if he decided to try a IP adress that I allready was using. Then I might also get access to my shared files if he guessed on one of my IP adresses, and my machine was turned off.  So I would prefer to restrict access on MAC adress and possible a combination of MAC and IP adresses.   

I am not using firestarter now, since my network is not up and running after I changed to Linux, and my server only has one network card, which I dont really want to change.,

about the "quid proxy cache. and delay buckets." I have no idea what this is...

Well.....some comments on my long reply??  :-)

---

