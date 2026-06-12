---
title: "PPA help"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Visvalor on 2011-04-27
Hey, I opened terminal and added sudo apt-get repository ppa:pmcenery/ppp


Unfortunately as you can see I put ppp so it's fjdsjfkdsjn'd up. 

I used gksudo gedit /etc/apt/sources.list to edit where I thought this problem would be located, but it's not.

When I type sudo apt-get update I get this (obviously);


W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppp/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/pmcenery/ppp/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppp/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pmcenery/ppp/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found


WHERE do I go to find the stupid PPP so I can change it to PPA and have this problem fixed?

Thanks for any help.

~Vis

---

### Post by falko on 2011-04-27
Did you check the /etc/apt/sources.list.d/ directory?

---

### Post by Visvalor on 2011-04-27
They are in there, but how do I delete them? I have the proper ones also there in ppa form.

---

### Post by itisbasi on 2011-04-27
Go to synaptic>settings>repositories>other software tab, here you will see a list of all your extra repositories including the wrong ppa, you could remove it...

---

### Post by bodhi.zazen on 2011-04-27
You can also :

```
gksu gedit /etc/apt/sources.list
``` and edit them directly =)

---

