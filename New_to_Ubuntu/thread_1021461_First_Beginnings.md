---
title: "First Beginnings"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Dozie on 2008-12-25
Hello Fellow Members :)

I am a total beginner with Ubuntu, I just installed it the other night, on a clean HD.  I don't know where to start with the sudo apt-get command feature.  I have an Nvidea Driver Disk and some other Third Party software applications, and was wondering how to install them within the Terminal window.

Please give me your expert advice on 'cutting my teeth' in this new Ubuntu experience.  Thank you kindly
Sam :)

---

### Post by taurus on 2008-12-25
Look in System -> Administration -> Hardware Drivers to see if your video card is on the list.  You can install nVidia driver for it from there.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by shifty_powers on 2008-12-25
are these third party apps for linux or windows?

---

### Post by Dozie on 2008-12-25
Thank you taurus.  I'll try that now :)

---

### Post by nhasian on 2008-12-25
apt-get is a command-line program.  to run it you need to open a terminal (also called bash, command prompt) in the menu click on Applications->Accessories->Terminal to access the terminal.  now you can type in commands like *apt-get*.  sudo gives you superuser permissions and *install* followed by the package name is the operation we give to apt-get.  so put it all together and you would type:

```
sudo apt-get install vlc
```

this will install the videoplayer vlc.  now you can access vlc from Applications->Sound&Video->VLC or you can simply type *vlc* from a command line to launch it.  for more help with the command line go to

[http://www.linuxcommand.org](http://www.linuxcommand.org)

also to enable any nvidia propriety drivers all you need to do is go to System->Administration->Hardware Drivers and activate the driver from there.

---

### Post by Dozie on 2008-12-25
@shifty_powers ehm?...I'm not sure about that distinction.  I used to use WindowsXP.  I'm guessing they were Windows compatible disks, since the Autorun files kicked in immediately on Windows.

---

### Post by Dozie on 2008-12-25
Thanks nhasian for your most helpful tip.

---

### Post by shifty_powers on 2008-12-25
> **Dozie said:**
> @shifty_powers ehm?...I'm not sure about that distinction.  I used to use WindowsXP.  I'm guessing they were Windows compatible disks, since the Autorun files kicked in immediately on Windows.

windows programmes will be compiled in a different way to linux apps, and are not compatible as such.

you can use wine, (wine is not an emulator), a compatibility layer to run windows apps, but not all will work.

which ones were they? there are usually linux native apps for what you need...

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

very interesting article :D

---

### Post by Dozie on 2008-12-27
Sorry Guys, I had a family emergency yesterday, and I'm only getting back just now to 'digest' all the info you have supplied me with.

I'm still confused about the 'sudo apt-get' command...I mean what file extension is the Terminal command line looking for?  Also, I am at a big disadvantage, in that I'm not online where I have Ubuntu installed...long complicated story.

So what Packages, or Software do I need to download for Ubuntu (on my Bro's Windows online computer) so I can install Third Party Drivers on my other Ubuntu 8.10 OS?

@ taurus...I followed your advice in trying to install within the Hardware Drivers section and I got an error message about 'No Proprietary Drivers Are Installed'.

@nhasian, I printed out a bunch of stuff from linuxcommand.org...whooo!!...it's gonna take me some time to figure it all out...incredibly interesting and challenging.  Thanks again Guys for all your support :)

---

### Post by shifty_powers on 2008-12-27
you know, i honestly think that a good read through:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

would be a very good place to start

---

### Post by billgoldberg on 2008-12-27
You seemed to be confused a bit about how things work on Linux.

The programs on your cd won't work on Linux.
They are Windows software, you are using Linux.

--

I don't know where you get the idea that you need to use the command line to install things, you can use it if you want, but you can use gui tools for it.

Go to "Applications, Add/Remove" or "System, Administration, Synaptic Package Manager" to install applications.

--

If hardware drivers says there aren't any in use, that's because you have to enable them.

That should be possible from within the hardware drivers program.

If not, you can use a program called "envyng" to do it.

If it isn't in the repository, google for the name and download the application.

--

If you told us what programs you had on your cdroms, we can suggest alternatives.

I also strongly suggest your read this article:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Dozie on 2008-12-28
Thx 4 all ur help guys.  I ordered An Official Guide To Ubuntu 8.10.  I'll thumb some pages until I'm stumped, and get back to you then. In the meantime I just joined the Ubuntu help Chat on ChatZilla. Not as Dozie.  I have another username up there.  I might bump into some of you there.  Happy New Year peeps :)

---

