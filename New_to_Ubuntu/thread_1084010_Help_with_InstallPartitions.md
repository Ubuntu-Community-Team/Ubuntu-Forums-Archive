---
title: "Help with Install/Partitions"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-01
Compete beginner here...just to forewarn all.  I have a 110 gb hd that i partioned 30 gb for ubuntu. the remaining 80 gb runs xp. i checked my disc and there are no errors. i believe i'm supposed to choose manual, as I've already partioned the hd. This is where I get lost. I'm suppose to create 2 additional partions within my 30gb?  do i do this through the insall process? if so, are there detailed instructions on how to do this? again, this is all new, so a lot of the terminology i'm unfamiliar with. After I click on manual, I see,
/dev/sda
 /dev/sda1  ntfs     35799mb   3221 mb
 /dev/sda5  ntfs     84243mb   10606 mb

this is the point that i don't know what to do.  is it easier to remove the partition and use the Guided option?  Thanks in advance.

---

### Post by thtrgremlin on 2009-03-01
The easiest way I see doing it is to start up to the desktop on the live CD, go to Applications -> Accessories -> Terminal. In the terminal type gksudo gparted. From there, delete the 30GB partition and leave it as free space. Save changes to disk, close gparted and the terminal, and run the installer.

When the installer asks where you want to install, instead of doing a manualsetup, you can just tell it to use the largest available free space, and all should go well from there.

If you are new, I believe this is your best option without having to dive into too much new stuff too quickly.

Let me know if you have any questions.

---

### Post by TeoBigusGeekus on 2009-03-01
Choose your 30gb partition.
Create a new partition in there of about 1gb and declare that it will be used as swap (additional ram so to say-whenever your system runs out or memory it will be used as auxiliary).
The remaining 29gb should be reformatted as ext3 (much better than ntfs) and have / as mount point. This will declare to the installer that the root partition will be there.
For further more detailed info, read this
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html")

---

### Post by handy on 2009-03-01
Have a look on the list of well written how-to's on the following page?  This page is well worth bookmarking for future reference:

*_[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)_*

---

### Post by js@lloyd on 2009-03-02
i tried using gremlin's way, as my lack of knowledge is keeping me from going the manual route.  unfortunately, it quit in the middle of deleting the partition and seem to direct me to the manual route.  being as green as i am, i'm afraid i need a step by step for the manual install.  i tried some of the provided links, but the version seems different than the newest version i'm tyring to install.    :confused:

---

### Post by thtrgremlin on 2009-03-02
gparted just quit in the middle of the operation? strange.

I thought that way would be the easiest. I played around with an installer in a Virtual Machine trying to copy your situation, and after doing it a few different ways, I thought that would be the most straight forward, but evidently not.

So the next way of going about it would be to just use the installer.

So here are some step by step directions.

[INDENT]1. Boot to the installer as you have done before and get to the part where it asks you to partition.

2. Select the manual option, and click 'forward'

3. Select your 30 gb partition and delete it.

4. Select the unused space and create a new partition whose size is equal to your amount of ram. tell it to put this partition at the end of the empty space. under format you want to select 'swap'. After selecting swap you will see most all the other options 'grey out'. That is because it is special.

5. Next, select the remaining empty space and create a new partition. You want the 'mount point' to be '/' aka 'root'. If you select it from the menu, it will just be the slash. Under format, you want to select ext3, which it may have already done for you, but if not, select it now.
[/INDENT]
Next it is going to ask you to confirm that you want to rewrite your partition map. You should have 3 partitions 1) Linux / ext3 ~28gb 2) swap ~2gb and 3) ntfs 70gb  and no additional free space. Click confirm and you are all set.

Sorry, I do not know which version of the installer you are using, but any difference from my directions and your installer will be purely cosmetic.

I'll be watching this thread carefully for awhile in case yuou have any questions along the way. Good luck.

---

### Post by js@lloyd on 2009-03-02
Thanks for the help. I have to run, so I'll devote some more time to this when I get back.  Really quick though, I highlighted the smaller partition to delete it, but the delete button isn't available..not highlighted.  Also, I tried to just boot up the machine into windows, but it's giving me an error about the cd not being in the machine.  typically, it tries to boot from the cd, and then goes to the hd when it's empty and boots up xp. i tried changing the boot sequence, and still no luck.  hope i didn't take out my xp.

---

### Post by handy on 2009-03-02
Something that is always worth keeping in mind when using tools like GParted, is to do one thing at a time. 

Don't have a number of processes waiting for you to give the go ahead, as there is a greater chance of finding trouble doing it that way.

---

### Post by js@lloyd on 2009-03-03
Thanks for all the help.  I gave it another go last night, and it looks to be a successful install.  However, there's a new problem.  As I mentioned yesterday, it wasn't booting up into XP after it reconized that there was no CD in the tray.  Now, it boots straight into Ubuntu without giving me an option. I was under the impression that i'd get to choose which OS I want to use.  I still will need to use XP until I can dial this one in.

---

### Post by literain2009 on 2009-03-03
hi,

regarding your first question during the installation
/dev/sda
/dev/sda1 ntfs 35799mb 3221 mb
/dev/sda5 ntfs 84243mb 10606 mb

you should have chosen /dev/sda1 ntfs 35799mb 3221 mb since this is your 30G partition reserved for ubuntu
-after that you can create other partitions such as /,/home etc.

the reason your not booting to ubuntu is that you have not installed the boot loader which will give you options on which OS to booth. Kindly look for topics on how to install the booth loader after installation. I hope that helps.

Lite

---

