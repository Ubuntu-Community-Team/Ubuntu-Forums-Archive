---
title: "New Problems with Old Computer"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Miss Kitty on 2009-06-08
[FONT=Times New Roman][SIZE=3]Being an Absolute Beginner, even though I skimmed through Ubuntu Linux For Dummies, I found no keyboard equivalents for the Windows Escape Key or the infamous Ctl-Alt-Del combo. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]This old HP Pavilion 7840 on which I just installed Ubuntu 8.10 (after some installation problems) froze up completely while I was glancing through some of the options on the top panel. I suspect an integrated video chip - but more investigation is necessary there. I ended up just hitting the Power button. I hate doing that.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]My question is, is there a better way to forcefully shut down than that? Like the Ctl-Alt-Del in Windows? (I did try that, it did not work). [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Another "Beginner" question - I have lots of diskettes and CDs with Windows Utilities programs, such as video testing, memory testing, hard drive testing, etc. Will these Windows utilities work with Ubuntu the only OS on the computer? :confused:[/SIZE][/FONT]

---

### Post by keplerspeed on 2009-06-08
Ctrl-alt-del will open up the shutdown menu, try it when th GUI is working fine.

To shutdown if the GUI crashes, press ctrl-alt-f1, log in to this terminal based session. From there you can enter this command to restart:
```

sudo shutdown -r now

```

I dont see why those win utilities wouldnt work, however, for HD testing win wont like ext3.

---

### Post by CJ Master on 2009-06-08
First install the Dontzap package by [Here.](apt:dontzap)

Run:

sudo dontzap --disable

Now if you press Ctrl+alt+backspace, it'll close all programs and return you to the login screen.

Edit: Keplerspeed's version will work, but it will restart, while my instructions will simply force logout. Use whatever you want.

---

### Post by Miss Kitty on 2009-06-08
Clicking on Here in your message sends me to a new window, "Cannot Find Server" Did you actually provide me with a link to the dontzap program?

---

### Post by CJ Master on 2009-06-08
My apologies, I'm running arch so I didn't know it wouldn't work for you, but I'm not quite sure why it doesn't work...?

Regardless, you can install it by running the terminal and entering:

```
sudo apt-get install dontzap
```

Wait.... you're running Ubuntu 9.04 right? If not, then you don't need Dontzap. Just press Ctrl+alt+backspace.

---

### Post by logos34 on 2009-06-08
How much RAM do you have?

in a terminal type:

> free -m

You don't need those windows utilities discs/diskettes because there are linux-based equivalents for all of them, i.e. memtest86+ (on your boot menu), e2fsprogs, gparted, hdparm, smartctl (smartmontools), etc.

---

### Post by Miss Kitty on 2009-06-08
To CJ  --  No - Ubuntu 8.10.  Also, this computer is not hooked up to my network, to enable it to get to internet. Whatever I download will have to be from my Windows XP computer and copied to a CD unless I change the floppy drive on the old one first.
 
To logos34:  Love your cat!!! I installed 512 megs of ram just recently; the BIOS recognizes it. That's all this motherboard will allow.

---

### Post by logos34 on 2009-06-08
> **Miss Kitty said:**
> To logos34:  Love your cat!!!

no, that's me! Really!

> I installed 512 megs of ram just recently

just thought i'd check...that's plenty

---

### Post by Miss Kitty on 2009-06-08
[quote=logos34;7419282]no, that's me! Really!
 
Purrrty kitty! I have one who looks a lot like ?you?

---

### Post by logos34 on 2009-06-08
> **Miss Kitty said:**
> I have one who looks a lot like ?you?

your gray cat looks a lot like a brother of mine...his name was Smoke

---

### Post by CJ Master on 2009-06-08
> **Miss Kitty said:**
> To CJ  --  No - Ubuntu 8.10.  Also, this computer is not hooked up to my network, to enable it to get to internet. Whatever I download will have to be from my Windows XP computer and copied to a CD unless I change the floppy drive on the old one first.
 
To logos34:  Love your cat!!! I installed 512 megs of ram just recently; the BIOS recognizes it. That's all this motherboard will allow.

Ah! Then, like I said, just press Ctrl+Alt+Backspace, and it should return you to login screen. :D

---

### Post by Miss Kitty on 2009-06-08
> **logos34 said:**
> your gray cat looks a lot like a brother of mine...his name was Smoke
 
This one's name is Smokey as well. He is my second Smokey (I didn't name him). My first Smokey I had for 19 years. I still miss him.

---

### Post by logos34 on 2009-06-09
> **Miss Kitty said:**
> This one's name is Smokey as well. He is my second Smokey (I didn't name him). My first Smokey I had for 19 years. I still miss him.

I feel your pain.  It's very sad when we lose a cat, or any pet. :(  If only they could live just a little longer! 16, 17, 18, 19 yrs is still not enough...One minute you're cursing them for dragging in a dead lizard (but you can never stay mad at the little guys, can you?), and then the next day they're gone, and it's really hard.  Your new Smokey looks like a neat little fella!

So, is your machine still freezing up when you browse through the panel menus?  Your specs are fine (plenty of ram)...If it is the video like you say, you might consider looking for a dedicated pci graphics card--don't need anything fancy or high-end...Something in the $25 range...added bonus is it won't be stealing system memory...

A shot in the dark: You might check panel>system>prefs>appearance>visual effects tab -- should be set to 'none'.  If it's set to 'normal' that might be enough to be causing a problem but otherwise be unnoticeable.

---

### Post by Steelmourne on 2009-06-09
Ctrl-Alt-Del brings up a menu listing if you want to suspend hibernate etc. You could install gnome-do. Then press super (windows key) + space and type shutdown or restart into the search box. After the first few letters hit enter. As for the utilities look them up in the wine database: appdb.**wine**hq.org/.

---

