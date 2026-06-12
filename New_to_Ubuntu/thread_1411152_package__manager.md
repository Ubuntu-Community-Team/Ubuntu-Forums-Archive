---
title: "package  manager"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by marcus1978 on 2010-02-19
hi im totally new to ubuntu i have ubuntu 9.10 and in the synaptic package manager it says this

[FONT=monospace]W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_karmic_partner_binary-i386_Packages)

synaptic wont work how can i fix it? 
[/FONT]

---

### Post by cogier on 2010-02-19
Marcus,

Have a look here System>Administration>Software Sources. Click on the "Other Software" tab and make sure you have no duplication of entries. If so remove them.

I'm not sure that this is your problem but it's worth a look.

---

### Post by theaaronc on 2010-02-19
You can check to see if your sources.list has an duplicate entries. Just make sure you make a backup before making any changes to the file:

$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.BAK
$ gksudo gedit /etc/apt/sources.list


If you can't find any duplicates, in the link listed below it looks like running the following command worked for a few folks as well:

 sudo apt-get clean

 [http://ubuntuforums.org/archive/index.php/t-262592.html](http://ubuntuforums.org/archive/index.php/t-262592.html)

---

