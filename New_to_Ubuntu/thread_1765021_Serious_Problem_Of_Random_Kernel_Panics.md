---
title: "Serious Problem Of Random Kernel Panics"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by zorbama on 2011-05-22
Hello people!

I'm a new user to Ubuntu, and this is my first forum thread here. I started using the operating system and immediately loved it. I was amazed how good it is.

There is, however, one serious problem I'm having: From the very first day of the installation, Ubuntu freezes at random points in time, I can't move the mouse or use the keyboard, and the caps lock and scroll lock leds are blinking on and off. I searched for this problem and realized it's a kernel panic.
Now, I tried many things I saw written on the Internet: tried reinstalling Nautilus, reinstalling my graphic driver, switching unity with the classic desktop, installing additional drivers, but nothing helped. If anything it's only getting worse, making kernel panics more often and sometimes right after the desktop showed up! I'm now using safe mode, and hopefully I won't have any trouble, but please help!

I'd send an error report, but I don't know where I can find one and if there IS one. In short, I'm a complete Ubuntu noob and am waiting for your advice.

I have:
Intel core 2 duo 6300 1.86 GHz
Ubuntu 11.04
nVidia 8500 GT graphics card

and if there's need of more information I'll gladly tell it.

Thanks in advance! :)

---

### Post by owenll on 2011-05-22
I had this problem for months until I came across this discussion on a bug. Might not be a solution to your problem but it worked for me:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720/comments/6)

in this thread 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720)

---

### Post by Gone fishing on 2011-05-22
Sounds like hardware to me. 

I'd be interested to know what temp your processor is running at is the heat-sink full of fluff?

What size is your power supply? Try a bigger one

Try running memtest - could easily be a RAM problem

Bet the problem is hardware

---

### Post by zorbama on 2011-05-22
onwell: Thanks, I tried doing what it said there, and I hope it helps. Checking it out now.

Gone fishing: Could you tell me how to check this stuff? As I said, I'm not very familiar with many things ^^;

---

### Post by cap10Ibraim on 2011-05-22
are you using unity ? did you try to login with Gnome 2.xx ?

---

### Post by corncob on 2011-05-22
> **zorbama said:**
> onwell: Thanks, I tried doing what it said there, and I hope it helps. Checking it out now.

Gone fishing: Could you tell me how to check this stuff? As I said, I'm not very familiar with many things ^^;

If its a tower you can start my taking the cover off and vacuum the dust off of everything (or take it outside and blow it off).  Make sure you clean the power supply too, fan and all. Do you have animals?  I've seen a computer clog up something awful from dander.

---

### Post by Gone fishing on 2011-05-22
Like Corncob says take the side off the case and use a vacuum cleaner - go to your PC store and get an aerosol blower better than nothing. The heat-sinks can really fill up with dust and fluff. You can read the temp of the CPU usually in BIOS or by using an application like conky or similar, but if after the PCs been running for an hour it feels hot (rather than warm) it's too hot.

Also instability can be caused by Power supplies often rubbish quality, work just about OK until you put a graphics card or sound card in. I don't know how you can tell if it failing other than does the problem go away if you get a bigger better one.

Memtest is on the grub boot screen run it for an hour any problems their shouldn't be.

---

### Post by zorbama on 2011-05-23
OK, so apparently what they said in that thread didn't work.

So I tried to do what you said and did some serious vacuum cleaning, and I hope it help, though I'm not sure it's the problem, since I didn't have that in Windows. I think it must be something inside Ubuntu.

---

### Post by zorbama on 2011-05-23
Right, so after cleaning up the computer (and quite thoroughly too), I'm STILL having kernel panics happening! It can't be a hardware problem, as it never happened in windows, and the computer seems fine. However, I don't know what it CAN be or how I can figure it out! Any suggestions? :confused:

---

### Post by hansolo4949 on 2011-05-23
If this issue is hardware related, which I think it's not, lay particular attention tk the fans on your computer. Do they spin up at all when using Ubuntu? If they do not, that is the issue. Ubuntu is not recognizing the temperature sensors in your machine, and because of that, is not spinning up the fans (I think). Has Ubuntu worked on this system before? Perhaps the kernel you have is bad?

---

### Post by zorbama on 2011-05-23
The fan is definitely working. I can hear it and I feel the breeze it makes.

What I think could be the problem is that bug of the graphic card driver not being in use. I now installed another driver, the free experimental one, and this one says that the driver is in use. It might have fixed that, but it's a little to early to tell.

---

