---
title: "Ubuntu Black screen?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by nu2buntu0 on 2010-05-11
Hello, I've been trying to try the demo of Ubuntu and just entering the disc alone does not help.

After learning the shortcut F6, I used it when I entered the Ubuntu disc, and I was able to access a menu.

I selected the first choice try without installing, and after two or three minutes I hear a song, I'm guessing that means it's working.

However, that shortcut I've heard on the forums ALT+CTRL+F1 does not work, and it seems like my keyboard itself does not work with Ubuntu, and my screen is black and cannot see anything.

Any help? :)

---

### Post by overdrank on 2010-05-11
Hi and welcome, could you tell us some system specs? 

Moved to Absolute Beginner Talk

---

### Post by nu2buntu0 on 2010-05-12
My computer is a Compaq, was Windows XP upgraded to 7.
It uses a NIVIDIA GeForce 6150 LE Graphics Card and it has 1 GB of RAM. It is 2005 technology, being made in 2007.

I don't know much else sorry.

---

### Post by overdrank on 2010-05-12
> **nu2buntu0 said:**
> My computer is a Compaq, was Windows XP upgraded to 7.
It uses a NIVIDIA GeForce 6150 LE Graphics Card and it has 1 GB of RAM. It is 2005 technology, being made in 2007.

I don't know much else sorry.

Hi, thats good info. :) 
I see in your first post that you know about the options under the F6 key. You can reach these options by pressing the esc key when you boot the cd.

Have you tried to edit the kernel line where it says boot options?
You can remove the quiet splash with the backspace key and then enter vga=771. This may help with the graphics. 
You may also check the cd for errors and burn it a the slowest speed possible.

---

### Post by nu2buntu0 on 2010-05-12
Thanks! I'll try that.

---

### Post by nu2buntu0 on 2010-05-12
It seems as if the same results.
Although as usual it's black while it loads, and the keyboard is not detected, after I hear the music the keyboard is detected by Ubuntu. However, the visuals are still black.

---

### Post by overdrank on 2010-05-12
> **nu2buntu0 said:**
> It seems as if the same results.
Although as usual it's black while it loads, and the keyboard is not detected, after I hear the music the keyboard is detected by Ubuntu. However, the visuals are still black.

Ok, have you checked the cd for errors?
 You may also check the [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") on the iso before you burn the cd.

---

### Post by nu2buntu0 on 2010-05-12
I checked already it passed through everything with no problem.

---

### Post by Catharsis on 2010-05-13
At the menu, press F6 and then Esc to edit the boot line. Then remove "quiet splash" and replace it with "nomodeset". See if that works.

---

### Post by nu2buntu0 on 2010-05-13
Thanks I will try that.

---

### Post by nu2buntu0 on 2010-05-13
Today my dad had just bought an old Windows 95 computer, is it possible for it to be upgraded in to Ubuntu also?

---

### Post by EssexEagle on 2010-05-13
> **nu2buntu0 said:**
> Today my dad had just bought an old Windows 95 computer, is it possible for it to be upgraded in to Ubuntu also?

Will depend on the specs, but even if it can't run Ubuntu I'm sure there will be some Linux distribution that will work.

---

### Post by nu2buntu0 on 2010-05-13
Thank you for the reply!

Anyway, I got it to work although I want to know a few things before installing Ubuntu:

1. If I install Ubuntu what settings do I go to if I want the screen to turn normal instead of black?

2. The installing guide for Compiz isn't very well explained or I am very slow. Can someone show me how?

Thanks for all your help guys!

---

### Post by nu2buntu0 on 2010-05-13
Sorry for bumping the topic but I am really eager to get this installed :)

---

### Post by Catharsis on 2010-05-14
> **nu2buntu0 said:**
> 1. If I install Ubuntu what settings do I go to if I want the screen to turn normal instead of black?

You haven't told us what you did to make it work, so we can't really tell you :P

---

### Post by nu2buntu0 on 2010-05-14
I did what the last member suggested replace quiet splash with no mode set.

Also, can I always adjust the RAM and CPU of the two OSes?

So for example on day I want windows to have 600 mb of ram and ubuntu to have only 400, and then another day I want the reverse. Is this possible?

And also please answer my previous questions, thanks a bunch!

---

### Post by admiralspark on 2010-05-14
Well, I haven't checked the OP yet, but as for Ram....
Ram is used in it's entirety by whichever operating system is currently active. The only exception is if you're running ubuntu in a Virtual Machine, meaning its running while windows is too. In that case, you can key in exactly how much of the ram should be given to either OS.
But Ubuntu doesn't function as fast or well running in a VM, and loses some of it's functionality. If you've installed Ubuntu like normal, it uses all the ram; if you start windows instead, that will use the ram.

---

### Post by nu2buntu0 on 2010-05-14
So in other words there is an option to set for RAM to be completely used on which ever OS is currently being used?

Also as I said before the installation probably adds the quiet splash I guess I just go into advance options to edit this?
Thanks.

---

### Post by Catharsis on 2010-05-14
There is no option for RAM. Whichever OS is running uses all the RAM. If you have Ubuntu loaded, that means Windows isn't, so why would your computer keep some RAM free for Windows? They can't run at the same time....

To get your computer to boot:
1) Hold down Shift as you boot to get to the grub menu.
2) Hit 'e' to edit. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.

From there you should install your nVidia drivers through System->Administration->Hardware Drivers. If the proprietary nVidia drivers don't fix it, you can make the above fix permanent by:
```
gksudo gedit /etc/default
```
Change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```
Then save and exit. Then run:
```
sudo update-grub
```

Re:Compiz:
Compiz is installed by default. To disable it, go to:
System->Preferences->Appearance->Visual Effects (Tab), and select "None". I don't really understand what else it is you mean by "install compiz".

---

### Post by nu2buntu0 on 2010-05-14
My graphics are set to normal, I don't have a Compiz Manager.
Shouldn't this be included? Or are they separate files that change the closing and entering appearances?


By the way, wrote this with Ubuntu :)

Also, I find the tutorials here are very complicated:

[I]How do I use Compiz?
How can I install flash?[/I]

Thanks for the help!

---

### Post by nu2buntu0 on 2010-05-14
AH I got Compiz to work, now can someone help me with how to install flash? Then I'll be a happy camper :)

---

### Post by Catharsis on 2010-05-14
I turn Compiz off immediately after I install, so I really couldn't tell you anything about it, sorry.

---

### Post by Catharsis on 2010-05-14
> **nu2buntu0 said:**
> AH I got Compiz to work, now can someone help me with how to install flash? Then I'll be a happy camper :)

[http://www.psychocats.net/ubuntu/flashkarmic](http://www.psychocats.net/ubuntu/flashkarmic)

---

### Post by nu2buntu0 on 2010-05-14
THANK YOU! I love Ubuntu and you guys are great, thanks for all the support!

Cheers!

---

