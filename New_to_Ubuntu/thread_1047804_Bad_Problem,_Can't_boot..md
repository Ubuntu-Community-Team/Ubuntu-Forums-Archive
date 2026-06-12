---
title: "Bad Problem, Can't boot."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Zach.Town on 2009-01-22
Okay I had a thread about me booting up and getting something along the lines of no image found, and then i'm asked to login and it's basically one big terminal. I got fed up with it thinking it was something I did with my xorg.conf so i reformated, I did some stuff, changed some display settings nothing that should have messed it up, rebooted. then the DAMN black screen again asking me to login same everything. So i reformat AGAIN thinking okay this time i'll just apply the graphics card driver it asks me to in the taskbar and install the updates, then I will reboot nothing else. so I do THAT and then I get the EXACT same screen.

tl;dr? I'm getting a black screen with white text that acts as a terminal when I boot.

chrissharp and adult swim I know you're there :D

---

### Post by Zach.Town on 2009-01-22
Am I allowed to bump this?

---

### Post by emarkd on 2009-01-22
bumps are usually not a problem, so long as you wait a bit between bumps.

as to your problem, i'm not sure i understand.  did the gui ever work?  if so, what exactly did you do before it stopped working?

also, what sort of video hardware do you have?

---

### Post by Zach.Town on 2009-01-22
Well for this final one the only thing I had done was start up ubuntu for the first time (had GUI and all).

isntalled the updates, checked the thing for my graphicscard drivers. Then rebooted to see if I still had this same problem, and I did.

My card is an Nvidia GeForce 8800 GT

---

### Post by Zach.Town on 2009-01-22
bump while im still awake >_<

---

### Post by kansasnoob on 2009-01-22
> **Zach.Town said:**
> Okay I had a thread about me booting up and getting something along the lines of no image found, and then i'm asked to login and it's basically one big terminal. I got fed up with it thinking it was something I did with my xorg.conf so i reformated, I did some stuff, changed some display settings nothing that should have messed it up, rebooted. then the DAMN black screen again asking me to login same everything. So i reformat AGAIN thinking okay this time i'll just apply the graphics card driver it asks me to in the taskbar and install the updates, then I will reboot nothing else. so I do THAT and then I get the EXACT same screen.

tl;dr? I'm getting a black screen with white text that acts as a terminal when I boot.

chrissharp and adult swim I know you're there :D

Each time you say "reformatted" did you actually reinstall Ubuntu again?

I'm sorry, but what you're saying leaves me totally lost. I'm not even sure if you're talking about an installed Ubuntu or running Ubuntu from the Live CD.

---

### Post by Zach.Town on 2009-01-22
Yes I reinstalled ubuntu all those times, and no it is not off of a live CD it is installed.

---

### Post by kansasnoob on 2009-01-22
Did you check the md5sum of the downloaded image?

Did you check the integrity of the Live CD?

Have you been able to run the Live CD without installing?

What version of Ubuntu is this?

---

### Post by Zach.Town on 2009-01-22
> **kansasnoob said:**
> Did you check the md5sum of the downloaded image?

Did you check the integrity of the Live CD?

Have you been able to run the Live CD without installing?

What version of Ubuntu is this?



1. Yes
2. Yes
3. Yes
4. Latest

---

### Post by kansasnoob on 2009-01-22
When you say "latest" do you mean Intrepid or Jaunty?

---

### Post by Zach.Town on 2009-01-22
Errr 8.10

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

that one.

---

### Post by Zach.Town on 2009-01-22
little bump :S

---

### Post by kansasnoob on 2009-01-22
Just FYI if you bump too often the the admin's will generally complain.

I just really wanted to rule out some things.

So, you were able to run the Live CD with a full GUI screen but once you installed 8.10 (Intrepid) you get nothing but a terminal?

If that's the case I'm not sure what you should do. I've been very lucky with Intrepid automatically detecting hardware and getting the settings right.

What worked in Gutsy no longer worked in Hardy and I can tell from looking at the differences in xorg between Hardy and Intrepid that the Hardy tricks won't work in Intrepid.

---

### Post by Zach.Town on 2009-01-22
Everything installed and ran perfect, it was just after a reboot that things didnt work.

So think going back to hardy would fix it? i've had that running perfectly a few months ago before removing linux.

---

### Post by kansasnoob on 2009-01-22
> **Zach.Town said:**
> Everything installed and ran perfect, it was just after a reboot that things didnt work.

So think going back to hardy would fix it? i've had that running perfectly a few months ago before removing linux.

Possibly! I recently tried to update a box from Linux Mint 5 to Mint 6 and had to revert, but it was due to a sound problem I couldn't get straightened out.

Linux Mint 5 is based on 8.04 and Mint 6 is based on 8.10.

8.04 is an LTS release so if it works for you, you know you're covered security wise for quite some time.

I'd personally like to learn more about configuring xorg in Intrepid, unfortunately I'm a dummy in that area!

---

### Post by Zach.Town on 2009-01-23
So, on the download page, I would select the one for mass deployment or w/e?

---

### Post by 3rdalbum on 2009-01-23
The problem sounds like Nvidia's video card drivers... *sigh*. They don't seem to want to work with your card.

Rather than install the drivers from the Hardware Drivers program, you should maybe try installing the absolute latest version from Nvidia's website. You need the package "build-essential" and "linux-headers" in order to install the driver manually.

---

### Post by boof1988 on 2009-01-23
> **Zach.Town said:**
> bump while im still awake >_<

Please consider waiting 24 hours before you bump your thread.

Kind Regards...

---

