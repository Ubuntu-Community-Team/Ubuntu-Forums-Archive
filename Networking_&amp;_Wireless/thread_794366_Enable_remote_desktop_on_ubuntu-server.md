---
title: "Enable remote desktop on ubuntu-server"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by halloiz on 2008-05-14
Hi!

I have a new server that i have no physical access to, only ssh enabled (commandline access). Now i need to connect to it with remote desktop. I have used NoMachine NX client for windows before (on another server), but i'm having a struggle connecting to this new server.
I think everything has been installed on the server correctly, but when i type:
```
sudo /usr/NX/bin/nxserver --start
```
I get this message:
```
NX> 595 ERROR: Detected an inconsistency in the NX server configuration.
NX> 595 ERROR: The exception id is: 079FF53D. To get detailed information about
NX> 595 ERROR: the error, search for the string: 079FF53D in the system log file
NX> 595 ERROR: (usually '/var/log/messages').
```

Any help would be gratefully appreciated. I'm still a n00b when it comes to ubuntu (and unix/linux in general) so bear with me please.

:)

---

### Post by Monicker on 2008-05-14
What shows when you search for 079FF53D in /var/log/messages?

---

### Post by vorgusa on 2008-05-14
What GUI do you use, gnome, KDE, or XFCE?

---

### Post by halloiz on 2008-05-14
I guess gnome is what is installed, but does that even matter as i'm not able to see anything but the terminal?

How do i search in that log? I said i was a n00b, and it was not a lie:razz:

---

### Post by Nampla on 2008-05-14
if you installed Ubuntu server by default you dont have any GUI. In other words you cant use NX until you install either gnome, kde, or another GUI supported by Nomachine.  You probably should stick to the terminal if you can for a server.  I have a similar set up and mapped the ports thru my router and set up one of my terminals at the same location as my server.  This terminal runs the desktop version of Ubuntu and therefore can use NX. I do this if i need a GUI and then ssh over to the server and am able to run gui applications over ssh on the lan. THis for me works better than trying to run an X program over the web. 
Good luck

---

### Post by halloiz on 2008-05-15
I think i installed gnome.
And since i'm in a hurry getting this server up and i don't know much about ubuntu yet, i think i'm gonna need a GUI.
If anyone is interested in setting up the NX server on my server and creating a user for me (so i can connect from my windows os using NX client), let me know. And you'll get 10$ (through PayPal) for the job - should not be much of a job if you know ubuntu i think. Less than 10mins probably.

---

### Post by halloiz on 2008-05-15
Bump...

Anyone?

---

### Post by Nampla on 2008-05-15
why dont you just install the desktop version of ubnutu instead.  You can have virtually all the features of a server and a GUI by default.  Otherwise look at OpenSusue 10.3 the server has a GUI installed by default either KDM or GNOME. I think that is your best bet. Even if I were to set it up you still need to know how to admin the system.  You might as well get your education now.

---

### Post by halloiz on 2008-05-15
You see, this is a server i'm renting and i can not change the OS on it. I have used ubuntu desktop (7.10 & now 8.04) on my laptop for like half a year now so i'm not totally new to ubuntu (i know how to manage it if i have a GUI), but i'm not very good working with terminal (yet).
And since i'm renting this server i want to get it up and running as soon as possible, in other words; no time for me learning how to use ubuntu without GUI. I'll have to learn that later;-)

Please let me know if you can help me out, i'd very much appreciate it.

Regards:-)

---

### Post by Nampla on 2008-05-16
I might be able to.  It depends on what your doing.  Message me what your doing with that server.

---

### Post by gutistef on 2008-11-28
Hi my friend,

did u find something for your error with NX NOMACHINE??

I have the same than you....

NX> 595 ERROR: Detected an inconsistency in the NX server configuration.
NX> 595 ERROR: The exception id is: 8B01065F. To get detailed information about
NX> 595 ERROR: the error, search for the string: 8B01065F in the system log file
NX> 595 ERROR: (usually '/var/log/messages').
NX> 280 Exiting on signal: 15

and don't know what i have to do...

I explain to you, i was able to use NXSERVER during few days and today i met some problemes. I decided to remove the last version and re-install the new one version of nxnode and nxserver. I'm on Ubuntu 8.04.
And when i make:

# sudo /usr/NX/bin/nxserver --stop

i have this error or when i try to connect to nxserver with my nxclient for windows i have the same error.

Did you find something interesting..??

To make my tests i am connected via Putty (ssh).

But in shell it's difficult, i prefere the Xserver.

Thanks you for your help..it's welcome!!

---

### Post by kdude63 on 2010-11-06
Failpost someone tell me how to delete. GRR.

---

### Post by kdude63 on 2010-11-06
[B][FONT="Arial"][SIZE="2"]You can get a GUI in Ubuntu Server but it requires that you basically turn it into the desktop edition. It doesn't need reinstalling or anything, but in the terminal type

[/B]```
sudo aptitude install (distro)-desktop
```[B]
Replacing (distro) with the release that you want to use, IE if you want the XFCE desktop (Which I would recommend, because it's the fastest.) you replace it with xubuntu, or kubuntu for KDE, or just ubuntu for Gnome.

 So you should understand now that Ubuntu Server and Ubuntu Desktop are exactly the same, except that Desktop has a GUI and some extra packages.[/SIZE][/FONT][/B]

Note: I have no Idea if this ended up in the right place or not. I HATE FORUMS! They are so damn confusing...

---

### Post by kdude63 on 2010-11-06
> **halloiz said:**
> You see, this is a server i'm renting and i can not change the OS on it. I have used ubuntu desktop (7.10 & now 8.04) on my laptop for like half a year now so i'm not totally new to ubuntu (i know how to manage it if i have a GUI), but i'm not very good working with terminal (yet).
And since i'm renting this server i want to get it up and running as soon as possible, in other words; no time for me learning how to use ubuntu without GUI. I'll have to learn that later;-)

Please let me know if you can help me out, i'd very much appreciate it.

Regards:-)
[B][FONT="Arial"][SIZE="2"]You can get a GUI in Ubuntu Server but it requires that you basically turn it into the desktop edition. It doesn't need reinstalling or anything, but in the terminal type

[/B]```
sudo aptitude install (distro)-desktop
```[B]
Replacing (distro) with the release that you want to use, IE if you want the XFCE desktop (Which I would recommend, because it's the fastest.) you replace it with xubuntu, or kubuntu for KDE, or just ubuntu for Gnome.

 So you should understand now that Ubuntu Server and Ubuntu Desktop are exactly the same, except that Desktop has a GUI and some extra packages.[/SIZE][/FONT][/B]

Note: Sorry if this is multipost. I dont know my way around the forum yet...

---

