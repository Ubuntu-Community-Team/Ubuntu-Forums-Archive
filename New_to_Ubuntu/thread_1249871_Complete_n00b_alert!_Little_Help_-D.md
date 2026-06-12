---
title: "Complete n00b alert! Little Help :-D"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by serialtoon on 2009-08-25
Hello everybody! I have recently returned to the idea of going full time to Linux. I have been a loyal windows user and i dont hate it, but i think that Linux will help me further my career and hopefully make me a more versatile OS user. So with this being said, i wish to get my knees deep in Linux :P. Here is what i am working with so far. 

2 - 30GB SSD's in RAID 0 w/ Windows Vista 64bit
1 - 1TB Hitachi Deskstar with my music and movies etc etc
1 - External eSATA connected drive that is blank

I downloaded Ubuntu 9.04 in 32bit mode, but i have 4 gigs of ram, should i have opted for the 64bit? Also, i wish to have ubuntu installed in the external eSATA drive because i don't want to have Linux as my main OS until i feel a bit more comfortable. So i also dont want it to screw with my Windows installation OR the MBR. Is there a method to achieving this? Preferably i would like to be able to switch back and forth between Ubuntu and Windows until i can really take hold of it and then finally, ditch Redmonds greatest. Here's hoping to hear some good news. Thanks a million!

---

### Post by Melk79 on 2009-08-25
64 bit will take full advantage of your RAM.  I run 64 bit, though I don't think I ever do enough to use all the RAM.  Email and news don't take much, but I like the dorky feeling of a 64 bit OS.  More and more programs are offered in native 64bit, so I haven't ran into any real problems there.  There's a bunch of threads on this in the 64 bit forum.  

Ubuntu has the Wubi installer to intall Ubuntu as a program in Windows.  Never used it myself because it doesn't seem like you're giving it a full chance.  The installers work so well now, installing Ubuntu along side Windows with GRUB really isn't very difficult and is very easy to switch between the two.

The real question is what you use your computer for and can you do those things in Ubuntu/linux easily.  What programs do you use often, why do you want to switch.  If you've asked yourself those things and determine Ubuntu will cover it, then it will be a good switch.  Have fun!

---

### Post by serialtoon on 2009-08-25
> **Melk79 said:**
> 64 bit will take full advantage of your RAM.  I run 64 bit, though I don't think I ever do enough to use all the RAM.  Email and news don't take much, but I like the dorky feeling of a 64 bit OS.  More and more programs are offered in native 64bit, so I haven't ran into any real problems there.  There's a bunch of threads on this in the 64 bit forum.  

Ubuntu has the Wubi installer to intall Ubuntu as a program in Windows.  Never used it myself because it doesn't seem like you're giving it a full chance.  The installers work so well now, installing Ubuntu along side Windows with GRUB really isn't very difficult and is very easy to switch between the two.

The real question is what you use your computer for and can you do those things in Ubuntu/linux easily.  What programs do you use often, why do you want to switch.  If you've asked yourself those things and determine Ubuntu will cover it, then it will be a good switch.  Have fun!
Thanks for responding! As you can see i only have 60GB of space and Windows devours about 30-40GB's of it. I mainly use my PC for the typical duties such as web,email,music,movies. The only snag i see is that i would need iTunes, but that is why i want to keep Vista around for a bit longer. Now, the reason i want to switch to Linux is to learn it and feel like i can master it the way i did with Mac OSX and Windows. Sometimes there are some jobs that i have to pass on to others because of my lack of skill in the Linux world. I dont mind having a linux box, but im sure you can understand that some people (my girlfriend mainly) is used to Windows and only cares about getting online and her iTunes music. Which is another reason i cannot go full Linux ... YET. But i see her with a Laptop in the near future. So, with that being said, i cannot split my "main" drive into more than 10gbs, so that idea is out of the question. How would i go about installing Ubuntu into my secondary hard disk without ruining my Vista install? :-D Thanks.

---

### Post by serialtoon on 2009-08-26
Just finished installing Ubuntu 9.04 with succession! Also i had success installing nVidia drivers and getting them to work 100%. What else can i do? Or more so, what do you recommend? Are there any interesting themes i can install?

---

### Post by jrox717 on 2009-08-26
If you are using iTunes for anything other than working with an iPod Touch or iPhone, then I have found that Rhythmbox (some people prefer Banshee or Amarok) works very well, and is much simpler to use than iTunes. So I would recommend trying one of those out, and exploring a bit
As for other cool things, browse the forums a bit, and for themes and such, check out [http://www.gnome-look.org/](http://www.gnome-look.org/) . Try customizing things and make them exactly the way you've always wanted. Welcome to the community!

---

### Post by dearingj on 2009-08-26
@serialtoon: I'd recommend installing [Ubuntu Tweak]("http://ubuntu-tweak.com/") (a useful utility for tweaking various settings in Ubuntu) and familiarizing yourself with the use of Synaptic Package Manager. As for themes, you can find a huge number of them by opening Synaptic and searching for 'theme'.

---

### Post by MelDJ on 2009-08-26
try installing compiz for advanced desktop effects

---

### Post by Cybie257 on 2009-08-26
> **serialtoon said:**
> Just finished installing Ubuntu 9.04 with succession! Also i had success installing nVidia drivers and getting them to work 100%. What else can i do? Or more so, what do you recommend? Are there any interesting themes i can install?

Well, you can play around with itunes 8.2 and see how well you can get it working in WINE with Linux. See the link below for more information. Be sure to scroll down to see the install instructions. Also, check the appDB for other software(s) that you might want to run natively on Linux that's only available for Windows. Not saying they will work so great, but might be fun to test and try and maybe get away from Windows all the way. :)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16848](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16848)

-Cybie

---

### Post by zkriesse on 2009-08-26
First, welcome to Ubuntu! Second, Ubuntu is a very versatile system so there is ALOT available. It's mainly up to the user of what is used and what is done. But remember it's really about what you're gonna use it for that determines the space, the usage, the speed, and ect.

---

### Post by serialtoon on 2009-08-26
I also downloaded and installed the Creative XFi driver. So everything is working 100% as of right now. I forgot to mention that i only use iTunes for my iPhone. Everything else about iTunes just irritates me. When I get home i will look into the Ubuntu Tweak utility. Thanks for the help.

---

### Post by serialtoon on 2009-08-31
> **serialtoon said:**
> I also downloaded and installed the Creative XFi driver. So everything is working 100% as of right now. I forgot to mention that i only use iTunes for my iPhone. Everything else about iTunes just irritates me. When I get home i will look into the Ubuntu Tweak utility. Thanks for the help.

Its been a few days since i have responded, but i was away for the weekend (Las Vegas anyone?) After getting home i decided to try and install the Ubuntu Tweak utility and it gave me a few errors when i tried to install it.
```
checking for TWEAK... configure: error: Package requirements (gtk+-2.0                >= 2.10
    pygtk-2.0               >= 2.10
    pygobject-2.0           >= 2.10
    gnome-python-2.0        >= 2.10
) were not met:

No package 'gtk+-2.0' found
No package 'pygtk-2.0' found
No package 'pygobject-2.0' found
No package 'gnome-python-2.0' found

```

---

### Post by MelDJ on 2009-09-01
> **serialtoon said:**
> Its been a few days since i have responded, but i was away for the weekend (Las Vegas anyone?) After getting home i decided to try and install the Ubuntu Tweak utility and it gave me a few errors when i tried to install it.
```
checking for TWEAK... configure: error: Package requirements (gtk+-2.0                >= 2.10
    pygtk-2.0               >= 2.10
    pygobject-2.0           >= 2.10
    gnome-python-2.0        >= 2.10
) were not met:

No package 'gtk+-2.0' found
No package 'pygtk-2.0' found
No package 'pygobject-2.0' found
No package 'gnome-python-2.0' found

```


that means the three packages are not in your ubuntu. download them from synaptic or run sudo apt-get install gtk+-2.0 pygtk-2.0 pygobject-2.0 gnome-python-2.0

---

