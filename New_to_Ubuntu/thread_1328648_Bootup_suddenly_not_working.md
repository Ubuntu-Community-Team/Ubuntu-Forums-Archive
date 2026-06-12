---
title: "Bootup suddenly not working"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by wrightak on 2009-11-16
Hi there,

I'm very new to Ubuntu and GNU/Linux but enjoying it very much.

I had a wonderful experience installing Ubuntu KK 9.10 using Wubi 4 days ago. The process was very smooth and I was very impressed at how it detected my obscure Japanese hardware. Even the function keys are working (they didn't work when I tried live CDs of Ubuntu in the past).

Anyway, I've been using Ubuntu happily for 4 days and last night I get a prompt to install a load of updates. I did this and continued using the machine normally and switched it off before going to bed. 

When I turned on the machine this morning, I selected Ubuntu instead of Windows XP (as I had been doing every day :)). It seems to encounter an error and instead of taking me to the normal menu, I get taken to a GRUB command line interface. 

I experimented with a few commands. ls showed me something like

(hd0,0)

and a few other things. 

I was pleased when a guess of "reboot" did exactly what I wanted it to.

I would be grateful if someone could help me repair the boot process. Not sure whether it's related to all those updates I installed yesterday.

---

### Post by Jon Monreal on 2009-11-16
> **wrightak said:**
> Hi there,

I'm very new to Ubuntu and GNU/Linux but enjoying it very much.

I had a wonderful experience installing Ubuntu KK 9.10 using Wubi 4 days ago. The process was very smooth and I was very impressed at how it detected my obscure Japanese hardware. Even the function keys are working (they didn't work when I tried live CDs of Ubuntu in the past).

Anyway, I've been using Ubuntu happily for 4 days and last night I get a prompt to install a load of updates. I did this and continued using the machine normally and switched it off before going to bed. 

When I turned on the machine this morning, I selected Ubuntu instead of Windows XP (as I had been doing every day :)). It seems to encounter an error and instead of taking me to the normal menu, I get taken to a GRUB command line interface. 

I experimented with a few commands. ls showed me something like

(hd0,0)

and a few other things. 

I was pleased when a guess of "reboot" did exactly what I wanted it to.

I would be grateful if someone could help me repair the boot process. Not sure whether it's related to all those updates I installed yesterday.

Try typing "startx" at the prompt, and seeing what happens.

---

### Post by wrightak on 2009-11-17
> **Jon Monreal said:**
> Try typing "startx" at the prompt, and seeing what happens.

Sorry for the delay. I did this and it says command not recognized. Do you have any other suggestions?

---

### Post by Jon Monreal on 2009-11-17
> **wrightak said:**
> Sorry for the delay. I did this and it says command not recognized. Do you have any other suggestions?

Try this: press ESC when it says Grub is loading. When the menu comes up, select the recovery option. When a menu comes up, select the option to "repair broken packages" allow it to finish completely (wait until you're sure) and then restart your computer.

I have a feeling that you shut down the computer while upgrades were still being installed; this can cause a problem like this, where X won't start (startx).

---

### Post by wrightak on 2009-11-17
Thanks for the reply. Unfortunately I'm back at work again and will give it a go when I get home. 

I'm pretty sure that I allowed the updates to finish, but perhaps something went wrong. 

I'll try and give a fuller description of what happens, just in case it helps:

I switch my Panasonic Toughbook Y5 on, and am presented with the options of Windows XP or Ubuntu.

I choose Ubuntu and usually I am then presented with another menu offering Ubuntu normal, Ubuntu safe mode and XP again.

Instead, the machine beeps at me, I think it fails to read something and then presents me with the GRUB command prompt. The error messages flash very briefly.

Only a certain set of commands are available to me, which I can see by pressing TAB. 

startx isn't one of those options.

I remember that some of the options available are: "linux", "reboot", "ls", and perhaps 15 others.

The time between selecting Ubuntu, the beeping, and the prompt appearing is very brief. I don't remember it saying that Grub was loading. I'll give it a shot though when I get home.

After reading the wubi FAQ, I tried to run "chkdsk /r" from XP. This failed to run because it said that another program was using the disk and offered to reschedule for a different time. "chkdsk" did run though. 

Sorry for the haphazard info - I haven't had a lot of time to look into it thoroughly. I thought I'd give you as much info as possible though.

Is this forum the right place to put this enquiry? Should I be directing this to a wubi forum somewhere?

---

### Post by Jon Monreal on 2009-11-17
> **wrightak said:**
> Thanks for the reply. Unfortunately I'm back at work again and will give it a go when I get home. 

I'm pretty sure that I allowed the updates to finish, but perhaps something went wrong. 

I'll try and give a fuller description of what happens, just in case it helps:

I switch my Panasonic Toughbook Y5 on, and am presented with the options of Windows XP or Ubuntu.

I choose Ubuntu and usually I am then presented with another menu offering Ubuntu normal, Ubuntu safe mode and XP again.

Instead, the machine beeps at me, I think it fails to read something and then presents me with the GRUB command prompt. The error messages flash very briefly.

Only a certain set of commands are available to me, which I can see by pressing TAB. 

startx isn't one of those options.

I remember that some of the options available are: "linux", "reboot", "ls", and perhaps 15 others.

The time between selecting Ubuntu, the beeping, and the prompt appearing is very brief. I don't remember it saying that Grub was loading. I'll give it a shot though when I get home.

After reading the wubi FAQ, I tried to run "chkdsk /r" from XP. This failed to run because it said that another program was using the disk and offered to reschedule for a different time. "chkdsk" did run though. 

Sorry for the haphazard info - I haven't had a lot of time to look into it thoroughly. I thought I'd give you as much info as possible though.

Is this forum the right place to put this enquiry? Should I be directing this to a wubi forum somewhere?

Ah, I thought you were saying you had a shell. In that case, no startx is not an option. Are you saying that you cannot even get to recovery mode? Can you list all of the options it gives you? I'm sorry, I don't use Wubi.

---

### Post by wrightak on 2009-11-17
> **Jon Monreal said:**
> Ah, I thought you were saying you had a shell. In that case, no startx is not an option. Are you saying that you cannot even get to recovery mode? Can you list all of the options it gives you? I'm sorry, I don't use Wubi.

Yep, I definitely can't get to recovery mode. I'm getting some kind of prompt that says "GRUB" at the top. I can't take a screenshot or copy and paste anything so I'll have to write it down or use a second machine side by side. 

If I had problems installing using Wubi, I would understand, but it seems odd that this problem came up so suddenly. Everything was working great for 4 days...

---

### Post by Jon Monreal on 2009-11-17
> **wrightak said:**
> Yep, I definitely can't get to recovery mode. I'm getting some kind of prompt that says "GRUB" at the top. I can't take a screenshot or copy and paste anything so I'll have to write it down or use a second machine side by side. 

If I had problems installing using Wubi, I would understand, but it seems odd that this problem came up so suddenly. Everything was working great for 4 days...

From what I've heard, Wubi can have problems that you would never encounter with a dual-boot standard install. That said, I'm hoping we can solve this problem without too much trouble.

---

### Post by wrightak on 2009-11-24
After reading this page:

[https://wiki.ubuntu.com/WubiGuide#Cannot](https://wiki.ubuntu.com/WubiGuide#Cannot) boot into Ubuntu

I decided to follow instructions and post this problem in a different section of the forum. I would be very grateful if you could continue with your help there.

Here's the link: [http://ubuntuforums.org/showthread.php?p=8377377#post8377377](http://ubuntuforums.org/showthread.php?p=8377377#post8377377)

Many thanks.

---

