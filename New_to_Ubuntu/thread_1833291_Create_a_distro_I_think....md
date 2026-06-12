---
title: "Create a distro? I think..."
date: 2011-08-25
forum: New to Ubuntu
---

### Post by D4J0K3R on 2011-08-25
Hi,

I don't know how to call what I want to do.
I want to install Ubuntu on my PC, install drivers, updates, modify the wallpaper, screensaver, software, install personal files & make a DVD of all this.
I want this DVD to be used as a LiveCD & I could install this OS on an other PC and all the settings, personal files, etc. would be installed when the OS installs...
Wow, that doesn't sound clear, but that's the best I can do...

Any help please?

Thank you!

---

### Post by Basher101 on 2011-08-25
Install all you need and configure everything, then use Remastersys to make a Live .iso

-regards

note: the normal "install 11.04" icon wont be on your desktop. You will need to go into your system settings > RELEASE Install to start the installation process. If it does not work open a terminal and type ```
sudo ubiquity --desktop %k gtk_ui
```

---

### Post by D4J0K3R on 2011-08-25
Awesome, that was so fast!
I've found oem-config-remaster in the "Ubuntu software center", is that it?
I was thinking about using ubuntu 10.04 LTS, I guess it's the same procedure?

Thank you!

---

### Post by Basher101 on 2011-08-25
its not that. just type "remastersys" into your software centre
edit: in my software center it also labels the package "Ubuntu and variant system remaster"

---

### Post by ubudog on 2011-08-25
> **Basher101 said:**
> Install all you need and configure everything, then use Remastersys to make a Live .iso

-regards

note: the normal "install 11.04" icon wont be on your desktop. You will need to go into your system settings > RELEASE Install to start the installation process. If it does not work open a terminal and type ```
sudo ubiquity --desktop %k gtk_ui
```

+1 

Thanks!

---

### Post by Basher101 on 2011-08-25
and another note, Remastersys cannot create a live iso bigger than 4 gb, so the ubuntu install you want to turn into a live CD must not be bigger than a maximum of 20 gb. For everything larger you should use Clonezilla

---

### Post by D4J0K3R on 2011-08-25
So I've added "deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/" to be able to see the remastersys software.
But now it tells me it's an untrusted package.
I'm sure it's just something really easy to do, but my n00b skills can't figure it out...

Thanks!

---

### Post by cbowman57 on 2011-08-25
Ignore the warning & install it.

---

### Post by D4J0K3R on 2011-08-25
I would love to, but the installation stops after I press ok.

---

### Post by cbowman57 on 2011-08-25
In a terminal **sudo apt-get install remastersys**

---

### Post by Basher101 on 2011-08-25
i dont get it. Remastersys shows up on me fine without having added any repositories

---

### Post by cbowman57 on 2011-08-25
> **Basher101 said:**
> i dont get it. Remastersys shows up on me fine without having added any repositories

Yours would be the exception.  I think Linux Mint had it in their repositories years ago but I haven't seen it like that in awhile.

---

### Post by Basher101 on 2011-08-25
well anyway just install it and be happy with your "custom" ubuntu distro @ OP

---

### Post by D4J0K3R on 2011-08-25
Maybe it's because you have 11.04, shot in the dark here.
So I've installed it through the terminal and it works!
Thank you everyone!

---

### Post by D4J0K3R on 2011-08-25
I've used the remastersys software to create a .iso file and to burn it to a DVD.
Now I restart my PC with the DVD & I get the error:
Could not find ramdisk image:  /casper/initrd.gz

So close to what I want but no cigar...

Thanks in advance for your help!

---

### Post by cbowman57 on 2011-08-25
Hmm, explore the disk and see if initrd.gz has a different extension.  If so just edit that in from the boot screen.

---

### Post by D4J0K3R on 2011-08-25
It doesn't seem to be there.

---

### Post by cbowman57 on 2011-08-25
Might be compressed in the squash.fs.

What version of Ubuntu are you using?

---

### Post by D4J0K3R on 2011-08-25
Ubuntu 10.04 LTS

---

### Post by cbowman57 on 2011-08-25
Ok, that shouldn't create any problem at all.

Did you run the backup or the distro?  Try running it from a terminal (sudo remastersys), I think that will display your options, if not remastersys --help or -h should.

---

### Post by D4J0K3R on 2011-08-25
I've runned backup.
After reading your e-mail I've runned backup through the terminal.
It gives me an .iso file.
I've burn the .iso file to a DVD & I still have the same problem...
I've made coasters out of my 2 useless DVD's
:P

Thanks for your time

---

### Post by flurospar on 2011-08-26
> **D4J0K3R said:**
> 
I've made coasters out of my 2 useless DVD's

For that bit, you might try Unetbootin!

As for making the distro, type "sudo remastersys dist"

---

