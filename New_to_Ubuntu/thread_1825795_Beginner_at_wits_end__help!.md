---
title: "Beginner at wits end :/ help!"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by L8az17 on 2011-08-15
Hey guys, 
      I had ubuntu 10.10 running on an older Gateway E-4500D. I had a GeForce 9800GT graphics card in it. everything spiraled downwards when I upgraded to 11.04.  everything was fine until my desktop began to act unresponsive and I couldn't access by home folder.  Then this morning the update manager prompted me to do a "partial upgrade" and, thinking it would fix the problem, I downloaded it. Upon restarting it after the upgrade, I got an error from booting: "MCU Error - Plymouth command failed" I took the GeForce card out of it, but then ubuntu just booted to a black screen.  Grub will not boot for a recovery, and a live cd doesn't fix the problem either.  I dont want to loose all of my files in my home folder... I've searched forums and conversations for the last 5 hours, and nothing seems to be working... can anyone help me? I'm at my wits end with this thing... any help would be greatly appreciated.

Regards

---

### Post by Jerry N on 2011-08-15
Are you saying that you can't boot from a live CD?  If so, you probably have a hardware fault.  If you can boot from a live CD, you should be using it to copy any important files you have to some kind of backup media before you start changing things.  You should, of course, already have your important files backed up but it seems that most people won't believe that until they lose them.

Jerry

---

### Post by Actonix on 2011-08-15
You say you took your Graphics card out but do not say what Graphics card replaced it - if you have none in place and therefore no Monitor attached you naturally will not get anything other than a blank screen

---

### Post by L8az17 on 2011-08-16
Thanks for the response guys,
                  When I removed the (GeForce) vid card, I just used the internal (stock) VGA card on the motherboard.  It just shows "Ubuntu" and loads, then the screen goes black. 

UPDATE:  with the live cd, I can now boot into the "try Ubuntu" desktop, but I can't access a terminal to try and load any NVIDIA drivers... I think that might be the problem?

---

### Post by Bucky Ball on 2011-08-16
Choose the recovery kernel when you boot (should be second on the list) and when you get to the options choose 'Failsafe X' option. That will give you a low res desktop. You can go from there and attempt to install the Nvid drivers or whatever else you want to try.

---

### Post by Noncon on 2011-08-16
> **L8az17 said:**
> Thanks for the response guys,
                  When I removed the (GeForce) vid card, I just used the internal (stock) VGA card on the motherboard.  It just shows "Ubuntu" and loads, then the screen goes black. 

UPDATE:  with the live cd, I can now boot into the "try Ubuntu" desktop, but I can't access a terminal to try and load any NVIDIA drivers... I think that might be the problem?

The nvidia card will run in VGA even without the drivers.  The reason your screen is turning black is the resolution is incorrect.  When it goes black, try CTL-ALT +/- (NUM Pad), and see if the screen comes back on. 

KJ

---

### Post by L8az17 on 2011-08-16
> **Noncon said:**
> The nvidia card will run in VGA even without the drivers.  The reason your screen is turning black is the resolution is incorrect.  When it goes black, try CTL-ALT +/- (NUM Pad), and see if the screen comes back on. 

KJ

It didn't work unfortunately, but I never thought about the resolution not being right.... however, now I can't boot into recovery from the Live CD.  When I press SHIFT it is unresponsive, and when I press ESC, it goes to a black screen that says "stdin: error 0", the black screen continues to load a little bit, the says "MCU - Error: no response from hardware"

---

### Post by jtarin on 2011-08-16
Can you boot to the desktop using the Live CD? Why can't you access terminal? If you can't access a terminal, while at the desktop can you access a virtual terminal by using the key combinations Ctrl + Alt + F1-F6? If you can then you can access your files using the CHROOT method.

---

### Post by scruffyeagle on 2011-08-16
> **L8az17 said:**
> It didn't work unfortunately, but I never thought about the resolution not being right.... however, now I can't boot into recovery from the Live CD.  When I press SHIFT it is unresponsive, and when I press ESC, it goes to a black screen that says "stdin: error 0", the black screen continues to load a little bit, the says "MCU - Error: no response from hardware"

Hi, I'm another newbie to Ubuntu, so take what I say w/ a big chunk of salt. Reading what you wrote, it almost sounds as if you've got 2 problems going on. One, being that it sounds like your graphics card died. That would be the error mssg. saying "no response from hardware". The other, would be that when you tried using the on-board VGA, the X11 settings were for a resolution higher than that VGA.

So, my suggestion would be to remove the card again, try to boot from the Live CD, and use the CTL-ALT +/- (NUM Pad) to change the resolution. I'm not sure exactly how that works, but if it's something you can do during booting, then it sounds like it might be a path toward being able to salvage your files onto some kind of backup medium.

---

### Post by jtarin on 2011-08-17
Also make sure the onboard graphics is enabled in the bios.

---

### Post by Bucky Ball on 2011-08-17
Did you try this yet?

> **Bucky Ball said:**
> Choose the recovery kernel when you boot (should be second on the list) and when you get to the options choose 'Failsafe X' option. That will give you a low res desktop. You can go from there and attempt to install the Nvid drivers or whatever else you want to try.

---

### Post by jtarin on 2011-08-17
> **Bucky Ball said:**
> Did you try this yet?
> Originally Posted by Bucky Ball View Post
Choose the recovery kernel when you boot (should be second on the list) and when you get to the options choose 'Failsafe X' option. That will give you a low res desktop. You can go from there and attempt to install the Nvid drivers or whatever else you want to try.

I don't think that will..... as he says.....

> but then ubuntu just booted to a black screen. **_Grub will not boot for a recovery,_**

---

### Post by L8az17 on 2011-08-18
Well guys, I ended up doing a fresh install of 11.04 from a Live cd and it seemed to fixed the problem! (knock on wood) 

In retrospect I could see how it would freak out because if all the add-ons and experimental stuff I had on there, I'm sure one or many of those factors had a hand in it!!

I want to thank all of you guys for your patience and fast response!! you guys are the best :] 

Happy fall!

---

### Post by pierreyy on 2011-08-18
So glad that it worked out! 
 dont forget to mark as solved ;)

---

### Post by Bucky Ball on 2011-08-19
Good news!

> **pierreyy said:**
> ... dont forget to mark as solved ;)

---

