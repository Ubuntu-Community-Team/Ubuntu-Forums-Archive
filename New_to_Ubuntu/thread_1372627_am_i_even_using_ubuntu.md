---
title: "am i even using ubuntu?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by ethan073 on 2010-01-04
i don't even know what i'm using. i think this is Ubuntu. 
i did a system restore on my previously windows os HP Mini netbook, and when i used the[ usb bootable restore image from hp's website ]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68017-1&cc=us&lc=en&dlc=en&product=3979068")it booted up using linux. i figured i'd give linux a try and see what its all about before switching back to windows.[URL="http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68017-1&cc=us&lc=en&dlc=en&product=3979068"]
[/URL] here is what the home screen looks like: [http://www.breakitdownblog.com/wp-content/uploads/2009/02/hp-mi-netbook-ubuntu-based-home-screen-500x292.jpg](http://www.breakitdownblog.com/wp-content/uploads/2009/02/hp-mi-netbook-ubuntu-based-home-screen-500x292.jpg)

i came across the Complete guide to Ubuntu on this forum ([http://ubuntuforums.org/showthread.php?t=781352](http://ubuntuforums.org/showthread.php?t=781352)) and have started reading, but i can't even find half of what its talking about on my computer.

for instance, in chapter 3 labeled "installing with gui", i cannot find the software sources page that is pictured. i cant even find the administration folder that the software sources folder is in. the only "System" i can find is when i click the Settings button in the top right corner of my screen, it pulls up a folder titled "System Settings". Maybe this is the same thing. Maybe its not. But if it is the same, why can't i find Administration?


Basically, i need to figure out if this is Ubuntu or not, which i believe that it is, and if it is how the crap do i go about installing wine.

any help is greatly appreciated.

thanks

---

### Post by camaron1 on 2010-01-04
No, that is not Ubuntu ?!

---

### Post by theozzlives on 2010-01-04
It sure don't look like Ubuntu.

---

### Post by LuisGMarine on 2010-01-04
Yeah that's weird...

---

### Post by J V on 2010-01-04
Looks like a linux ripped HP OS designed to restore windows systems (What a dirty rotten trick! if theres anything linux shouldn't be used for...)

You can download ubuntu from the ubuntu.com website.

---

### Post by lincoln32 on 2010-01-04
HP used several versions of linux but I believe you are using a hp modified ubuntu but linux changes fast. so consider a reload to ubuntu netbook remix
(unr) 9.10 since you are at a good point to start fresh and get the latest
software. ubuntu.com and look for link to unr file download per instructions
it is fast and full featured.

---

### Post by pgp_protector on 2010-01-04
You appear to be using HP's Linux
"HP Mobile Internet Experience, Linux"

According to this it's a customized version of Ubuntu 8.04
[http://www.downloadsquad.com/2009/02/04/hp-releases-netbook-interface-for-ubuntu/](http://www.downloadsquad.com/2009/02/04/hp-releases-netbook-interface-for-ubuntu/)

---

### Post by Methuselah on 2010-01-04
Or is it one of those minimal linux installs built into the motherboard on ROM?

---

### Post by cenzorrll on 2010-01-04
it looks like a customized version of some sort of linux (the battery icon and stuff on the bottom right looks like gnome stuff)

try this ctrl-alt-f1 (to get out you can type ctrl-alt-f7 and you'll get back your screen, if it's linux) and you should get a scary, black screen with a login

then it's most likely linux 

then, type in your username and password.

then 
```
uname -a
```

and it should give you some information. on what you have.  mine looks like this:
```
Linux TableTop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```


edit: or you can just read this post > You appear to be using HP's Linux
"HP Mobile Internet Experience, Linux"

According to this it's a customized version of Ubuntu 8.04
[http://www.downloadsquad.com/2009/02...ce-for-ubuntu/](http://www.downloadsquad.com/2009/02...ce-for-ubuntu/)

---

### Post by ethan073 on 2010-01-04
ok so its HP's customized version of Linux Ubuntu 8.x ... so anybody know how to install programs on this thing? i miss my itunes.

---

### Post by Marlonsm on 2010-01-04
Installing iTunes in Linux is not an easy task, as Apple doesn't want people to move to Linux.
It's way easier to install some alternative, like Amarok.

The way of installing depends on how HP customized it.
If you can find anything like "Add/Revome Applications" it should be there, just click to install.
If you can't, just open the terminal and type (assuming it's based on Ubuntu):
```
sudo apt-get install amarok
``` and type in your password (you likely won't see the *'s while you type, it's normal).

Amarok should work with most music players.

---

### Post by ethan073 on 2010-01-04
there is an add/remove applications on here. so can i just download wine and then download itunes and start using it from there? and if so which version package should i use of wine?

also, is normal Ubuntu available via bootable usb flash drive? there are not cd or dvd drives on these netbook mini's.

---

### Post by ubudog on 2010-01-04
You could just install ubuntu from ubuntu.com and install wine from there.  Open a terminal and type: ```
sudo apt-get install wine
```

---

### Post by Vignesh S on 2010-01-04
Yes for sure, Ubuntu can be booted off USB's. I do it all the time. There's a USB startup disk creator in Ubuntu, though I'm not sure about what you've got at the moment. 

As for iTunes, version 9.02 works in Wine version 1.1.34, albeit with a few glitches, which are mentioned [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18308")

---

### Post by sandyd on 2010-01-04
> **ethan073 said:**
> <snip>

also, is normal Ubuntu available via bootable usb flash drive? there are not cd or dvd drives on these netbook mini's.
you can use unetbootin.

---

### Post by Vignesh S on 2010-01-04
Say, do you still have Windows on that by any chance? If not, try typing in unetbootin in Add/Remove or more preferably Synaptic Package Manager

---

