---
title: "pidgin updates"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by DarinB on 2009-08-14
i tried to add this from the pidgin web site but it doesn't respond says conflict and doesn't seem to respond. am i just asking for trouble?????? or what?????
[B]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list[/B]

---

### Post by Tibuda on 2009-08-14
I think the it has something to do woth those bars without newlines. Try removing the bars:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```
Can you post the whole message you got?

Alternatively you can download the packages from getdeb: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

---

### Post by colau on 2009-08-15
> **danielrmt said:**
> I think the it has something to do woth those bars without newlines. Try removing the bars:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```
Can you post the whole message you got?

Alternatively you can download the packages from getdeb: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)
Problem is solved!

---

### Post by Tibuda on 2009-08-15
> **colau said:**
> Problem is solved!

Good. What have you done, the PPA or GetDeb?

---

### Post by colau on 2009-08-15
> **danielrmt said:**
> good. What have you done, the ppa or getdeb?
ppa.

---

### Post by DarinB on 2009-08-15
do i use this code or do i have to do something else not sure what bars you are talking about??????

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

---

### Post by colau on 2009-08-15
Copy and paste those two commands.

---

### Post by DarinB on 2009-08-15
i did but not sure what is supposed to happen?
I am at pidgin 2.5.5 no upgrades appeared. how can i check if the ppa is there???

---

### Post by colau on 2009-08-15
> **DarinB said:**
> i did but not sure what is supposed to happen?
I am at pidgin 2.5.5 no upgrades appeared. how can i check if the ppa is there???
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
sudo aptitude update
sudo aptitude install pidgin

```

---

### Post by DarinB on 2009-08-15
In Software sources i have the pidgin key but not the ppa??? here are some screen shots
[ATTACH]124989[/ATTACH]

[ATTACH]124990[/ATTACH]

[ATTACH]124991[/ATTACH]

---

### Post by colau on 2009-08-15
You can also get pidgin 2.5.8 from [http://www.getdeb.net/release/4509](http://www.getdeb.net/release/4509)

---

### Post by DarinB on 2009-08-15
well i did what was above but the PPA did not add but i found this in the forum

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main

and added it to the sources list and it upgraded my pidgin to 2.5.8 easy not really, kind of a pain. i could never get anyone else to go through this.

---

### Post by Tibuda on 2009-08-15
When you manually add a PPA to /etc/apt/sources.list.d/ instead of /etc/apt/sources.list (like the command in the Pidgin website do), it will not show in the software sources GUI, but you'll be able to download/update packages from the PPA.

---

