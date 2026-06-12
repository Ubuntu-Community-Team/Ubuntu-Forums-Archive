---
title: "new ubuntu user with questions"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by ceece on 2009-08-27
:P I have an Eeepc 900 ASUS netbook and just newly installed the ubuntu 9.04. I did all the update installations that were recommended when I first fired it up.
 
1. How do I get adobe flash? like in youtube. I tried 3 different kinds from youtube site, and they all failed. 
 
2. When I try to play a dvd, a program pops up and identifies my dvd by name, but then I get an error that says I need a "dvd source plug in which is not installed"
 
3. still working on getting my webcam (the one that is built into my netbook) to work.
 
other than that, I like ubuntu better so far than the original linux that was installed on my netbook.:cool:
Ceece

---

### Post by Ms_Angel_D on 2009-08-27
For flash/java etc..etc..etc. in terminal run:

```
sudo apt-get install ubuntu-restricted-extras
```

or go into add/remove programs and make sure you have all software selected then search for restricted. Select and apply.

for dvds you'll want to have a look at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Not sure about the webcam

---

### Post by Tibuda on 2009-08-27
> **Ms_Angel_D said:**
> For flash/java etc..etc..etc. in terminal run:

```
sudo apt-get install ubuntu-restricted-extras
```

Or [click here]("apt:ubuntu-restricted-extras") if using Firefox from Ubuntu.

---

### Post by beastrace91 on 2009-08-27
Medibuntu is what you want to solve your media woes :)

Just run the following two commands in terminal while you have an active internet connection: ```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
sudo apt-get install non-free-codecs vlc mplayer libdvdcss2
``` And then you should be able to play just about any media out there :)

~Jeff

---

### Post by donkyhotay on 2009-08-27
+1 for medibuntu

---

### Post by cusinmex on 2009-08-27
Just use the Synaptic Package Manager..
just makes it more easier than
downloading the tar.gz and having
to manually install it.

hope this helps :D

---

### Post by ceece on 2009-08-27
another problem I am having since I am totally new to LInux :confused: is, 
How do you open a program you downloaded.
I just downloaded "cheese" program for the webcam, but do not know what application I use to open it and install it. 
 
thanks
Ceece

---

### Post by Squalo_ch on 2009-08-27
For Cheese don't bother with installations. Go the easy way:
On the top panel click on Applications>Add/Remove... type cheese on the search field, then tick Cheese on the Application list and press Apply changes. Voila!!

---

### Post by ceece on 2009-08-27
Thanks Squalo, 
I installed in quickly from the add/remove programs, but Cheese says "no camera found"
I have the camera installed in the actual netbook (built in)
I wonder if this is not a recognizable camera with Cheese.
 
Does anyone know how to get the camera on my netbook (already installaed within the book itself) to run?

Thanks!
Ceece:KS

---

### Post by ceece on 2009-08-27
Thanks everyone for the great tips.
I will check all of them out and see if I can get somewhere with this!!!
Ceece:P

---

### Post by ceece on 2009-08-27
Miss Angel and Daniel,
Youtube is working now after i put the code in.
thanks from this newbuntu!!!:popcorn:

---

### Post by ceece on 2009-08-27
I went to medubunti to run the two codes, the shorter code worked but the longer one failed (404)
Is there any easier way to get my media player working? i might be putting spaces or dashes where I shouldn't. Not sure if I'm typing in the apostrophes ' and spaces correct.

So far a full day dedicated to getting this up and running has some headway!
I've gotten this far.....:confused:

---

### Post by pedro3005 on 2009-08-27
You can copy and paste into the terminal, makes it easier.

---

### Post by ceece on 2009-08-27
:lolflag:  now it wants my password. when i try to type the password, it does not type out????

---

### Post by RJ12 on 2009-08-27
> **ceece said:**
> :lolflag:  now it wants my password. when i try to type the password, it does not type out????

In the terminal this is normal its for security reasons type your password then press enter

---

