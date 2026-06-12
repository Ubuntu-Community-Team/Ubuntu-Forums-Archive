---
title: "No Ethernet installed"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by RandomUsr on 2008-03-09
Installed Server 7.10 and chose to configure Nic with the gui tools. I didn't know that the Gui Doesn't install by default. Hopine someone can help me get ethernet going from the BASH so that I can install Gnome from the web.

---

### Post by handydan918 on 2008-03-09
Hmmm. Shot in the dark time. 
What kind of card? 
```
lspci | grep -i net
``` will tell you.

Assuming the card is recognized, a simple ```
sudo ifconfig
``` should tell you if it has pulled an ip address or not. 
If you are getting an ip with dhcp, then ```
sudo dhclient
``` should be sufficient to request an ip address from whatever is serving them up.

---

### Post by RandomUsr on 2008-03-10
Well that's working. Now how do I install Gnome using 
apt-get?

---

### Post by handydan918 on 2008-03-12
Hmmm...have you tried ```
sudo apt-get install gnome
```

I would think apt would pull all the dependencies on its own...

---

### Post by RandomUsr on 2008-03-12
can't find package gnome

---

### Post by handydan918 on 2008-03-12
> **RandomUsr said:**
> can't find package gnome
Funny, I'm pretty sure Ubuntu uses it...:)

How about gnome-core and/or gnome-common?

---

### Post by unutbu on 2008-03-12
```

$ apt-cache policy gnome
gnome:
  Installed: (none)
  Candidate: 1:2.18.3ubuntu2
  Version table:
     1:2.18.3ubuntu2 0
        500 http://archive.ubuntu.com gutsy/universe Packages
        500 http://us.archive.ubuntu.com gutsy/universe Packages

```

Therefore, make sure 
```

deb http://archive.ubuntu.com gutsy universe
deb http://us.archive.ubuntu.com gutsy universe

```
are enabled in your /etc/apt/sources.list

---

### Post by RandomUsr on 2008-03-13
What's the command from BASH to post the /etc/apt/sources.list on pastebin?

---

### Post by handydan918 on 2008-03-14
Not familiar with pastebin, but you can create a textfile containing the contents of /etc/apt/souces.list by doing ```
cat /etc/apt/souces.list > path/and/name_of_textfile
```

---

### Post by RandomUsr on 2008-03-14
really if I knew why chmod return errors when

chmod u+x against my sources list

than I'd be good

---

### Post by handydan918 on 2008-03-14
> **RandomUsr said:**
> really if I knew why chmod return errors when

chmod u+x against my sources list

than I'd be good

I guess my big question is "Why do you want to make a text file user-executable?"
What in the world is the problem you are trying to solve?

---

