---
title: "a question about one of my tv cards functions"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by techno-mole on 2009-06-18
hello.

i have a kworld pci card, which allows me to watch free to air digital tv (free view) i have it set up using kaffeine and it runs great, nice clear picture and such like.

now to the point, the card also allows for listening to fm radio and it has a AV/S-Video input, which means i can plug a dvd player, vdieo or other device into it and watch it on the monitor.

the AV/S-Video input also allows for the connection of a games console, i have my xbox (not 360) connected to it, now in windows i can use the software that came with the card to access the AV/S-Video input (just a matter of selecting the input from a menu) so i was wondering if it would be possible to set it up so that i can access the AV/S-Video input on ubuntu, so i dont have to log into my windows install to play on the console ?

cheers

(the tv card is this one - [http://www.kworlduk.com/products/dvbt-210-se/index.php](http://www.kworlduk.com/products/dvbt-210-se/index.php))

---

### Post by SteveDee on 2009-06-18
If you have VLC media player installed you can view video from the video input of your card by typing the following in a terminal window:-

vlc v4l2:///dev/video0:input=1:width=640:height=480

This assumes that your video card is mounted to /dev/video0 (if not change to video1 or whatever). The "input" argument selects composite video (the video input on your card) when set to "1"

Once you have this working you can create a desktop launcher, rather than type this into a terminal window every time.

I hope this helps.

---

### Post by techno-mole on 2009-06-20
cheers for that, it works a treat, well almost, i have no sound output, the composite does have sound as well (be a bit silly with out it i guess) is there some thing else i need to do ?

im running 9.04 (jaunty) does this make a difference ?

cheers again for the help, im one step closer even with out the sound.

---

### Post by SteveDee on 2009-06-20
> **techno-mole said:**
> cheers for that, it works a treat, well almost, i have no sound output, the composite does have sound as well (be a bit silly with out it i guess) is there some thing else i need to do ?

im running 9.04 (jaunty) does this make a difference ?

cheers again for the help, im one step closer even with out the sound.

To use your computer for video+sound you need to connect video from your source (as you have already done) and the left and right sound channels to your computer sound input.

A typical configuration is to use a triple phono/RCA lead, with a miniature jack plug to twin phono adapter. For example;
 - yellow [composite] video from DVD video out to computer video in, 
 - red [right channel] audio from DVD right channel output to sound card in via jack,
 - white [left channel] audio from DVD left...

Basically composite video includes all the video components, but no audio.

I hope this is clear, but if not just say so.

---

### Post by techno-mole on 2009-06-20
well that explains it. (you learn something new everyday, i didnt know that)

how ever whilst i was waiting for people to get back to me (cheers for that by the way) i came up with the wacky idea of making my own lead, i figured that the yellow was the video input/output and that red and white respectively were the sound out puts (left and right channels) so i routed about in my junk draw and found a lead that basically attaches to the red and white plugs, and then goes to a 3.5mm jack socket, i have a lead with 2 3.5mm plugs on either end, which i figured i could plug into the lead i, and the other end i could plug into the input jack of my sound card.

the only problem is that the lead i found had male connectors, and i needed female, sound i have spliced the plugs from another lead onto it, it works, so its a result.

cheers for the help (and sorry for not knowing about the audio output/inputs)

---

