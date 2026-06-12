---
title: "Starting screens"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by jermza on 2011-01-08
My first experience with Ubuntu was 9.04.  Being a creative, I naturally compared the interface to Snow Leopard.  I was impressed with Ubuntu's polished look and decided to attempt a conversion.

What I liked was that the screen appeared blank with nothing but that little logo sitting in the middle, and then the login window appeared.

However, in 10.10, that's no longer there and the loading screen looks like a Windows DOS prompt.  Even the shutting down is messy and resembles a DOS prompt, which I don't remember happening in 9.04 and 9.10.

It's just all (become) so unpolished, which is disappointing because the operating system is the best it's ever been (especially for someone like me who likes design and attention to detail).

What are your thoughts?

---

### Post by cariboo on 2011-01-08
Plymouth is broken in 10.10, and more than likely won't be fixed. There are work arounds available, have a look [here]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html#more").

The developers are working hard on Natty, including getting plymouth to work no matter what graphics card you use.

---

### Post by jermza on 2011-01-09
> **cariboo907 said:**
> Plymouth is broken in 10.10, and more than likely won't be fixed. There are work arounds available, have a look [here]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html#more").

The developers are working hard on Natty, including getting plymouth to work no matter what graphics card you use.

I see.  SO it's related to the graphics card.  I have a fairly new Nvidia, which "has been tested by the Ubuntu community", but one can only hope that the developers clean up the clumsy starting / closing screens.

---

### Post by jermza on 2011-01-24
I've gotta say that, for a top class operating system, Ubuntu truly has the most untidy, unpolished boot-up screen I've ever seen.  I know it's related to the graphics card, but I'm the end user and I'm not supposed to worry about that.  It's supposed to work AND look polished.

All I know is that I have a current PC with the latest Ubuntu.  I brag about it to friends, telling them how much better than Snow Leopard it is, only to have the opening (delayed) boot-up screen looking like a DOS prompt from the 90s.

And then I read that it probably won't ever be fixed.  Which is disappointing.

---

### Post by andymorton on 2011-01-24
> **jermza said:**
> I've gotta say that, for a top class operating system, Ubuntu truly has the most untidy, unpolished boot-up screen I've ever seen.  I know it's related to the graphics card, but I'm the end user and I'm not supposed to worry about that.  It's supposed to work AND look polished.

All I know is that I have a current PC with the latest Ubuntu.  I brag about it to friends, telling them how much better than Snow Leopard it is, only to have the opening (delayed) boot-up screen looking like a DOS prompt from the 90s.

And then I read that it probably won't ever be fixed.  Which is disappointing.

Enter the following into a terminal and it should be ok

sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u

---

### Post by ivanovnegro on 2011-01-24
My graphic card is supported and it looks great.
If the graphic card is not supported it can look odd but this is not so important if the OS is working, what it does, compare the start up of Ubuntu with Windows or the shut down, Ubuntu is really fast!
I hope also in Natty they will fix this. :p

Addition: In my opinion what I see on the screen at boot or shut down is not important especially when it is going so fast, more important is the rest, that the OS is working great and fast.
But I can understand the point of asthetics also.

---

### Post by jermza on 2011-01-24
> **andymorton said:**
> Enter the following into a terminal and it should be ok

sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u

My graphics card is supported.

I'm worried about running that command.  What happens if Ubuntu doesn't load after I run that?

---

### Post by NightwishFan on 2011-01-24
If you are worried about it I would just bite the bullet for now. Plymouth the splash used in Ubuntu has some amazing potential. The reasons for the ugly one on some graphics cards is that it was judged better to have better reliability over looks. It can work, but you will need to do as suggested.
[http://www.youtube.com/watch?v=01eYYka3TIc](http://www.youtube.com/watch?v=01eYYka3TIc)

---

### Post by andymorton on 2011-01-24
> **jermza said:**
> My graphics card is supported.

I'm worried about running that command.  What happens if Ubuntu doesn't load after I run that?

I've used that command every time I've done a fresh install (which is quite a few) and it's never failed to work. But ultimately having the plymouth theme appear on boot up is just for aesthetics, so it isn't really that important. 

andy :)

P.S. When I said in my previous post that 'it should be ok' I didn't mean your entire system, I just meant that it should sort out the delayed loading of the plymouth theme. :)

---

### Post by jermza on 2011-01-24
> **andymorton said:**
> I've used that command every time I've done a fresh install (which is quite a few) and it's never failed to work. But ultimately having the plymouth theme appear on boot up is just for aesthetics, so it isn't really that important. 

andy :)

P.S. When I said in my previous post that 'it should be ok' I didn't mean your entire system, I just meant that it should sort out the delayed loading of the plymouth theme. :)

Thanks.  Well, there is no theme to speak of, when my Ubuntu loads.  

I turn on my machine and immediately see the graphic card's logo (along with those bios options), 
followed by a black screen with a blinking cursor (which takes a while to change),
followed by a message "too many connections",
followed by Ubuntu's "logo" (which is really a DOS-style word) with a few dots under it,
followed only THEN by the login screen.

My graphics card has the Nvidia package installed and says that it's been tested by the community, and it loads a colour profile correctly, so I assume that there isn't a problem with it.

Are you suggesting that I still run that command?  (Yes, I DO like the sexy aesthetics, but am scared it will break Ubuntu.)

---

### Post by sadaruwan12 on 2011-01-24
Yo buddy stop asking the same thing again and again if you want tot run it run it if you don't then don't. want more I candy try mint or any other remix of ubuntu there are thousands out there.

---

### Post by jermza on 2011-01-24
All I worried about is whether or not I'll be able to log into Ubuntu if the code doesn't work.

---

### Post by steve7777777 on 2011-01-24
> **jermza said:**
> All I worried about is whether or not I'll be able to log into Ubuntu if the code doesn't work.

You can Boot off Clonezilla CD and create an image of SDA as insurance.

Maybe you don't have the right temperament to run Ubuntu/Linux?  Is switching to MAC/Snow Leapard an option? Everything will look antiseptic and none of the messy stuff to look at. Of course the MAC is built on UNIX foundation, but the command line is hidden.

Good luck!

---

### Post by jermza on 2011-01-24
> **steve7777777 said:**
> You can Boot off Clonezilla CD and create an image of SDA as insurance.

Maybe you don't have the right temperament to run Ubuntu/Linux?  Is switching to MAC/Snow Leapard an option? Everything will look antiseptic and none of the messy stuff to look at. Of course the MAC is built on UNIX foundation, but the command line is hidden.

Good luck!
I'm not quite sure why I'm being attacked with, yet again, "help" in the form of "have you tried [insert something unhelpful]".  This is a beginner forum and I am a beginner asking beginner questions.  I am an Ubuntu convert and run only Ubuntu and am very happy.

If I wanted to run Snow Leopard, then I'd run Snow Leopard.

I've received some help already, but I'm just asking for guidance about what could happen if Plymouth doesn't load at all.  (That is, does Ubuntu load at all, if the given code malfunctions?)

Anyway, never mind.  I'll mark this thread as "solved".

---

### Post by Dr Small on 2011-01-24
> **jermza said:**
> All I worried about is whether or not I'll be able to log into Ubuntu if the code doesn't work.
Sitting around worrying about it gets nowhere. If you are afraid to run it, don't run it and don't worry about it. Otherwise, try it and find out. If the system would break (which I highly doubt it would), just boot up into root and fix the problem.

---

### Post by jermza on 2011-01-24
> **Dr Small said:**
> Sitting around worrying about it gets nowhere. If you are afraid to run it, don't run it and don't worry about it. Otherwise, try it and find out. If the system would break (which I highly doubt it would), just boot up into root and fix the problem.
And how do you boot up into root?

---

### Post by steve7777777 on 2011-01-25
> **jermza said:**
> And how do you boot up into root?

Did you try the solution provided? You shouldn't have to boot into root.

This doesn't exactly answer your question about booting into root but see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jermza on 2011-01-28
> **steve7777777 said:**
> Did you try the solution provided? You shouldn't have to boot into root.

This doesn't exactly answer your question about booting into root but see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Nope.  If anything goes wrong, then I'm not smart enough to know how to resolve it, especially because this is my only PC and the one I work on too.  I'll rather wait for the next release of Ubuntu and see what happens...

---

### Post by ivanovnegro on 2011-01-28
> **jermza said:**
> Nope.  If anything goes wrong, then I'm not smart enough to know how to resolve it, especially because this is my only PC and the one I work on too.  I'll rather wait for the next release of Ubuntu and see what happens...

So, wait untill the next release, maybe this is the best idea!

---

### Post by HiImTye on 2011-01-28
it shouldnt mess up your boot, but if it does then do this instead

```
sudo cp /etc/initramfs-tools/conf.d/splash /etc/initramfs-tools/conf.d/splash.old
sudo echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```and if you cant boot into ubuntu then boot into a shell (by ctrl+alt+f1 then logging into the terminal) and run the following command
```
sudo cp /etc/initramfs-tools/conf.d/splash.old /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
sudo reboot
```

---

