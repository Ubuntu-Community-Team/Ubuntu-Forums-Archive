---
title: "noooooooooobie here."
date: 2009-11-09
forum: New to Ubuntu
---

### Post by slowsmoke on 2009-11-09
Hello folks,  I have installed Ubuntu yesterday and like it so far.  I have come across a small problem though.  While playing Farm Town on Facebook, I noticed my neighbors pictures at the bottom of the game screen were, smushed together.  Also in the "gifts" box, I could not scroll down to the bottom.  this is a problem because there was no scrolling option.  I really have no idea where to start.  If any one could Help me I would be very thankful.

---

### Post by doas777 on 2009-11-09
I hope your query elicits a better response than this one (my kids woudl love it), but if you rightclick in just the right place on the border of the flash plane, it MAY show an entry called "This Frame >". expand "this frame>" and select "open frame in new Tab/window"

hth

---

### Post by sandyd on 2009-11-09
> **slowsmoke said:**
> Hello folks,  I have installed Ubuntu yesterday and like it so far.  I have come across a small problem though.  While playing Farm Town on Facebook, I noticed my neighbors pictures at the bottom of the game screen were, smushed together.  Also in the "gifts" box, I could not scroll down to the bottom.  this is a problem because there was no scrolling option.  I really have no idea where to start.  If any one could Help me I would be very thankful.
your using firefox right?

---

### Post by nwadams on 2009-11-09
Did you install flash or java? I suspect the webpage formatting issue is a flash or java issue. 
Hope that helps. 

Ps. It also may be a font issue. If you install ubuntu restricted extras that should fix it

nwadams

---

### Post by nikhilbhardwaj on 2009-11-09
you're probably missing the correct flash plugin
i think you should try to install flashplugin-nonfree from synaptic package manager

---

### Post by kyuubi777 on 2009-11-09
nobody help anyone who plays that useless hopeless anoying game.. every time i log in it;s all "somebody is 'movin on up' in farmville" .. i have deleted friends for this.. i make it a policy to do so

---

### Post by sandyd on 2009-11-09
> **slowsmoke said:**
> Hello folks,  I have installed Ubuntu yesterday and like it so far.  I have come across a small problem though.  While playing Farm Town on Facebook, I noticed my neighbors pictures at the bottom of the game screen were, smushed together.  Also in the "gifts" box, I could not scroll down to the bottom.  this is a problem because there was no scrolling option.  I really have no idea where to start.  If any one could Help me I would be very thankful.
did you isntall flash player?

edit: i got beat
just install
```

ubuntu-restricted-extras
```

---

### Post by doas777 on 2009-11-09
well, I have teh same problem (or rather the kids do) on jaunty with flash-nonfree, sun java6 and the restricted extras package installed.

the problem seems most pronounced on the HDTV monitor (42" @1920x1080)

---

### Post by slowsmoke on 2009-11-09
> **carlee said:**
> did you isntall flash player?

edit: i got beat
just install
```

ubuntu-restricted-extras
```

carlee, do I install in Terminal?

---

### Post by slowsmoke on 2009-11-09
and "my kids will love it"

---

### Post by slowsmoke on 2009-11-09
> **carlee said:**
> your using firefox right?
and yea im using firefox

---

### Post by doas777 on 2009-11-09
yes, run that command in a terminal. it will take some time to complete, but has lots of good codecs and runtimes.

---

### Post by slowsmoke on 2009-11-09
> **doas777 said:**
> yes, run that command in a terminal. it will take some time to complete, but has lots of good codecs and runtimes.
just says command not found...

---

### Post by doas777 on 2009-11-09
```
sudo apt-get install ubuntu-restricted-extras
```

sry. I thought carlee posted teh complete command. that shoudl do ya

---

### Post by sailor2001 on 2009-11-09
sudo apt-get install ubuntu-restricted-extras


in terminal, yes

---

### Post by slowsmoke on 2009-11-09
> **doas777 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```sry. I thought carlee posted teh complete command. that shoudl do ya
Okay, carlee and doas, I installed the  flashplugin-nonfree and ran the command.  Still nothing.  Any thing else I can try?

---

### Post by slowsmoke on 2009-11-09
> **slowsmoke said:**
> Okay, carlee and doas, I installed the  flashplugin-nonfree and ran the command.  Still nothing.  Any thing else I can try?
ould it be my graphics card or drivers? I'm running a GeForce 7600gs with 512  also I just noticed when I tried to play "trigger".  My screen went black and would not play?

---

### Post by Merk42 on 2009-11-09
What driver are you using?
System > Admin > Hardware Drivers

---

### Post by slowsmoke on 2009-11-10
> **Merk42 said:**
> What driver are you using?
System > Admin > Hardware Drivers

NVIDIA accelerated graphics driver (version 185) [Reciommended]

---

### Post by doas777 on 2009-11-10
hmmmm. the nvidia drivers in ubuntu are pretty much on par with what you woudl download from nvidia (I wish i could say the same for ATI), so there may be an subtle incompability at play (never got overscan control working on an 8300 or 8400 for instance).
you can try using envy-ng to install a driver straight from nvidia but it may not change anything.
just a thought/

---

### Post by slowsmoke on 2009-11-11
> **doas777 said:**
> hmmmm. the nvidia drivers in ubuntu are pretty much on par with what you woudl download from nvidia (I wish i could say the same for ATI), so there may be an subtle incompability at play (never got overscan control working on an 8300 or 8400 for instance).
you can try using envy-ng to install a driver straight from nvidia but it may not change anything.
just a thought/

thanks I will give it a try...

---

