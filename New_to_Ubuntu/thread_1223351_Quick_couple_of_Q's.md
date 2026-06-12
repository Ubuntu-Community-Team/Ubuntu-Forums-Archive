---
title: "Quick couple of Q's"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by thesuperjman on 2009-07-26
Ever since I made the switch to Ubuntu(8.10) from Vista ive got two problems.

1: My sound seems to have a volume cap I can't find or change. My speakers/headphones only go so loud now, barely half of their potential that they gave when i used vista.

2: and two, my computer isnt exactly the best gaming computer but its hving trouble running a simple game like Nexuiz. Im pretty sure its a graphics problem. Where/how can i locate this problem and fix it?

---

### Post by cariboo on 2009-07-26
> 1: My sound seems to have a volume cap I can't find or change. My speakers/headphones only go so loud now, barely half of their potential that they gave when i used vista.

Double-click the speaker icon in the top panel and make sure Master and PCM are turned up.

---

### Post by Jimleko211 on 2009-07-26
> **thesuperjman said:**
> 
2: and two, my computer isnt exactly the best gaming computer but its hving trouble running a simple game like Nexuiz. Im pretty sure its a graphics problem. Where/how can i locate this problem and fix it?
Make sure to install your graphic card's driver.  System > Administration > Hardware Drivers

---

### Post by Gen2ly on 2009-07-26
> **Jimleko211 said:**
> Make sure to install your graphic card's driver.  System > Administration > Hardware Drivers

Also disable desktop effects if you got them turned on.

---

### Post by thesuperjman on 2009-07-26
> **Gen2ly said:**
> Also disable desktop effects if you got them turned on.

do you mean go in compizconfig settings and disable everything under the effects section?

and also, thanks cariboo907, turning up the PCM helped a lot.

---

### Post by Liolikas on 2009-07-26
If you run 3D game in 3D desktop cube you may end up with 9D.:popcorn:
I hope your card can handle this.

---

### Post by NullHead on 2009-07-26
> **thesuperjman said:**
> do you mean go in compizconfig settings and disable everything under the effects section?

and also, thanks cariboo907, turning up the PCM helped a lot.

Go to System>Preferences>Appearance and go to the "Visual Effects" tab at the top. Select the "None" option to completely turn off all off compiz.

---

### Post by thesuperjman on 2009-07-26
Thank you Nullhead, that fixed the problem!!

ok guys that solves both problems, thanks a lot!

---

### Post by thesuperjman on 2009-07-27
maybe someone can help me with one more thing.

my computer's clock. i keep trying to change it and it'll stay like i want it. unless i turn off the computer or hibernate, suspend, etc. it keeps going back an hour every time i get back on.

like right now it's 11:29 but my computer shows 10:29 and it won't stay corrected.

---

### Post by DrDevice on 2009-07-27
Make sure you set your timezone information correctly in System->Administration->Time and Date.

Also, I set mine to Manual instead of "Keep synchronized with Internet Servers", maybe Ubuntu is contacting a time server during boot.  Setting it to Manual should stop that.

---

### Post by thesuperjman on 2009-07-29
man i did that and it still changes it.

---

### Post by thesuperjman on 2009-08-04
Here's another one I have for yall.

I run Banshee music player, and it'll play cds fine but when I try to import them it says "could not find encoder for ripping". With other cds it won't even make it that far, on the bottom it will say "fetchin metadata" forever.
Can anyone help me correct both of these problems.

---

### Post by hotstovejer on 2009-08-04
> **thesuperjman said:**
> man i did that and it still changes it.

Check the time in your bios. If that's off, then Ubuntu will be off as well.

---

### Post by hotstovejer on 2009-08-04
> **thesuperjman said:**
> Here's another one I have for yall.

I run Banshee music player, and it'll play cds fine but when I try to import them it says "could not find encoder for ripping". With other cds it won't even make it that far, on the bottom it will say "fetchin metadata" forever.
Can anyone help me correct both of these problems.

Under your Banshee preferences, the audio cd tab should have the import format set to whatever you want your files to be ripped as. I assume you're going to rip them to mp3, so use the mp3 lame encoder. Make sure you have the correct GStreamer codec installed. If you don't know how to install those, go to Add/Remove, and search for GStreamer.

The metadata... maybe I am using something that isn't listed, but it's doing the same thing for me. Sorry!

Jeremy

---

