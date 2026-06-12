---
title: "How to enable 3D Acceleration"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by aaronson2012 on 2010-07-14
Hello Everyone!

I am an absolute beginner to Ubuntu (and Linux), but I am very willing to learn.

What I am trying to do is enable 3D Acceleration. (because PlayOnLinux told me to do so) I have an NVIDIA GeForce 9800GT.

I have been reading through the forums and I do understand that there really is no straightforward answer for anything on here, Gotta jump through tons of hoops first.

So, if you can, please be as descriptive as possible.

And Thank you very much.

---

### Post by Zeike on 2010-07-14
Go to "System->Administration->Hardware Drivers" and make sure "NVIDIA accelerated graphics driver [version current]" is selected.  If it isnt, hilight it and click "enable", then you'll have to restart.

If its already enabled then 3D Accel should already be working.

I have this same card, it works flawlessly for me.

---

### Post by MooPi on 2010-07-14
There should be an icon on the top panel that looks like a PCI add-on card. This represents a program that will assist your installation of the Nvidia driver for your video card. Just click on this icon to start the process and follow the instructions.

---

### Post by mocoloco on 2010-07-14
Don't know why you think there's no straightforward answer.

[LIST=1]
[*]Click the **System** menu
[*]Point to **Administration** and click on **Hardware Drivers**
[*]After Ubuntu shows you a driver is available, select it and click **Enable**
[*]One it's downloaded and installed you'll be propted to reboot.
[/LIST]

You're done.

---

### Post by aaronson2012 on 2010-07-14
> **Zeike said:**
> Go to "System->Administration->Hardware Drivers" and make sure "NVIDIA accelerated graphics driver [version current]" is selected.  If it isnt, hilight it and click "enable", then you'll have to restart.

If its already enabled then 3D Accel should already be working.

I have this same card, it works flawlessly for me.

Thank you for the reply.

Yes, the driver is enabled and in use, but when I open the program "PlayOnLinux" It says, "You don't seem to have 3D acceleration! We advise you install and enable it." How do I fix that?

And by the way does anyone have any experience with this "PlayOnLinux" software? Or is there somthing better I can use to run my Windows based games?

---

### Post by staf0048 on 2010-07-15
> **aaronson2012 said:**
> And by the way does anyone have any experience with this "PlayOnLinux" software? Or is there somthing better I can use to run my Windows based games?

I have not had the issues you're having POL myself, but it's just a wrapper for Wine.  So, you could try just using Wine itself, but in my experience POL does a good job of setting the game program up properly for you.  You could always use Wine and try playing with the settings to see if you can do better.

---

