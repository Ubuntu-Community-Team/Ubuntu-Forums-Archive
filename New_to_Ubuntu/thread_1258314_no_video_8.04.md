---
title: "no video 8.04"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by plang68 on 2009-09-04
no video on ubuntu 8.04 laptop hp pavilion dv5 1235  video card intel 4

---

### Post by mikewhatever on 2009-09-04
> **plang68 said:**
> no video on ubuntu 8.04 laptop hp pavilion dv5 1235  video card intel 4

Can you try again and explain the problem in about 20 words, no need writing a novel.
Are tryinh to run from cd, installing, already installed?
What's Intel 4?

---

### Post by Paqman on 2009-09-04
What sort of video? Flash video on the internet? A .avi or .mpeg file you've downloaded? We need a bit more info.

---

### Post by mapes12 on 2009-09-05
To play most video formats including streaming you need the non free codecs. So, in Synaptic install ubuntu-restricted-extras

Then go to Medibuntu and cut and paste the commands into Terminal based on your Ubu version for the other codecs: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then try your video again.

Also, try alternative video players like Xine and VLC

---

### Post by rockstarrem on 2009-09-05
Yes, try alternative players if it's an avi or mpeg file (or something similar). 


Applications > Accessories > Terminal
```

sudo apt-get install mplayer vlc ubuntu-restricted-extras

```

You should be fine after that, post back with results.

---

### Post by pipedreamer on 2009-09-05
HI all,

As a pretty much complete beginner, I'm having trouble streaming (such as you get on youtube) on firefox.

I know about synaptic - can you tell me how to install the non-free codecs in the ubuntu-restricted extras?

Also: I'm using 8.10.

Thank you muchly!

Rachel

---

### Post by mikewhatever on 2009-09-05
OK, so the problem is with playing flash videos. Find **flashplugin-nonfree** in Synaptic and install it.

---

