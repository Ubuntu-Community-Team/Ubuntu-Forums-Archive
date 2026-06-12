---
title: "Broadcom wireless"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by komatsu100 on 2010-02-01
I am new to Ubuntu and I have 9.10 with duel boot with Windows XP. They are loaded on a Acer Aspie 3000. I know it has a Broadcom wireless card and it wasn't working just right and some one told me the driver for a Broadcom BCM4311 or BCM4312 would work. I down loaded Drivers for BCM4311-BCM4312-BCM-4321and BCM4322, all in a package.  I down loaded and installed, lost wired and wireless connection.  Is there any hope for me our must I stay with Microsoft.  If anyone can help I sure would appreciate it.

---

### Post by samantha_ on 2010-02-01
go into the directory where you extracted the tar.gz to
and run this
```

sudo make uninstall
sudo apt-get install bcmwl-kernel-source

```

---

### Post by komatsu100 on 2010-02-01
> **samantha_ said:**
> go into the directory where you extracted the tar.gz to
and run this
```

sudo make uninstall
sudo apt-get install bcmwl-kernel-source

```

The returns I recieved are;
make;*** No rule to make target 'unstall' stop 

bcmwl-kernel-source is already the newest verson

I do have the wired internet back, but I still would like to get my wireless back.

---

### Post by samantha_ on 2010-02-01
> **komatsu100 said:**
> The returns I recieved are;
make;*** No rule to make target 'unstall' stop 

bcmwl-kernel-source is already the newest verson

I do have the wired internet back, but I still would like to get my wireless back.
I took a good search using google and.....
bad news, see here :[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/127627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/127627)

---

### Post by komatsu100 on 2010-02-01
> **samantha_ said:**
> I took a good search using google and.....
bad news, see here :[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/127627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/127627)

Thanks for the help; and the unstall was a typo, I had put in the terminal uninstall, 
Here is what I recieved back, 
Return-dpkg unknown option. 
I am tired and I am going to quit for the night, I will try to contact you tomorrow.
Ron

---

### Post by cenzorrll on 2010-02-02
I'm not quite sure what happened that made you lose your wired connection.  If you can get that figured out, I would suggest updating your system then running the "hardware drivers" application in system>administration.  I know there was a problem with either jockey (the hardware drivers application) or the kernel that didn't allow the correct installation of that driver (I had many frustrated hours trying to get it to work on my machine when karmic was first released).

```
sudo apt-get update
sudo apt-get upgrade
sudo jockey-gtk
```

apt-get update updates your package lists, apt-get upgrade upgrades your system, jockey-gtk runs the hardware drivers application, and of course sudo runs those commands as an administrator

You may also need to install wicd in order to fully utilise your wireless.  I had many a disconnect and slow speeds until I started using wicd instead of network manager.  You probably won't need to since we probably don't have the same card.  Just in case:

```
sudo apt-get install wicd
```

---

### Post by superprash2003 on 2010-02-02
have you tried system->admin->hardware drivers?

---

### Post by komatsu100 on 2010-02-02
> **superprash2003 said:**
> have you tried system->admin->hardware drivers?

It is blank, it used to say Broadband drivers, but now it is blank.  I have a Broadcom Airforce One, wireless card and I have found out it uses BCM4317 drivers, how do I get them and how do I load them?  
All Red Heads are a lot of help.

---

### Post by samantha_ on 2010-02-02
oh. no wonder its not working.....
the airforce card doesnt work with the Broadcom STA Drivers ;)

so...
```

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter
```
will hopefully get the card working....

---

### Post by komatsu100 on 2010-02-03
> **samantha_ said:**
> oh. no wonder its not working.....
the airforce card doesnt work with the Broadcom STA Drivers ;)

so...
```

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter
```
will hopefully get the card working....

Sorry but for some reason, it is still not picking up the wireless. I interned everything just like you told me and it tells me the bmwl-kernel-source was uninstalled and b43-fwcutter has been installed, but my wireless switch will not turn on with Ubuntu but will with windows do you have any other tricks up your sleeve. 
Ron
I went back to the Net Work Manager and the internet is not working. 
Thanks Samatha, I am a redhead also. 
Ron

---

### Post by warfacegod on 2010-02-03
If you right click the network icon in the panel, is wireless enabled?

---

### Post by samantha_ on 2010-02-03
im afraid im out... and looking at the bug report that i linked your issue to made me less hopeful, since the problem hasnt had one solution yet... I simply advise you to either replace the card, or buy a usb dongle.

---

### Post by bkratz on 2010-02-03
I did find this one regarding the BCM4318 and an Acer and some extra steps that the OP did.  It may not be applicable( it is kinda old), but as much problems as you have had, it seems like it may be worth a try!

[http://georgia.ubuntuforums.org/showthread.php?t=970624](http://georgia.ubuntuforums.org/showthread.php?t=970624)

---

