---
title: "google earth install"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by amitpokhrel on 2010-11-06
can anyone tell me how can I install google earth on my system using terminal.

---

### Post by I'mGeorge on 2010-11-06
> **amitpokhrel said:**
> can anyone tell me how can I install google earth on my system using terminal.

You have the regular i386 Ubuntu or the Ubuntu x86_64 ? Because the installation of Google Earth varies according to the architecture you have.

---

### Post by sikander3786 on 2010-11-06
You can simply download it here.

[http://www.google.com/earth/index.html](http://www.google.com/earth/index.html)

Alternatively,

[https://help.ubuntu.com/community/GoogleEarth#Alternative%20%20Installation](https://help.ubuntu.com/community/GoogleEarth#Alternative%20%20Installation)

Any specific reason behind installing from terminal?

---

### Post by amitpokhrel on 2010-11-06
i have ubuntu x86-64

---

### Post by I'mGeorge on 2010-11-06
> **amitpokhrel said:**
> i have ubuntu x86-64

Than the first thing you have to do it's to open synaptic, and in your search box type ia32 

Install the following packages

ia32-libs
ia32-libs-dev
ia32-libs-gtk

After that go to google earth main site [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html) and download the .bin file. You could try execute the bin file just licke in windows with a left mouse button double click. If it doesn't work open a terminal, put the path to the folder where you have downloaded your googleearth.bin file "cd /path_to_your_bin" followed by the commands 

chmod a+x googleearth.bin
./googleearth.bin

Do this as a normal user, you don't have to be root to install it and it's actually not recommended to install GE as root.

---

### Post by amitpokhrel on 2010-11-06
thanks

---

