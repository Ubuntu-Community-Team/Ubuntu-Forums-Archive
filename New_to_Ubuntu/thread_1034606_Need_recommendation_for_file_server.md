---
title: "Need recommendation for file server"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by NorStarTech on 2009-01-08
Ok all you beautiful tech people, I need some advice and maybe a little help.  My mortgage company was using a Windows XP box as a file server for a couple of years now, but our growth has caused something of a problem.  I have learned that Windows XP will only allow up to 10 other computers to connect to it, not good for our staff of 14.  I was looking at Ubuntu as a possible replacement.  I have never touched a Linux program before, so I have a couple of questions:

1) Will Ubuntu Desktop allow up to 15 connections so I can use it to share some folders across a network?

2) I downloaded and installed the Server version, but the lack of GUI is a bit scary.  I feel my situation is a bit minor, but if I could get some direction on how to copy and share my files on the server I believe I could handle it.  Is this overkill?

Just a heads up, I have already tried a NAS box, but the mortgage software we use doesn't like the file structure of the NAS's that I have used.

Please advise on what you would do in this case.  Thanks!

---

### Post by tuxxy on 2009-01-08
> **NorStarTech said:**
> 
1) Will Ubuntu Desktop allow up to 15 connections so I can use it to share some folders across a network?

2) I downloaded and installed the Server version, but the lack of GUI is a bit scary.  I feel my situation is a bit minor, but if I could get some direction on how to copy and share my files on the server I believe I could handle it.  Is this overkill?

Just a heads up, I have already tried a NAS box, but the mortgage software we use doesn't like the file structure of the NAS's that I have used.

Please advise on what you would do in this case.  Thanks!

1. Yes providing you have sufficent bandwidth to operate with a 15 user volume.

2. If you prefer a GUI to work from you can install GNOME on the server version with the following command
```

sudo apt-get install ubuntu-desktop
```

Here you can take a look at what comes with ubuntu-desktop package and once installed you will have a graphical login also.

[http://packages.ubuntu.com/intrepid/ubuntu-desktop](http://packages.ubuntu.com/intrepid/ubuntu-desktop)

---

### Post by albinootje on 2009-01-08
> **NorStarTech said:**
>  1) Will Ubuntu Desktop allow up to 15 connections so I can use it to share some folders across a network?

Short answer : with Linux the sky is the limit.
> 
2) I downloaded and installed the Server version, but the lack of GUI is a bit scary.  I feel my situation is a bit minor, but if I could get some direction on how to copy and share my files on the server I believe I could handle it.  Is this overkill?

Having a GUI on your Ubuntu server as a beginner is fine.

An important question imho is : 
Are you using a Primary Domain Controller right now ? 
Or more simple : Are your Windows-clients logging on locally or on some Windows domain ? 
Or perhaps you have no idea ?

You have a few choices :
1) Set up Samba on your server, and forget about PDC
2) Set up Samba + PDC without LDAP
3) Set up Samba + PDC with LDAP

LDAP is pretty complex, let's skip that for now.
The easiest on the server side is to install Samba without PDC setup, and leave it at that.
That's more work on the clients, because then it makes sense to make a batch file for each user in their AutoStart directory to connect to the shares.

Have a quick look here :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
and install this on your samba server :
```

sudo apt-get install system-config-samba

```
After installation of that GUI for samba, go here :
-> System -> Administration -> Samba

---

### Post by NorStarTech on 2009-01-08
Wow, thanks for the quick reply!

We just use a simple Windows workgroup, security is not an issue.  Bandwidth is also not an issue, the files that are being shared are less than 5 KB and not constantly accessed.

I do have a question, how do I join my new fangled Ubuntu box to the Windows workgroup?  I thought I looked over all the documentation and I am coming up empty.

Thanks again!

---

### Post by albinootje on 2009-01-08
> **NorStarTech said:**
>  I do have a question, how do I join my new fangled Ubuntu box to the Windows workgroup?  I thought I looked over all the documentation and I am coming up empty. 

Just make sure that the "workgroup" in /etc/samba/smb.conf is the same workgroup name.
In the earlier mentioned samba GUI you can edit the workgroup too.

---

### Post by NorStarTech on 2009-01-08
When I try to save my changes in the smb.conf I get a warning saying "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." Help please?

---

### Post by perlluver on 2009-01-08
> **NorStarTech said:**
> When I try to save my changes in the smb.conf I get a warning saying "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." Help please?

Are you typing sudo before the edit command?  That will allow you to modify system files.

---

### Post by albinootje on 2009-01-08
> **NorStarTech said:**
> When I try to save my changes in the smb.conf I get a warning saying "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." Help please?

```

sudo gedit /etc/samba/smb.conf   (in the GUI)
or
sudo nano /etc/samba/smb.conf    (in the CLI)

```

---

### Post by DGortze380 on 2009-01-09
May I suggest you continue to learn how to configure the new linux server, attach it to your network with a new static IP, and put it through a trial period before doing anything drastic to your windows box. we all kinks are worked out, switch full time to the new server.

Linux is an awesome and powerful tool that can definitely do what you want it to. But it's a bit of a learning curve, and it's always a bad idea to switch mission-critical components to any new device/system if you're not yet comfortable with it's operation.

---

