---
title: "How can I easily share files and folders?"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2008-08-13
Simple question. What is the best way to share files and folders across my home network? I have three computers  through a router, all dual booting a flavour of Windoze and a flavour of Ubuntu. I want to be able to access the EXT3 and FAT32 drives on the computers in Ubuntu as my network already understands the Windoze setup (including in Ubuntu:Places->Network->Windows Network).

In Windoze things seemed to setup pretty easily, but the option I am looking at is setting up a samba server. Do I really need to do that to do this? Or smbfs?

I've have heard ssh could be a possiblity. How difficult/easy is this and is there a GUI to work with or terminal?

Here's hoping for some responses and thanks in advance ...

---

### Post by tamoneya on 2008-08-13
just setup samba in all the ubuntu installations.  Samba will be able to be read from windows and linux so it seems to fit nicely.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Bucky Ball on 2008-08-13
> **tamoneya said:**
> just setup samba in all the ubuntu installations.  Samba will be able to be read from windows and linux so it seems to fit nicely.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Thanks for that, but do I take it to mean I need to set up a server; ie one of the machines is the server and needs to be on for the set up to work? Or do I set them all up as servers?

Having another look at that page, I think that is what I am getting at ... :)

---

### Post by tamoneya on 2008-08-13
any computer that has files on it that you want to share should be set up as a server.  Then whenever that computer is on you will be able to browse it across the network.  You could make just one central server and store all your files there which has the benefit of being able to access all your files even if some of your computers are off.  Its really your choice on how you set it up.  However if you go with the second option realize that you are probably going to want that computer to be on 24/7 as well as have a lot of harddrive space.

---

### Post by Bucky Ball on 2008-08-13
>  on 24/7

Yea, I have no need for a 24/7 machine and slowly trying to convert the hardware to more energy efficient in all of them. Does setting up a server like this drain resources severely or any other hidden surprise in performance?

---

### Post by tamoneya on 2008-08-13
its very lightweight.  You wont even notice the load difference.  It will be sleeping most of the time anyways.  Even when it is utilized CPU load will be low.  It may take longer for disk IO if you are pulling stuff across the network at the same time.

---

### Post by Bucky Ball on 2008-08-13
Fine. Thanks for that, I think you have answered my questions regarding samba setup. I'll give it a go tomorrow and post again if I have any probs.

Cheers! :)

---

