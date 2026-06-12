---
title: "the default firewall of fedora installed in ubuntu.is this possible?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-22
i was surfing around the net when i stumbled to a wiki about fedora's firewall..
as a newbe im not a power user or something like that but i found very nice nad i think its a frontend for iptables(but im not sure) 
is this available on the repos?

---

### Post by 67GTA on 2009-07-22
Not sure what Fedora uses, but you can try firestarter, or even easier is gufw. They are both in the repos.

---

### Post by Durden on 2009-07-22
> **heyyy said:**
> i was surfing around the net when i stumbled to a wiki about fedora's firewall..
as a newbe im not a power user or something like that but i found very nice nad i think its a frontend for iptables(but im not sure) 
is this available on the repos?

[http://www.techotopia.com/index.php/Basic_Fedora_Linux_Firewall_Configuration](http://www.techotopia.com/index.php/Basic_Fedora_Linux_Firewall_Configuration)

Seems like its using something custom for its basic config and offers Firestarter for the more complex stuff, which is also available in Ubuntu.

---

### Post by heyyy on 2009-07-22
> **67GTA said:**
> Not sure what Fedora uses, but you can try firestarter, or even easier is gufw. They are both in the repos.

yes im aware of both
im with firestarter now but i really liked the other one from screenshots i saw
i think its called "system-config-firewall"

---

### Post by heyyy on 2009-07-22
> **Durden said:**
> [http://www.techotopia.com/index.php/Basic_Fedora_Linux_Firewall_Configuration](http://www.techotopia.com/index.php/Basic_Fedora_Linux_Firewall_Configuration)

Seems like its using something custom for its basic config and offers Firestarter for the more complex stuff, which is also available in Ubuntu.

oups sorry ive seen your post

---

### Post by 67GTA on 2009-07-22
You could try to download an rpm and convert it to deb with alien.

[http://rpm.pbone.net/index.php3?stat=3&search=system-config-firewall-tui&srodzaj=3](http://rpm.pbone.net/index.php3?stat=3&search=system-config-firewall-tui&srodzaj=3)

---

### Post by ibutho on 2009-07-22
The app will probably work with Ubuntu, but some changes may need to be made in order for it to work properly. System-config-printer (The printer config and admin tool) which is used in Ubuntu was ported from Fedora.

---

### Post by ajgreeny on 2009-07-22
You may not need to install a firewall configuration application unless you are running a server of some sort.  A stand-alone desktop running normal desktop applications that use the internet/network, such as firefox and thunderbird, etc etc, will probably be perfectly safe behind the default iptables, which you are correct, is the actual firewall in ubuntu.

---

### Post by heyyy on 2009-07-22
> **ajgreeny said:**
> You may not need to install a firewall configuration application unless you are running a server of some sort.  A stand-alone desktop running normal desktop applications that use the internet/network, such as firefox and thunderbird, etc etc, will probably be perfectly safe behind the default iptables, which you are correct, is the actual firewall in ubuntu.

yes but although iptables are installed by default in ubuntu they are not set up(at least i think so) ,so you have to set by yourshelf,,,right?

---

### Post by sisco311 on 2009-07-22
> **heyyy said:**
> yes but although iptables are installed by default in ubuntu they are not set up(at least i think so) ,so you have to set by yourshelf,,,right?

yep, but the real question is that *do you need a firewall?*

---

