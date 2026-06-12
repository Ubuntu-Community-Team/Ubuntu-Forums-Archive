---
title: "Total noobie, nvidia nForce630m and a blank screen"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by minathebrat on 2009-05-10
Hi.
I'm hoping someone can help me. I've been reading thread after thread about people having issues with Nvidia graphics card drivers so I know it's fairly common, but honestly, I can't make sense of the ensuing conversations, so I'm hoping someone can put it into small words for me!

I installed Ubuntu on my hubby's laptop as an in-Windows Vista dual boot. I got it online, but I got an error msg saying that the nvidia driver was unsupported. The card is a Nvidia GeForce 7150m/nForce 630M. So I went into the Hardware driver section and tried to install the nvidia drivers they had listed ( I think it was 173 and 177) but neither would install. So then I downloaded and installed all of the updates for Ubuntu. I was then able to install the driver it recommended thru the hardware driver, it wasn't the 173 or 177, it was a 180-something, I don't remember exactly. It wanted me to reboot the computer, which I did, we got to the log-in screen, I type in the log-in and password and then the screen goes black.

I realize from reading threads that there is some kind of recovery mode for ubuntu, but I don't know how to access it, or how to remove or repair the driver once I'm there. I also have found out that there are linux drivers from nvidia, but are these the ones that ubuntu tries to use first, or do you have to manually download them?

Thanks so much, I really appreciate it!

---

### Post by overdrank on 2009-05-10
Hi and welcome, I have limited knowledge of Wubi installations, but I believe you can reach recovery mode when selecting Ubuntu at the prompt press e instead and this will enable you to choose recovery mode.
Then you should be given 4 choices where you can choose xfix to repair graphical issues. 
Once xfix complete then you should be given the 4 options again and choose to boot normally. Hope this helps.

---

### Post by minathebrat on 2009-05-10
> **overdrank said:**
> Hi and welcome, I have limited knowledge of Wubi installations, but I believe you can reach recovery mode when selecting Ubuntu at the prompt press e instead and this will enable you to choose recovery mode.
Then you should be given 4 choices where you can choose xfix to repair graphical issues. 
Once xfix complete then you should be given the 4 options again and choose to boot normally. Hope this helps.

Hi! Thank you so much! I appreciate the help. What I did was, after I selected Ubuntu at the boot, it had a few second option to choose >esc<, so I figured this is what you meant. I had a couple of options TWO recovery modes- one was Ubuntu 8.10 2.6.27-11 generic recovery mode and the second one was Ubuntu 8.10 2.6.27.7 generic recovery mode. I picked the first one, and selected b to boot. Then it gave me the options you described, and I picked xfix and then rebooted! It worked!

So then I was back where I was, and this time I selected the driver that was NOT recommended and it rebooted and it's working! Ubuntu told me it was using unsupported drivers. If I go to Monitor Resolution Settings it gives me plenty of options! Yay!

I only have one small issue left and it's so embarrassing!!!, but I can't figure it out!  Under Monitor Resolution Settings, I'm trying to choose a nicer resolution...I think the current settings must be like 400x600. But the thing is, it's so HUGE I can't select it, because the select button is off the screen and I can't scroll down or move the window up!

Is there another way to do this? There has to be!
Thanks so much! You've been wonderfully helpful :)

---

### Post by minathebrat on 2009-05-10
Hi :)
Honestly, I never figured out how to resize the window, or get it to move, but I just started playing around with 'tab' and 'enter' trying to get it to input and eventually got it to re-size! lol
So, now everything is up and running the way it should be.
Thank you much overlord for your help.
Looking forward to being able to read thru the literature and understand how to work ubuntu better.

---

### Post by overdrank on 2009-05-10
> **minathebrat said:**
> Hi :)
Honestly, I never figured out how to resize the window, or get it to move, but I just started playing around with 'tab' and 'enter' trying to get it to input and eventually got it to re-size! lol
So, now everything is up and running the way it should be.
Thank you much overlord for your help.
Looking forward to being able to read thru the literature and understand how to work ubuntu better.

Good luck :)

---

