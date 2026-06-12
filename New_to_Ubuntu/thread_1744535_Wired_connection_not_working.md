---
title: "Wired connection not working"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by PZJM on 2011-04-30
Hey folks, I'm experiencing a strange situation.  2 days ago I ran the Ubuntu Updates (did not upgrade to 11.04) and everything was working fine.  The next day I had not internet connection.  I checked the back my computer and there was not light at all for the ethernet connection.  I'm not sure how to trouble shoot something like this.

Either my new motherboard has crapped out or the update screwed with my ethernet settings. How does one go about troubleshooting something like this?  Oh, by the way I am still able to access the internet via my wireless laptop.  So, my router is ok I'm just not sure if it's a motherboard issue or an update that screwed with my settings.  Any help would be greatly appreciated.

Thanks.

---

### Post by user333 on 2011-04-30
Can you load a Live CD and see if that connects? If it does, it may mean the problem is with the computer.

---

### Post by cavalier911 on 2011-04-30
No light on the ethernet adapter means no carrier signal between the adapter,the ethernet cable and switch,hub,accesspoint,cable/dsl modem it's connected to. Anyone of those things could be the problem if it's a hardware issue. I've had the ethernet ports go out in a Linksys wireless router and the wireless still worked.I'd power the router off and on and the ethernet ports would work for a few days and then die.
If the live cd doesn't work and your laptop has a working ethernet adapter substitute it for computer that won't connect. If it's ethernet signal light comes on and it connects you've verified everything as good except the computer.You may have to poweroff/on your modem to get it to give your laptop an ip address.
If you can't get it working specific information on what hardware you have between this computer and the internet will be needed.

---

### Post by PZJM on 2011-04-30
Live CD did not work.  So, am I safe to assume that my 2 month old motherboard has a problem with the ethernet port?  How do you troubleshoot something like that or should I just contact the manufacture?

---

### Post by JayKay3OOO on 2011-04-30
I had problem like this, erm. But.. it was only when going between w7 and ubuntu.

Anyway. Does your pc have a switch for the power supply unit? Try turning this off for 30 or so seconds and back on. Pull out and put in your ethernet cable too.

This used to work for my Asus motherboard (till I dropped the windows!)

Try a diff ethernet cable also to be sure.

Also try another Linux distro or Windows (if you have) to see if it fails in these too because then you can say it's mobo for sure. Just run a live CD should be enough.

Theoretically, assuming your ethernet adaptor is compatible with ubuntu it will either work or it won't (in most cases)

I would be highly surprised if the motherboard ethernet has blown up, but stranger things have happened.

---

### Post by cavalier911 on 2011-04-30
Open terminal:
```
lshw -C network
```
Does it list the network adapter?
```
ifconfig
```
Is your ethernet adapter listed?
```
nm-tool
```
Is the ethernet card listed?

If ethernet adapter is not listed in those commands:
Onboard ethernet cards are switched on/off in the motherboards bios setup.For example,on a gigabyte MB you hold down the delete key to access bios,on-board sound,ethernet ,etc. is in the Integrated Peripherals section of the menu. Find the directions,go into bios menu,reset the bios to defaults,verify ethernet is on and save. 

Final thoughts:
Were it my MB and the on-board ethernet adapter failed I'd replace it with a 10/100 PCI ethernet adapter which cost under $10 USD before contacting the manufacturer,removing the MB from the computer case,pay for shipping,waiting,reinstalling MB.

---

### Post by PZJM on 2011-05-01
Thanks for all the suggestions.  I really appreciate all the help.  So, I decided to totally power down the computer, shut down (unplug) the router and modem.  Then I cycled everything and booya, my ethernet port worked.  I'm not sure what is going on.  The last thing I did before my connection stopped was to update Ubuntu (patches only).  Thanks for all the advice.  I will definitely be keeping a watch on my connection status.

Long live Ubuntu....

---

### Post by unebaguettesvp on 2011-06-18
Wow. Thanks JayKay3OOO and PZJM! All I had to do was unplug the power cable! So weird.

---

