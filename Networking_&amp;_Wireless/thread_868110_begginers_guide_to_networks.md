---
title: "begginers guide to networks"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by petegreenhorn on 2008-07-23
hi , could anyone point me to a guide/help to networks , i'm trying to set up 
my 3 machines so that they can share and exchange files etc. any help appreciated

---

### Post by aeon on 2008-07-23
if you just want to share files between the computers then 3 machines aren't that hard to set up, if you have a router just put static ips on the machines (router side based on the mac of the comps, or then on the computers themselves) after that just install a ssh server (eg. OpenSSH) on the machines and you're all set.

if you want you can tweak your /etc/hosts file so that it's easier to ssh to the other computers..

---

### Post by petegreenhorn on 2008-07-23
thanks for the reply , but that just didn't help me much , as i am totally new to this . if you're in a position to help me out then here is where i'm upto . i have 3 machines connected to a router and i don't know how to get any further

---

### Post by Iowan on 2008-07-23
If they're all Ubuntu machines, you have several options - SSH, NFS, Samba to name a few.  [This]("http://ubuntuforums.org/showthread.php?t=866546") thread has a response by DMIZER.  His(?) signature has several links  (for FTP, NFS, Samba), - one of which may be helpful.  [https://help.ubuntu.com/]("https://help.ubuntu.com/") also has some topics on networking. 
... or you can get answers to specific questions here. :)

---

### Post by aeon on 2008-07-23
I'm assuming that all the computers are running some sort of linux here, otherwise you might want to have a look at samba (SMB)
I haven't used it or set it up so google or searching the forum helps you more there..

A howto for setting up openssh can be found [here.]("https://help.ubuntu.com/7.10/server/C/openssh-server.html")
it's for gutsy but it should be the same for hardy aswell.

now, if you want you can set up static ips on the router, but there's some problems sometimes so the easiest would be to just put a static ip on all the computers, [this]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html") is a good guide how to do that using the GUI.

when you're done with that you can edit the /etc/hosts file with
```
sudo gedit /etc/hosts
```
there just add the ip adresses of the other computers and the hostnames of those computers.

like this:
```

IPAddress               Hostname    		 Alias
127.0.0.1		 localhost	 	 
192.168.0.1		 hostname of comp 1       comp1
192.168.0.2             hostname of comp 2       comp2
192.168.0.3             hostname of comp 3       comp3

```           

you can change the alias to what you like but the hostname needs to be the same as the hostname that is in /etc/hostname on the other computers

when you're done editing the hosts file you can just copy it over to the other computers.

to update the network just do
```
sudo /etc/init.d/networking restart
```


after this you should be able to ssh to the other computers using
```
ssh user@host:portnumber
```

portnumber is the port that you defined when setting up openssh, it defaults to 22 if you don't change it

to easily exchange files just hit ctrl-L in nautilus and type in
```
ssh://user@host
```

you can also put shortcuts on the desktop by going to "Places -> Connect to server..." and just fill in the info there


hope this helps a bit :)

---

