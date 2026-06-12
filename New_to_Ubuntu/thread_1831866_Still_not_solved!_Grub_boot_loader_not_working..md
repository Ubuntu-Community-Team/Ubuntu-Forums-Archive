---
title: "Still not solved! Grub boot loader not working."
date: 2011-08-24
forum: New to Ubuntu
---

### Post by inabitofapickle on 2011-08-24
Well a month ago i posted to try and get help with my grub boot loader. I tried to make it pretty with burg, and that didn't work. every time i boot up it says grub rescue and what not. I've tried live CD's but my laptop keeps saying remove disks / media press any key to reboot. I have NO CD slot seeing as this is just a netbook, and I'm really hoping to save the windows side if i can.  please some one explain to me how to fix this, give me directions like you'd give to an autistic child. please help!

---

### Post by jfed on 2011-08-24
Hello, I don't exactly know what your problem is as your post was a bit less than comprehensive, haha but there is a solution that might work. First, you have to tell me something, can you actually boot into Ubuntu at all? Without a livecd or anything, when you turn your computer on, can you boot into Ubuntu?

---

### Post by inabitofapickle on 2011-08-24
no i get the grub rescue screen. i cannot boot in to windows 7 either.

---

### Post by jfed on 2011-08-24
Okay, obviously you must have another computer, or you couldn't be writing this post right?

Do you have another computer you can use? Also, you said you tried LiveCDs, do you actually have a LiveCD with ubuntu on it handy at the moment?

---

### Post by inabitofapickle on 2011-08-24
I do. And live cd is the 4.1 gb ISO file right?

---

### Post by jfed on 2011-08-24
Not...quite. Thats a LiveDVD file, they're much bigger. Here is what you need to do. Download the Ubuntu 10.04 LTS CD iso, the one that is about 700megs, and burn it to a CD. 

I realize you can't use a CD on your netbook, but we'll get to that, also the reason I'm saying to do 10.04 is because I'm not completely familiarly with 11.04 to be honest, also I'm not sure if the same methods would even work..

So yes, thats possible for you right? To do that? I'm not trying to be condescending haha, I'm just asking. :P

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Select Ubuntu 10.04 LTS, and 32-bit, then click big orange download button. (I like that button :)

---

### Post by zirch on 2011-08-24
I've had a similar problem. Check out this thread: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It should at least be able to help you to boot into Windows.

---

### Post by jfed on 2011-08-24
Just for the sake of time, I'm going to explain what might fix your grub.

Don't burn the iso to a cd, i was wrong. Just follow this guide, and install it onto a usb stick.

[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

Once thats done, put it into your netbook, and boot from it. It might not do this by default, so you might have to look for something at startup that says press F# for boot menu, then just select usb.

After that, follow this guide:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Control+F or scroll down to where it says "Reinstalling Grub2"

That might do it. It worked for me when I had a similar problem with Fedora/ubuntu.

Or of course Zirch's guide might work too, even if they don't, reading is good for you! :D

---

### Post by inabitofapickle on 2011-08-24
okay. what the right licve cd for 10.10?

---

### Post by rj7 on 2011-08-24
worst case: If you need your windows partition and if you dont worry about your ubuntu just reinstall ubuntu in the same partition....
But there  are lot of better ways just google "grub rescue" you ll get the answer...
Also to install burg follow this
[http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/](http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/)

---

### Post by jfed on 2011-08-24
I hadn't thought of that..
:-k

---

### Post by rj7 on 2011-08-24
should be 10.04!!!!

---

### Post by inabitofapickle on 2011-08-24
yeah i got 10.04, just wondering; can i make it think its on the ubuntu partition and re-install the bootloader from the usb stick?

---

### Post by rj7 on 2011-08-24
ya sure you can definitely do...
and booting from usb is very easy....
if you have another Ubuntu running go to system>Administrator>Start up disk creator
Select the iso and usb....
If you dont have another ubuntu running download unetbooting...

---

### Post by inabitofapickle on 2011-08-25
okay. so i tried that. and it says operating system missing.

---

### Post by inabitofapickle on 2011-08-25
NVM! I GOT IT TO BOOT what do i do now?

---

### Post by inabitofapickle on 2011-08-25
new problem; my track pad does not  work

---

### Post by zirch on 2011-08-25
Which OS did you boot into? Try installing the drivers.

---

### Post by inabitofapickle on 2011-08-26
well i can only boot in to ubuntu live, i have to use an external mouse, when i use the ubuntu live usb it won't recognize the track pad, and for the last month I haven been able to boot in to either windows 7 home p. or ubuntu 10.10 (those were my two partitions)

---

### Post by zirch on 2011-08-26
Do you have your Windows 7 installation DVD or recovery disk?

---

