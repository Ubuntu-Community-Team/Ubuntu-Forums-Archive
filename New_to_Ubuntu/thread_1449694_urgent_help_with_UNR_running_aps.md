---
title: "urgent help with UNR running aps"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Schiaparelli on 2010-04-08
Have been running UNR successfully for a while. last night I installed a whole lot of libraries. long story short, it appears that something updated the headers. I'm a complete and utter novice and I have absolutely no idea what I'm doing - I simply follow the instructions on webpages (to my peril it seems).

Something has definitely changed - I can't shut down it just takes me to some user log-in screen (which I've never had before) and almost no apps work. absolutely nothing works under the Files & Folders menu. Neither the software enter or the update manager work. When I try run any of these it just says loading.... then that message disappears. 

Could someone PLEASE PLEASE PLEASE help me diagnose the problem? I'm assuming that the sudo apt-get install update is what broke things - but this is just a very loose assumption. I'm hoping there's some way to reverse this process so that I don't have to reinstall UNR and lose all the software I've installed...

please help the noob......please!

---

### Post by Psumi on 2010-04-08
Just so you know, with the Lucid release so close, you won't get as much help as of late. So don't go screaming "I'm going to move to windows!!!!" Yet.

---

### Post by Schiaparelli on 2010-04-08
heh Psumi - you read my mind! I REALLY don't want to go back to Windows... it's just a VERY frustrating experience having no idea how to trouble shoot. I put in my UNR boot flash disk - everything works perfectly when I boot off that (although of course all my custom apps are not displayed) and I installed something called PCMan file manager - and that does actually work... my other apps (such as software updater etc) alas just dont work at all.... Will the Lucid release be for UNR as well - I presume so?
my problem here is time.... I need this little netbook up and running for a trip that I'm taking in a few weeks... so if no-one can help me I'm going to have to reinstall - which is beyond a pain....
thanks for your reply tho....

---

### Post by Psumi on 2010-04-08
> **Schiaparelli said:**
> heh Psumi - you read my mind! I REALLY don't want to go back to Windows... it's just a VERY frustrating experience having no idea how to trouble shoot. I put in my UNR boot flash disk - everything works perfectly when I boot off that (although of course all my custom apps are not displayed) and I installed something called PCMan file manager - and that does actually work... my other apps (such as software updater etc) alas just dont work at all.... Will the Lucid release be for UNR as well - I presume so?
my problem here is time.... I need this little netbook up and running for a trip that I'm taking in a few weeks... so if no-one can help me I'm going to have to reinstall - which is beyond a pain....
thanks for your reply tho....

Ubuntu UNR already has a file manager, why go installing PCManFM?

---

### Post by Schiaparelli on 2010-04-08
well I figured that perhaps it was Nautilus that was broken.... so thought I'd try a different file manager - didn't really help tho heh. I'm pretty suspicious of the sudo apt-get install update that I did - and I figure if I could roll that back I'd be a-for-away. it's so weird having some things (like terminal) working, and others not....

---

### Post by Psumi on 2010-04-08
> **Schiaparelli said:**
> well I figured that perhaps it was Nautilus that was broken.... so thought I'd try a different file manager - didn't really help tho heh. I'm pretty suspicious of the sudo apt-get install update that I did - and I figure if I could roll that back I'd be a-for-away. it's so weird having some things (like terminal) working, and others not....

It's actually **sudo apt-get update** then **sudo apt-get upgrade**, in that order.

---

### Post by Schiaparelli on 2010-04-08
ah! well clearly I followed the wrong instructions heh. One thing I've noticed - and perhaps this is something to do with the problem - is that all my file associations are toast - for instance JPGS (which used to open with image viewer) just have some file icon - and you cant click on them.... it's almost like when I click on anything in files & folders the computer doesnt know what action to take...

all the apps work except for ones that require the file manager.... so nothing under the files and folders menu, all the favourites I have work except for the software centre and update manager.... it relaly does seem like nautilus has taken the hit because of some or other update I did.... any clues as to how to update an already up to date nautilus? heh...

Is there a way of uninstalling and reinstalling the file manager?

---

### Post by Schiaparelli on 2010-04-08
right. decided to just reinstall.... quicker and easier for everyone :P

---

### Post by Calash on 2010-04-08
Can you link to the instructions you were following.  It may help if we can see what you were trying to do and where it broke.

The shutdown issue sounds oddly familiar to me.  If you go into the terminal and type the following what happons


users-admin

Don't change anything, just let us know if the window opens or if you get any error ether in a popup or in the terminal.


Edit: that is, if you have not reinstalled yet :)  Typed too slow :)

---

### Post by Schiaparelli on 2010-04-08
heh. at 94% 
it'll teach me to mess around with the terminal when I don't know what I'm doing....

I actually think you were on the right track - pity - but I've also noticed that the battery icon had also disappeared...so best to just yank its brain out before it wanders off down the street to frighten the village folk...

---

### Post by Calash on 2010-04-08
Did sound drop out too?

My guess was going to be that the messagebus user and group got messed up somehow.  If the group ID changes it can cause the messagebus not to be able to start important services.

Had that happen to me a couple of weeks ago when my group file exploded into fire and brimstone.  Took a while to work out what was going on.

A reload is never a bad thing, especially when you are having odd issues.  I am planning on doing a reload when 10.04 hits RC myself, if only to clean up some odd issues from my years of abuse.

---

### Post by Schiaparelli on 2010-04-08
yeah sound also got a bit sketchy... to be honest a reinstall was probably the right way to go (although that said I'm currently staring at the long list of pieces of software to put back and gritting my teeth) as I'd installed all sorts of nonsense just to see what it did. This whole free software thing is like giving candy to a kid...then setting them on fire.... I just HAVE to install it to see what it does you know? I'll probably also do a fresh install by the time 10.04 rolls around - I'm sure I'll have borked this fresh install by then.... thanks for your willingness to help though man, much appreciated.... if you ever need help crash testing ubuntu (read: mindless zombie setting fire to stuff) let me know...

---

### Post by walt.smith1960 on 2010-04-08
I'm a little bit the same way--if it's not broken, fix it 'til it is:lolflag:.  With cheap high capacity disks available, I have a few installations of Ubuntu running. I have a shareware boot manager where I can have 100+ primary partitions so it's possible to have one installation that works (don't screw with it!!!) and other installations for experimentation & abuse.  30Gb is plenty for an ubuntu installation so I could have one stable partition plus 8 or 9 abused partitions if I wanted.  If one gets too messed up, delete it and reinstall. It's SO  nice to not have to worry about beseeching the Great God Microsoft for permission :).

---

### Post by Schiaparelli on 2010-04-08
well I met uncle Bill once when he was here in Cape Town - took him and his wife around the peninsula - seemed like a nice couple... Mark Shuttleworth on the other hand gave me a scar on my knuckle (he has one from me on his knee) as he was my fencing partner in high school. So all things considered, I'd have to agree with you on that one... As to your partitioning idea, that sounds like a damn good way for me to proceed... And as I write this, the netbook has finished reinstalling all the software.... so that wasn't so painful I guess!

---

