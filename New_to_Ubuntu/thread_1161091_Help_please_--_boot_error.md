---
title: "Help please -- boot error"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by mkirizarry on 2009-05-16
Good Morning!  :p  I am new to Ubuntu.  I received I received the desktop edition 9.04 cd in the mail yesterday.  I am very excited about learning more. 
I followed the installation instructions carefully for the side by side install.  When I rebooted I am receiving Grub error 21 and then nothing happens.  I am still able to boot from the cd, which is what I am uing right now.  I would still like to be able to acess my windows xp and learn ubuntu at the same time.  
I have been out of the loop as far as computers are concerned for a few years, but am going back to school for computer applications and computer science.  If someone could please advise I would be very grateful.    ):P Thank you!!

---

### Post by bumanie on 2009-05-16
Please post the output of > sudo fdisk -lfrom terminal. To get to terminal Applications --> Accessories --> Terminal 
That is a lower case L, not the digit one.

---

### Post by mkirizarry on 2009-05-16
I tried to go to applications - accessories - terminal.  all I get is a blank white window??

---

### Post by bumanie on 2009-05-16
You should get a window that looks like the one in the middle of the screenshot. If you are getting a blank terminal, there must be some other issue. What are your computer specs?

---

### Post by mkirizarry on 2009-05-16
Still just a blank white window.

---

### Post by goldblattster on 2009-05-16
hello, and welcome to the ubuntu forums. ):P
Terminal *is* a blank white screen. Terminal is where you can enter BASH commands in Linux, kinda like the command prompt is where you enter DOS commands in windows. However, inside the terminal when you first start it, you should see
```
yourusername@yourusername-laptop:~$
```
or, if you are using a desktop,
```
yourusername@yourusername-desktop:~$
```
I have attached an image of an example of what it might look like.
Once terminal is loaded, like the other guy said, please post what you see after you type in
```
sudo fdisk -l
```
and hit the enter button. Also, when you his the enter button, it will probably need your password, which is ok. Cheers! ;)

---

### Post by mkirizarry on 2009-05-16
Could it be that because I booted from the cd that I am not getting the correct window.  I understand that something should be there, but still am just getting a blank window??  very confused!!

Peace, Miki

---

### Post by goldblattster on 2009-05-16
Ok. First, Make sure all your windows have an orangeish colour scheme. Then, go into terminal, and right click anywhere in the terminal. Then go to profiles>profile preferences. Select the colours tab, and make sure that the "use colours from system scheme" box is checked. Then click close. If the terminal does not let you right-click or if that or changing it to the defualt colour scheme does not work, tell me (or someone else)

---

### Post by goldblattster on 2009-05-16
please post if it does not work, because I believe I know a workaround.

---

### Post by mkirizarry on 2009-05-16
> **goldblattster said:**
> please post if it does not work, because I believe I know a workaround.
Thanks, I will try to work through that and let you know what happens.
Please bear with me for a couple of questions though.  Since I already did an install, is there a way to uninstall or can I just leave it.  And second if I do a install on my second drive with the windows drive unplugged should I do a side by side or a full install where it wipes the second drive clean and then installs,  I have lots of info on my secondary drive and since I cannot seem to access it right now I don't know how I would move all my files to my external hd. 

Thank you so much for taking your time to help me!!:D

Peace, Miki

---

### Post by goldblattster on 2009-05-16
You are very welcome.
Question 1: You already installed ubuntu, so it is on your hard drive, just like windows. Just like in windows if you have it on your machine, then the only way to remove it is to format the hard drive and install linux/windows/mac os again. However, if you installed ubuntu on a seperate partition, you can just format that partition and ubuntu is gone.
Question 2: If you do an install on your second drive and the only thing on it is files, you cannot do a side-by-side install. If you do a clean install on your second drive, your files will be gone. When doing a clean install on the second drive, I believe you should be able to boot from your second drive as well as your windows drive, provided windows is on your windows drive. Since your files seem to be gone, your hard drive *may* have failed. Before freaking out, maybe you could try to plug your second drive into another computer to see if it really has failed.

---

### Post by sailor2001 on 2009-05-16
interjecting...........download and burn "super grub" very handy disk when losing start-up manager

---

### Post by mkirizarry on 2009-05-16
I checked the color scheme.  Settings seem to be correct. Still just a blank window.

---

### Post by mkirizarry on 2009-05-16
Thank you!  Where do I find "Super Grub"?

---

### Post by mkirizarry on 2009-05-16
I found all my files where they were supposed to be.  I just had too dig for them.  Someone suggested downloading "super grub".  I think that sounds like something I will try before wiping out a drive with lots of files on it.  It appears that both windows and ubuntu are present, just need to figure out booting.  Thanks.

Peace Miki

---

### Post by goldblattster on 2009-05-16
Hello. Try the keyboard shortcut Alt+F2 and then type in xterm and hit enter. You should now have a working terminal that is less pretty than the normal one but works the same.

---

### Post by KCormier on 2009-05-16
error 21 means that grub is installed as your boot loader but it cannot find it's configuration files in order to boot correctly.

You shouldn't need to wipe ANYTHING.  You just need to fix grub.  Can you please boot to the cd, but when it first loads, select to check your disk(s) rather than boot into ubuntu.  The fact that terminal doesn't open correctly (just a blank screen) makes me think you might have a defective CD and that's why your install has failed.

-Kevin

---

### Post by goldblattster on 2009-05-16
Actually, super grub should fix your problem. Now it is just a matter of the problem of the blank terminal window. Ubuntu forums solved one of your problems! Huzzah!  :p

---

### Post by goldblattster on 2009-05-16
> **KCormier said:**
> The fact that terminal doesn't open correctly (just a blank screen) makes me think you might have a defective CD and that's why your install has failed.

I thought she said she recieved her cds in the mail?

---

### Post by KCormier on 2009-05-16
i agree goldblattster that supergrub will get the computer to boot but god knows what will happen after that if his disk really is corrupted.  If the only problem was booting I'd agree with you but i'm more interested in seeing if the whole of ubuntu is corrupted.  If that's the case I'd say just clear the mbr and go back to windows & download a new copy of ubuntu if that's possible.

The cds were mailed but that doesn't mean anything.  They may be MORE reliable but they're still not perfect.

-Kevin

---

### Post by goldblattster on 2009-05-16
> **KCormier said:**
> i agree goldblattster that supergrub will get the computer to boot but god knows what will happen after that if his disk really is corrupted.  If the only problem was booting I'd agree with you but i'm more interested in seeing if the whole of ubuntu is corrupted.  If that's the case I'd say just clear the mbr and go back to windows & download a new copy of ubuntu if that's possible.

The cds were mailed but that doesn't mean anything.  They may be MORE reliable but they're still not perfect.

-Kevin
Yeah, your right. *sighs*

---

### Post by mkirizarry on 2009-05-16
> **goldblattster said:**
> Ok. First, Make sure all your windows have an orangeish colour scheme. Then, go into terminal, and right click anywhere in the terminal. Then go to profiles>profile preferences. Select the colours tab, and make sure that the "use colours from system scheme" box is checked. Then click close. If the terminal does not let you right-click or if that or changing it to the defualt colour scheme does not work, tell me (or someone else)

:p WOW!! Lot's of good feed back!!  I got a working terminal window open now and will attempt to download "Super Grub"  and see if that works.  

Peace, Miki

P.S.:  I will post with outcome;)

---

### Post by goldblattster on 2009-05-16
You mean the xterm terminal I showed you, right? If you want to use the defualt terminal I might have a "quick' fix.
EDIT:You may take your time with the super GRUB before venturing into the terminal topic.

---

### Post by mkirizarry on 2009-05-16
Yes, I got the xtreme terminal working.  But I have to be honest, I am starting to feel really dumb here.  Also I am feeling really lost  I went to download super grub, but since I do not have a dvd burner on my computer I tried to follow the directions to download onto a pen drive and got lost.  Boy, it really shows how far behind on this stuff I have fallen.  Sure am glad I am going to school.

---

### Post by goldblattster on 2009-05-16
Are you doing it from the live cd? That should work...
I thought supergrub was a CD, not a DVD. It's DVD now? 
*hides in corner*
"evil modern technology!"

---

### Post by mkirizarry on 2009-05-16
My dumb, I meant cd.  I am trying to download from the website.  It says I need to burn a live cd.  Which I can not do without a burner.

Peace, Miki

---

### Post by KCormier on 2009-05-16
if the cd drive is that old, it may be an issue with your cd drive.  Did you try testing the cd when it boots?  Did the cd pass?

-Kevin

---

### Post by mkirizarry on 2009-05-16
Yes, I tested the cd, it came up good, no problems.

I have windows xp booting just fine now.  But still can only boot ubuntu from live cd.  Come on this all really can not be this hard to do.  Every thing I read says says it is simple.

Can I uninstall ubuntu from windows, and then try reinstalling it.  Or What???  I am not very happy with the way this is going.

Peace, Miki

---

### Post by goldblattster on 2009-05-16
Assuming you ***partitioned*** your hard drive and only if you partitioned your hard drive, you can locate the ubuntu partition in windows and format it, no?

---

### Post by mkirizarry on 2009-05-17
Ok, I am ready to throw my hands up.:???:

I formatted the partitions and attempted to install ubuntu again.  Still will not boot. 

One last question, at least for tonight.  Is it really ok to install ubuntu within windows xp?

If that does not work, I will just have to wait until I get another computer and can actually afford to try something new.  

Thank you to all who posted suggestions!

Peace, Miki

---

### Post by goldblattster on 2009-05-17
Hello again! Virtualization is free and painless. Not to mention far safer than messing around with partitions... At least in my expierence, however it can be a bit sluggish... :???: basically, you can download and install Virtualbox at Virtualbox.org. It is pretty self explanatory, however there is a nice article you can check out [here]("http://http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox").

Happy Virtualboxing!

---

### Post by mkirizarry on 2009-05-17
Thank you,  will try later on.  Too hot here to stay cooped up inside on computer.  Have a Great Day All!!

---

### Post by goldblattster on 2009-05-17
No problem :p

---

