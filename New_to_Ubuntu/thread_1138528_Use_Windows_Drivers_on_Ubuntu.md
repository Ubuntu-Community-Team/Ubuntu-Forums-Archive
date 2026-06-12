---
title: "Use Windows Drivers on Ubuntu"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Roadbloc on 2009-04-26
I heard somewhere you can use windows drivers for ubuntu. Is i true and if so how do i install them? ive got a wireless card spare and id be dead chuffed if i could useit on ubuntu :)

---

### Post by Sealbhach on 2009-04-26
Have you already tried the wireless card? It might run OK without the windows drivers.

Supported wireless cards:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=370108](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=370108)

If not supported, you could use ndiswrapper to install the windows drivers.


.

---

### Post by Cybie257 on 2009-04-26
Have you tried going to the manufacturers website for your wireless card to see if they offer Linux drivers? What brand and model is the card? Maybe someone can help you get it to work if you let us know. :)

-Cybie

---

### Post by Roadbloc on 2009-04-26
ive tried all of that and the only drivers i found didnt work. i was just wonderig if you can get windows drivers to run????

---

### Post by Sealbhach on 2009-04-26
Yes, you possibly can using ndiswrapper.

[http://ubuntuforums.org/private.php?do=newpm&pmid=978348](http://ubuntuforums.org/private.php?do=newpm&pmid=978348)

.

---

### Post by Michael.Godawski on 2009-04-26
Yes we can.

You can use the ndiswrapper tool to install windows drivers for your wlan card.

You need the .inf file from the driver package. 
I always install the package ndisgtk, a graphic front-end making the installation easier. 

```
sudo apt-get install ndisgtk
```After the install of ndisgtk it shows up in System > Administration > Windows Wireless Drivers.
There you just point to the .inf file and restart the network with

```
sudo /etc/init.d/networking restart
```That's how I do it with my USB dongle.
If you have questions, feel free to ask.:)

---

### Post by Roadbloc on 2009-04-26
thanx for the advice everyone. ive installed ndisgtk, but none of my drivers .inf files appear to work. it just comes up with "invalid diver!"

does it really have to be an .inf file or am i doing something wrong?

---

### Post by Sealbhach on 2009-04-26
There could b a few things you could try, e.g. the suggestions in this thread:

[http://ubuntuforums.org/showthread.php?t=257639](http://ubuntuforums.org/showthread.php?t=257639)

and here:

[https://answers.launchpad.net/ubuntu/+question/15438](https://answers.launchpad.net/ubuntu/+question/15438)


.

---

### Post by steveneddy on 2009-04-26
Tell us what kinda card you have and maybe someone could help you better. It seems as if you are asking an open ended question but not giving us enough information to fully help you.

What version of Ubuntu are you using? (8.04, 8.10, 9.04....Hardy, Intrepid, Jaunty)

Is it 32 or 64 bit?

What wireless card is in your machine? model number? brand name?

What kinda PC are we looking at? stock or manufactured? model number? specs?

Wireless should be fairly to get up and running. There has been lots of development of wireless drivers and known ways of getting various wireless cards to work correctly on Ubuntu.

---

### Post by Roadbloc on 2009-04-27
solved it. thanks for all of your help :)

---

### Post by Sef on 2009-04-27
> solved it. thanks for all of your help :smile:


How did you solve it?   Please post how, so others can benefit from your experience in solving this problem.

---

### Post by Roadbloc on 2009-04-27
It was my mistake. I was using the wrong driver :oops:

---

### Post by Sealbhach on 2009-04-28
> **Roadbloc said:**
> It was my mistake. I was using the wrong driver :oops:

Yeah, that would fix it. :)

Thanks for letting us know  and I'm glad it worked for you.


.

---

