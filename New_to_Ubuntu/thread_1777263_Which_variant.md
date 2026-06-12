---
title: "Which variant???"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by TuskBilly on 2011-06-07
This is a great forum for me. I am an Absolute Beginner in the Linux world. I have worked with several UNIX variants, VMS, several IBM OS's and of course, DOS and Windows. I'm trying to venture out a bit...
 
Now my question. Is one of the Ubuntu variants "lighter" than another? I want to install on a Dell desktop w/ a P4 processor and 640MB. All I need for this system is a web browser, an e-mail client and a simple word processing app.
 
I have downloaded Ubuntu 11.04 and have it installed. It gave me a message about video capabilities and launched the "classic" UI. Would Xubuntu or Kubuntu be lighter and a better fit???
 
Thanks for the feedback from a newbe...:p

---

### Post by jramshu on 2011-06-07
I have a Dell w/p4 Hyper-Threading. I suggest using 10.04 LTS, though 11.04 runs fine on it, Unity does too. Have you enabled hyper-threading? Mine came with it disabled in bios by default. What gpu are you using?

EDIT: Sorry, I should have asked for you to do this.
Open the terminal and type this to get gpu info.
```
lspci
```

paste the output.

---

### Post by Paqman on 2011-06-07
Generally speaking, Xubuntu is designed to be a bit lighter. Kubuntu is as hefty as Ubuntu, if not a little more so.

A good lightweight word processor is Abiword. The lightest way to do email would be in your browser. The two main desktop email clients (Thunderbird and Evolution) are not at all lightweight.

---

### Post by Rubi1200 on 2011-06-07
Hi and welcome to the forums TuskBilly :)

With 640MB of RAM I would be tempted to suggest that you either add more RAM or use a lighter version.

Both Xubuntu and Lubuntu are excellent choices.

Download and burn the images to CD/USB and try them live first to see how they work and which one you like.

---

### Post by jramshu on 2011-06-07
Oops, mine has a gig of ram. 640 is a little light for unity. 

Still would be useful to know what kind of graphics card is being used since its telling flagging your video capabilities.

---

### Post by snowpine on 2011-06-07
If you are happy with Ubuntu's performance, then there is no reason to switch (Pentium 4's are capable, if a bit hot, in my experience).

If you want to give Xubuntu a try you can install it from Software Center or:

```
sudo apt-get install xubuntu-desktop
```

Next time you log out, you'll see an Xfce option in the little menu at the bottom of the login screen, that's Xubuntu. :)

---

### Post by Joe of loath on 2011-06-07
Lubuntu is the lightest of the lot.

---

### Post by TuskBilly on 2011-06-07
Whoa...  That was fast!
 
I'm not at the box so I can't get the video specs right now.  I will also have to look to see if Hyperthreading is turned on.
 
I'm hoping I don't have to add memory.  This is a system for my 80+ year old mother who is tired of all the.... stuff... that comes along with the BillGates world.  She has had the system several years.  It came w/ XP.  I left it as shipped.  She has had a few to many "friends" try to help her with it.  I am hoping loading an Ubuntu variant will discourage some of this since I am 4 hours away from her and remote troubleshooting is frustrating for both of us...
 
I will try both Xubuntu and Lubuntu to see which one works best.  It needs to be *real* simple but nothing fancy....
 
My next question will be how to create a Ubuntu VM on my Win 7 work laptop (Core i7, 4GB) but I will tinker a bit before throwing it out there for help!
 
From what I have seen so far, I think I'm going to like this Linux thing......
 
Thanks! :D

---

### Post by Joe of loath on 2011-06-07
If you want simple with no bells and whistles, Lubuntu is perfect.

For a VM, just install virtualbox and start playing :D

---

