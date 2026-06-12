---
title: "Updating ubuntu locally using ftp"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by shankhs on 2009-08-22
Due to high cost of internet I have only one system connected to the net,and other 10 systems are standalone(not connected to internet).
The main problem I am facing is update and upgrade of offline ubuntu boxes.So I decided to make an ftp repo in my online ubuntu box which will download the updates from ubuntu servers and add the online box to the software sources of the offline boxes.
I am unable to decide how to do this!!!
Which ftp server to use?
How to make a repo?
Please help.

---

### Post by zvacet on 2009-08-22
Read [this]("https://help.ubuntu.com/community/Apt-Cacher-Server") and see is it of any help to you.

---

### Post by shankhs on 2009-08-22
thanx zvacet.
The apt-cacher is pretty ubuntu-specific.
I am looking for something more general , like how to make ubuntu updates repo in a suse machine or a windows machine.
Then I wouldn't have any problem if the machine (connected to internet) changes.
Any idea?
Thank you.

---

### Post by k3lt01 on 2009-08-22
I would have suggested [this]("http://ubuntuforums.org/showthread.php?t=352460"). Because you are in effect mixing systems I think you'll need to ask on other forums as well because I have no idea how other versions of Linux (non-Debian based) update themselves nor even if you would be able to setup a "mixed" repository.

---

### Post by zvacet on 2009-08-22
> The apt-cacher is pretty ubuntu-specific.

Yes,bnecause you told me that 

> The main problem I am facing is update and upgrade of offline ubuntu boxes.

I don´t know how will it be wit h mixed repos.

---

### Post by shankhs on 2009-08-23
What an irony!
Ubuntu,suse,fedora are all linux but still so different.
I searched the whole web fanatically but of no use couldn't get a single website that explains how to build a ubuntu repo in suse or fedora or any other linux.
Anyways thanx guys.If I get anything meaningful I will let u know.

---

### Post by inobe on 2009-08-23
give that a try

[http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/](http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/)

i see this has been mentioned, it's something commonly utilized' confused a bit.

edit: lets start with .debs for debian based os compared to windows .exe or even opensuse .rpm's , they are all different in their own way !

---

### Post by shankhs on 2009-08-23
thanx inobe.
I see the difference but dont you think all linuxes should be interoperable?
Anyways I am trying to set the apt-cacher.

---

### Post by EXCiD3 on 2009-08-23
Check out [Keryx]("http://keryxproject.org") for updating offline machines. It's very useful and is cross platform so you can grab updates and new packages for offline machines on just about any computer. :)

---

### Post by shankhs on 2009-08-26
Thanx excid3
Keryx is helpful if you want to transfer updates using pen drive(USB drives).
I am searching for a software ( like a server client) which when installed in an online system fetches the updates and the offline systems can download update using this system in LAN.
Anyways I am currently using Keryx and simultaeneously exploring the source code . I hope that I can change it to something that I want.

---

### Post by EXCiD3 on 2009-08-26
I think the best way you could do it would be to mount the /var/cache/apt/archives folder over the LAN for each system and that way the online machine would download the packages once and the offline machines would have immediate access to that. You'd have to probably also do the lists folder so they could get a list of the most up to date packages (and know about the updates).

If you have any code changes you'd like help on or ideas, you should drop by our IRC channel in freenode (irc.freenode.net #keryx) and discuss it with us. We'd be glad to help you on it and probably include the feature in a new release. :)

---

