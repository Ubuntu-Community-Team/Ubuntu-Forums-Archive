---
title: "Gedit/Networking problem"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by kunnie on 2009-02-24
Ok, absolute noob here. I´ve just installed Ubuntu in my brand new laptop, and for my surprise, my wireless card was suppored! However, since, acording to what I´ve been told, the network manager is useless (because of a subnet mask problem), I resorted to [a guide I found]("http://www.ubuntu-es.org/index.php?q=node/104418"), in spanish,  about setting a wireless lan (static IP) "manually", messing with the conf files and whatnot.

However, when I try to edit them and save them, the terminal I was using says:

** (gedit:7404): WARNING **: Could not write gedit state file: there has been an error while trying to create the file <</root/.gnome2/gedit-2.7B82PU>>: No suc file or directory

I/O error: No such file or directory
I/O error: No such file or directory

Can anyone help me to either fix my wireless conection or fix my gedit problem?

BTW, if you need help reading the guide, I´m a native spanish speaker, so ask away :lolflag:

---

### Post by alinuxfan on 2009-02-24
You should be able to right-click on the network icon and "edit connections."  From there, click on the "wireless tab" 

Then click on Auto_(Your_Connection_Name) and click 'edit'

then click 'IPV4 settings'

There you can change the dropdown box from 'DHCP' to 'Static'

When entering IP, Subnet, and Gateway, make sure you click in the box again after putting in the last one, I always have issues with it not storing the last one unless I click just underneath it

Enter your DNS (or opendns: 208.67.222.222,208.67.220.220) and hit ok

You might have to left click on the network manager applet and reconnect to your wireless

(I think that is how you do it, I am at work on a Windows computer)

I will check back when I get home

What version of Ubuntu are you using? IN 8.10 network manager is working very well.

What are your subnet mask problems?

---

### Post by kunnie on 2009-02-24
Gee, the problem is just that instead of 255.255.255.0, it goes to 24... Its so freaking frustating!! ]Anyways, I purged the regular network manager, so can you tell me how to get it back so I can try and do what you said?

BTW, my IP address and my gateway dont change, just my subnet mask

---

### Post by kunnie on 2009-02-25
Can anyone help me? I just need to set up a static wireless connection with my router so I can download another network manager.

---

### Post by superprash2003 on 2009-02-25
here.. hope this helps [http://ubuntuforums.org/showthread.php?t=1080272](http://ubuntuforums.org/showthread.php?t=1080272)

---

### Post by kunnie on 2009-02-25
> **superprash2003 said:**
> here.. hope this helps [http://ubuntuforums.org/showthread.php?t=1080272](http://ubuntuforums.org/showthread.php?t=1080272)
Its another of my own threads :lolflag:

---

### Post by superprash2003 on 2009-02-26
oops.. that didnt work?? what error is it giving?

---

