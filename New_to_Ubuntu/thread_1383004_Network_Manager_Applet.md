---
title: "Network Manager Applet"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-16
I accidently deleted the Network manager Icon or applet from my top menu bar. I've searched the forums and googled but I can't find how to put it back. I reinstalled Netmanager but it didn't come back. Yes I know..DUH! Thanks for any help :)

---

### Post by MarkC502 on 2010-01-16
How did you do that? Mine can be disabled etc but you cannot right click and delete it. I think maybe you set network manager to not start at bootup in the Startup Applications utility. Go to top toolbar -> System -> Preferences -> Startup Applications and make sure you have network-manager checked there :-) 

If you deleted it from that list you can choose "Add" and enter the following
Network-Manager               for the NAME
nm-applet --sm-disable       for the command
then save it and make sure its checked


Either way once you have it in that list and enabled just reboot.

---

### Post by ThePinkWitch on 2010-01-16
> **MarkC502 said:**
> How did you do that? Mine can be disabled etc but you cannot right click and delete it. I think maybe you set network manager to not start at bootup in the Startup Applications utility. Go to top toolbar -> System -> Preferences -> Startup Applications and make sure you have network-manager checked there :-) 

If you deleted it from that list you can choose "Add" and enter the following
Network-Manager               for the NAME
nm-applet --sm-disable       for the command
then save it and make sure its checked


Either way once you have it in that list and enabled just reboot.

I have no idea how it happened because I thought I was deleting an app next to it and I lost it. I had Network manager ticked to start up automatically as well. I think it might be something to do with AWN..not sure. Anyway Thankyou so much :)

---

### Post by ThePinkWitch on 2010-01-16
It didn't work. I only have the choice of applications in my applications menu. Network manager isn't one of them.  If I right click to add and type in what you told me I get some weird icon that doesn't work. I don't have any option to save either. I've done something weird to the top panel. I shouldn't have been able to delete the Network Icon. :( I have AWN installed on the bottom. Maybe thats something to do with it. How do I get the original panel back on top with the original icons or applets?  Wish I'd stop messing with stuff :D

---

### Post by spiderbatdad on 2010-01-16
network manager lives in a little spot called "notification area" on your panel. Add to panel "notification area."

---

### Post by ThePinkWitch on 2010-01-16
> **spiderbatdad said:**
> network manager lives in a little spot called "notification area" on your panel. Add to panel "notification area."

Oh cool!! Thanks :D

---

### Post by MarkC502 on 2010-01-16
I meant system startups which is in System -then-click-> preferences -then-click-> "Startup Applications".

That is where you can see what major components are starting at bootup such as printing or bluetooth etc. Network manager is listed there as well and if you uncheck it then you would no longer see the network-manager applet in your top toolbar as it would not even be loading at boot time, I thought this sounded like the most likely cause of it disapearing from the top panels notification area. Sorry to confuse :-)

---

### Post by ThePinkWitch on 2010-01-18
> **MarkC502 said:**
> I meant system startups which is in System -then-click-> preferences -then-click-> "Startup Applications".

That is where you can see what major components are starting at bootup such as printing or bluetooth etc. Network manager is listed there as well and if you uncheck it then you would no longer see the network-manager applet in your top toolbar as it would not even be loading at boot time, I thought this sounded like the most likely cause of it disapearing from the top panels notification area. Sorry to confuse :-)

Thats cool, thankyou for your help :)

---

