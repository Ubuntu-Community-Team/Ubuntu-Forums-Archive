---
title: "Mic not working on my acer laptop"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by irfad on 2010-06-07
I have installed ubuntu 10.04 and working fine. But I cant get microphone to work on skype or sound recorder. Speaker output has no problem. Im using **"acer extensa 5220"**

Driver is : 
[B]Card: HDA Intel                                   
Chip: Realtek ALC268 [/B]

Please someone give me a solution. :(

---

### Post by Metrop021 on 2010-06-08
Is it a USB mic or a 3.5mm mic?

---

### Post by Bucky Ball on 2010-06-08
... or the laptop mic?

---

### Post by irfad on 2010-06-08
Its and inbuilt laptop mic

---

### Post by flying_174 on 2010-06-09
This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There  should be 2 sliders, and a input tester at the bottom. Speak into the  mic. you will know if it is working. If it is not, slide the slider that  says Front Left, to 0%. Now speak. If the mic works here your good to  go. 

Hope this helps.

---

### Post by irfad on 2010-06-11
Hey thanks alot. it's working great.. You saved my time :popcorn:

---

### Post by bookcrazy on 2010-08-08
Thanks a million for the post. That worked like a charm!

---

### Post by Yehudama on 2010-08-10
> **flying_174 said:**
> This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There  should be 2 sliders, and a input tester at the bottom. Speak into the  mic. you will know if it is working. If it is not, slide the slider that  says Front Left, to 0%. Now speak. If the mic works here your good to  go. 

Hope this helps.

Dear Friend,

I have Acer laptop ASPIRE 4930ZG , built in mic sound is strange noise
can't record good quality voice , and also Skype doesn't work
I hear sound , but mic is not working....

Please help

---

### Post by vbartolotta on 2010-09-22
Good Day,

I have Karmic installed on an Acer Aspire 7740-5618 laptop. The built in microphone doesn't work with any application. I've tried the remedies in this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) to no avail.

Oddly enough, the microphone works fine when I boot the laptop in Windows 7.

Selecting default devices, adjusting volume levels with the PulseAudio Volume control doesn't change anything. Alsamixer reports my gains are set to maximum.

Playback is not a problem. Speaker output is just fine.

Any help is greatly appreciated.

Victor

---

### Post by Bucky Ball on 2010-09-22
I advise you to start a new thread specifically about your issues. This thread is old and you're buried nine deep.

Welcome to the forums and good luck. :)

---

