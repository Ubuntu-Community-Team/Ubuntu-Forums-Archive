---
title: "Codecs for video and audio"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by tim1970 on 2009-04-14
I am trying to figure out what I need to install after 8.10 is loaded.

I believe if I run the following:
sudo apt-get install ubuntu-restricted-extras

then I will have all the codecs for music, as well as flash to watch flash videos.  Correct?  Does this allow me to watch DVD videos also?

Also, I see where I can add the Medibuntu repository for additional packages. What does this repository give me, that I can't get from ubuntu-restricted-extras.


What I am trying to accomplish, is to generate a list of items that need to be installed after loading 8.10, so I can put this on several desktops and laptops.


Thanks

Tim

---

### Post by achase79 on 2009-04-14
Medibuntu give you the ability to watch encrypted DVDs (libdvdcss2), AAC codecs, & other non-free codecs (wma, wmv).

---

### Post by cozmicharlie on 2009-04-14
The Medibuntu repository contains most of the codecs you will need.  Add the medibuntu repository before you install the Ubuntu Restricted Extras.  You also may need to add some codecs individually from Synaptic - for example I add flac, aac and alac because I listen or transcode music coded in each of those formats.

---

### Post by naveedmurtuza on 2009-04-14
Hi

For the list of packages in medibuntu 

[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

And for installing the medibuntu repo

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by steve101101 on 2009-04-14
also when you are playing some movie type, such as an .avi in Ubuntu and don't have the required codec. It will tell you this and ask to install it. If you do this it should play fine.

---

### Post by tim1970 on 2009-04-14
> **cozmicharlie said:**
> The Medibuntu repository contains most of the codecs you will need.  Add the medibuntu repository before you install the Ubuntu Restricted Extras.  You also may need to add some codecs individually from Synaptic - for example I add flac, aac and alac because I listen or transcode music coded in each of those formats.


So I add the Medibuntu repository,
 then run sudo apt-get install ubuntu-restricted-extras?

Is ubuntu-restricted-extras a package in the Medibuntu repository?


Tim

---

### Post by achase79 on 2009-04-14
add the Medibuntu repository and then run ```
sudo apt-get install ubuntu-restricted-extras non-free-codecs libdvdcss2
```

---

### Post by AndyCooll on 2009-04-14
As the above say, and you can get all the information you need about Medibuntu, and how to add it as a repository [here]("https://help.ubuntu.com/community/Medibuntu")

No, Ubuntu Restricted Extras isn't in Medibuntu. As far as I'm aware you don't need Medibuntu to run Ubuntu Restricted Extras (which is just a shortcut script pointing to a number of applications) and to just install the general codecs, e.g. to play mp3's this will be enough. 

What you need Medibuntu for is to install a couple of the more "controversial" codecs such as libdvdcss2 (which helps you play some encrypted DVD's) and w32codecs. 

:cool:

---

### Post by tofiluk on 2009-04-14
i think the easiest way (and maybe the more practical way) is to follow what steve101101 said. it works for me. playing a multimedia without the codec will give you a message to install necessary codecs for that multimedia and that's it. :D

---

### Post by steve101101 on 2009-04-14
> **tofiluk said:**
> i think the easiest way (and maybe the more practical way) is to follow what steve101101 said. it works for me. playing a multimedia without the codec will give you a message to install necessary codecs for that multimedia and that's it. :D

:) thanks.

---

### Post by swoody on 2009-04-14
Tim1970. The other's advise it great to follow. That should set you up pretty well!

I have found Ubuntu-Freak's post on multimedia to be a GREAT guide, as it walks you through the whole process of what packages you need to install, as well as different options for 8.04 vs. 8.10, etc. It also has complete sections dedicated to the certain types of things you want to do - i.e. DVD playback, Audio encoding, etc. The guide is designed as a Terminal 'copy and paste' so besides opening your terminal, and knowing your password, there's really no skill or otherwise knowledge required! You may want to check it out [HERE]("http://ubuntuforums.org/showthread.php?t=766683") :D

---

