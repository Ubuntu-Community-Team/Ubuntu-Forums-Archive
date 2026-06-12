---
title: "mythfrontend installation"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2009-01-07
Ok I am new to Ubuntu and I am using 8.10 64-bit. I am installing myth tv on another computer which is ubuntu server 8.04 32-bit. However that is not the problem. I want to be able to install just mythfrontend on my 8.10 so I can use the 8.04 server as a backend. How do you install mythfrontend on ubuntu 8.10? I know this may be a stupid question, but plz don't yell at me!

---

### Post by nevernamed on 2009-01-07
Read the instructions?

---

### Post by Indian_Guy101 on 2009-01-07
like I said I am pretty new to Ubuntu I kind of fast read the instructions and I found nothing related to Ubuntu or even Debian. I only found Fedora and Manriva instructions. So is there a single termainal command I can use or something (Go ahead yell at me you will feel better)

---

### Post by fenian on 2009-01-07
Install mythbuntu-conrol-centre from synaptic or enter in terminal...

> sudo apt-get install mythbuntu-control-centre

Then open it from the menu; System>Administration>Mythbuntu Control Centre
Click on System Roles and check the Frontend Box
Click apply and it will install the required packages.

---

### Post by Indian_Guy101 on 2009-01-10
So if I weere to do that, the next time that i start Ubuntu it won't automatiically start the frontend right because I don't want it to. I still want to be able to use the computeer the way I do now, only with the option to run mythfrontend so I can connect to my seperate backend.

---

### Post by fenian on 2009-01-14
> **Indian_Guy101 said:**
> So if I weere to do that, the next time that i start Ubuntu it won't automatiically start the frontend right because I don't want it to. I still want to be able to use the computeer the way I do now, only with the option to run mythfrontend so I can connect to my seperate backend.

In the conntrol centre under Artwork and Login Behavior,uncheck the box next to Automatically start Mythtv standalone session upon boot and Ubuntu will start as normal and you can launch Mythtv Frontend from the Applications>Sound and Video menu.

---

