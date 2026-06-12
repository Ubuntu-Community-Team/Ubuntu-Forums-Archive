---
title: "Karmic 9.10 - Change sound device using bash (Script)"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by fatality_uk on 2010-06-02
I have a USB phone (Freshtel FT-102 VOIP USB Phone) which I would like to use. It works fine as long as I go into the Sound Preferences and manually change the input and output device.

However, my wife would like to use SKYPE as well to call home so I would like to create a script which will switch the input and output devices for the FT-102, start SKYPE and grab the PID for it, monitor it and when that PID is released, switch back the audio devices.

I should be able to do the getting the PID bit (Google being our friend here) but the audio hardware switching eludes me.

Anyone offer any suggestions please?

---

### Post by fatality_uk on 2010-06-03
I am going to bump this cos I KNOW there are much smarter people then me out there who can do this ;)

---

### Post by fatality_uk on 2010-06-10
Just wondering if anyone might be bale to shed light on this?

Thanks

---

### Post by fatality_uk on 2010-06-18
100+ views, not one answer. RIGHT!!

[IMG]http://www.printedclothing.com/contents/media/pc425%20youre%20fired%20alan%20sugar.jpg[/IMG]

---

### Post by Sef on 2010-06-18
> 100+ views, not one answer. RIGHT!!

Then the one who would have the answer has not seen your thread then.  Sometimes, it takes longer than you want for the right person to come along.

---

### Post by fatality_uk on 2010-06-18
> **Sef said:**
> Then the one who would have the answer has not seen your thread then.  Sometimes, it takes longer than you want for the right person to come along.

I know! It was nothing but a shameless bump :oops:
As was this, wait I better stop now :)

---

### Post by gentleStu on 2010-06-22
Hi there,

it's not exactly what you're looking for, but you might find the script in [http://ubuntuforums.org/showthread.php?t=1370383](http://ubuntuforums.org/showthread.php?t=1370383) helpful for examples of switching audio devices. It works for me in Lucid switching between a USB headset and the standard audio (though n.b. I needed to 'apt-get install notify-bin' to fix the reference to notify-send).

hope this helps

Stuart

---

### Post by fatality_uk on 2010-07-23
Hi Stu, thanks for that but actually my wife solved this rather difficult problem quite simply.

I had been coding with Python, bash etc to try and solve this and one day I heard her on the USB phone and then 5 minutes later watching YouTube.

Puzzled, I asked how the heck she managed to switch the audio devices in the "sound manager" to re-enable the SoundCard.




[SIZE="4"]**I JUST UNPLUGGED THE PHONE AND YOUTUBE WORKED!**[/SIZE]





*sigh......

---

