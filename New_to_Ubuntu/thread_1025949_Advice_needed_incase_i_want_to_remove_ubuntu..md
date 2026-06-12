---
title: "Advice needed incase i want to remove ubuntu."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Oz-1313 on 2008-12-30
Hi there, 
Ive got a Live CD with Ubuntu on it from linux format magazine.  Ive played with linux a few times and like it, and am quite drawn by the speed of it as vista runs soo slowly on my laptop at times.  I like not having to worry about viruses also!  

I have a couple of questions though.

I have tried to install it form the option within the Live boot and when i get to a partitioning section it doesn't continue. it says it is about to repartition, gives an error saying it cant do it and no more explanation.  I have read that going back into windows and doing a full de frag should solve the problem but haven't tried this as yet.

I also would like to know what happens if in a few months time i decide that linux is not for me?  I plan on giving it plenty of time to try it out etc but in the scenario that i don't wish to use it, am i able to "uninstall" ubuntu? (i know its an OS so it doesnt uninstall but i dont know the correct word!)  Will i get back all the partition i set aside in the first place and will it do this automatically?

Any help it greatly appreciated.

Thanks Rob

---

### Post by oilchangeguy on 2008-12-30
this may help:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

and this:
[http://ubuntuforums.org/showthread.php?t=475281](http://ubuntuforums.org/showthread.php?t=475281)

---

### Post by Michael.Godawski on 2008-12-30
hi  Oz-1313,

perhaps you can read this article about switching from windows I have written: 

[LIST]
[*][http://www.godawski.oxyhost.com/switch.html](http://www.godawski.oxyhost.com/switch.html)
[/LIST]
> 
Will i get back all the partition i set aside in the first place and will it do this automatically?

No. You will have to recreate the partitions Ubuntu will create during the installation. Windows cannot use the ext3 partition type which Ubuntu uses. But you can do this very easily with the application called Gparted, which is also on the Live CD.

I would recommend doing a dual-boot for some time. I have a link posted in the article.
Then when you like what you see, and all your hardware is set up correctly you can make the switch perfect.

If you have questions concerning the dual-boot feel  free to ask.

PS: Welcome to the Community :D

---

### Post by jimmy the saint on 2008-12-30
First, go into vista, defrag the drive and shrink the main partition to free up whatever you can spare.  10 Gigs should be ok to play with, but if you plan to use Ubuntu regularly you should do at least 20 (for file storage and such).

Then you have two options: standard dual boot or wubi.
Standard:  you install Ubuntu to the empty space created by shrinking the main partition.  The plus is that the wubi installer can be a little buggy for some people and you can avoid that.  The downside is that you have to know what you are doing.  
Wubi:  Much simpler.  It runs as a windows program and does everything (installation related) from within windows, so if you are not very experienced, it is likely the way you will want to go.  Also, I understand it makes removing Ubuntu pretty simple as well.
see this guide: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I recommend Wubi.  If you use it, peruse the guide first, and make a FULL BACKUP before you do anything!!!  I cannot stress that enough.  Anytime you mess with partitons and OS installs you run the risk of losing everything if there is a power outage or an error.  

This forum is filled with Dual Boot threads that should address any questions you have, but if you need any help, feel free to ask questions and we will do our best to help you out!

Good Luck
JTS

---

### Post by kansasnoob on 2008-12-30
> **Oz-1313 said:**
> Hi there, 
Ive got a Live CD with Ubuntu on it from linux format magazine.  Ive played with linux a few times and like it, and am quite drawn by the speed of it as vista runs soo slowly on my laptop at times.  I like not having to worry about viruses also!  

I have a couple of questions though.

I have tried to install it form the option within the Live boot and when i get to a partitioning section it doesn't continue. it says it is about to repartition, gives an error saying it cant do it and no more explanation.  I have read that going back into windows and doing a full de frag should solve the problem but haven't tried this as yet.

I also would like to know what happens if in a few months time i decide that linux is not for me?  I plan on giving it plenty of time to try it out etc but in the scenario that i don't wish to use it, am i able to "uninstall" ubuntu? (i know its an OS so it doesnt uninstall but i dont know the correct word!)  Will i get back all the partition i set aside in the first place and will it do this automatically?

Any help it greatly appreciated.

Thanks Rob

First thought:

You say, "Ive got a Live CD with Ubuntu on it from linux format magazine". What version of Ubuntu is it?

Second thought:

You don't specifically say what version of Windows you're running!

But as an answer to your question:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Oz-1313 on 2008-12-30
Hi guys thanks for your quick replies!

Its a cd with ubuntu 8.10 for reference.

I have decieded not to install on my laptop just now, i assume that if i didnt got through with the whole install then i wont have redone any partitions etc? I am seeing back in vista that my c: drive is nearly at my full hard disc capacity (minus the recovery drive and some space for the vista install which i imgine is big!)

I still plan on running ubuntu though, i have an old desktop pc which im going to install ubuntu on so that i can try things out over a longer period of time.  Im just not confident enough with my computing knowledge and skills to run it on my main machine.  I was bad enoguh with that install just fretting about wiping my system and loosing all my data or somehpw making all my disc space disapear!!

Thanks for the advice, the guides will be very usefull for my install to the desktop, if anything goes wrong with that, then its not a problem, i wasnt using it anyways!
  Hopefully down the road ill be fluent enough to make the switch on my main machine.

Sure it wont be long till im calling for help once more!

Thanks again, Rob

---

### Post by kansasnoob on 2008-12-30
> **Oz-1313 said:**
> Hi guys thanks for your quick replies!

Its a cd with ubuntu 8.10 for reference.

I have decieded not to install on my laptop just now, i assume that if i didnt got through with the whole install then i wont have redone any partitions etc? I am seeing back in vista that my c: drive is nearly at my full hard disc capacity (minus the recovery drive and some space for the vista install which i imgine is big!)

I still plan on running ubuntu though, i have an old desktop pc which im going to install ubuntu on so that i can try things out over a longer period of time.  Im just not confident enough with my computing knowledge and skills to run it on my main machine.  I was bad enoguh with that install just fretting about wiping my system and loosing all my data or somehpw making all my disc space disapear!!

Thanks for the advice, the guides will be very usefull for my install to the desktop, if anything goes wrong with that, then its not a problem, i wasnt using it anyways!
  Hopefully down the road ill be fluent enough to make the switch on my main machine.

Sure it wont be long till im calling for help once more!

Thanks again, Rob

Well, you can always try the Live CD, just choose to "run with no changes to your computer".

If you like it try Wubi:

[http://www.wubi-installer.org/](http://www.wubi-installer.org/)

It's not quite as good as a true dual-boot but it's OK other than really not liking power outages, etc!

There is definitely a learning curve between Win and Ubuntu! Mine was about 30 days!

Now I find it actually painful to use Windows!

---

