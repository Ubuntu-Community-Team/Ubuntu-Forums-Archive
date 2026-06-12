---
title: "problem with connecting to wireless"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by fiocook on 2010-10-12
Dear All, this is my first post. 
 
My boyfriend installed Linux / ubuntu on my PC (which is a zoostorm freedom netbook) a month ago, and he had to do some research to get the wireless working at first, but it was working like a treat for a month. however, then i installed some updates and now it's not working, and i'm working overseas so i can't ask my boyfriend to fix it again!
 
I don't know what version of ubuntu i'm using or how i find this out (the set up menu says ubuntu 2.6 32-25 generic but i don't think this is the version). 
 
My boyfriend suggested a few commands but they don't work. He also referred me to his original posts (on the french ubuntu forum') but i wasn't able to make sense of it all! 
 
I saw that to find out if there is wireless connection you should put in 
[SIZE=3][FONT=Times New Roman]iwconfig to the control panel, when i do this it replies [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]lo no wireless extensions.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]eth0 no wireless extensions.[/FONT][/SIZE]
 
 
[SIZE=3][FONT=Times New Roman]I am trying to connect to a wireless network (but it's somewhere in the building and i can't hook up with the wire) called Linksys (802.11) which I can access with Windows. [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]As I say it was working before so it seems the update has uninstalled something my boyfriend did. Can anyone help? If you could take me through it step by step that would be great, bearing in mind that I can't configure it in ubuntu itself for the moment but can save things on my USB stick to type into the control panel.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Many thanks in advance[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Fiona[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Many thanks in advance[/FONT][/SIZE]

---

### Post by scrooge_74 on 2010-10-12
At first glance your wifi card is not working, first try the key combinations that start and stop your wifi. Sometimes this happens (never figure it out)

On a terminal also type lspci so you can post what type of wifi chip you have

---

### Post by anewguy on 2010-10-12
To get a whole lot of information to help us, please do the following and post the outputs back here:

lspci

lshw -C network

iwconfig

ifconfig

lsusb

That should give us plenty to start helping you!

Dave ;)

---

