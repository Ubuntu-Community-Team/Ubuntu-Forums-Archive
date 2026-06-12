---
title: "Extremely slow computer"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by userub on 2011-09-05
Hello,

I'm using Ubuntu 11.04 and Firefox 6. And the computer is incredibly slow. For instance, it will sometimes take ten minutes just to open Firefox, open a tab, go to Google, and enter something. The tab will take a long time to load, Google will load slowly and the computer will freeze while I'm entering text. Hitting enter and waiting for the page refresh also takes a long time.

If I minimize Firefox and try to maximize it again, it will show a white screen and take over five minutes to return to the page.

Chrome also has the same problems.

And when I move the mouse around, the computer will often freeze and leave the mouse trail jerky. Even the seconds on the system clock will freeze!

There's a loud grinding noise from the computer when it's slow. I don't know why it's doing any of this.

---

### Post by snip3r8 on 2011-09-05
Questions
1: What are your specs?
2: Did you remove the disc after installation

Possible solution:

Open up your system monitor and check your processes tab for any processes that may be taking up valuable CPU time.

---

### Post by oscarivera9 on 2011-09-05
I'd like to help you but in order for me to do that I first have to find out a few things. 
1. My first thought is this, do you have Ubuntu installed on your HDD or are you using a Live CD?
If you are using a Live CD that answers everything because the PC is running off an OS that hasn't been installed on a hard drive yet which is naturally much slower than if it were installed on a hard disk.  Still, it shouldn't be that slow anyway.  Let's continue.
2. What kind of setup are you using?  In other words, what kind of computer do you have?  
     What's your CPU?  
     How much RAM?  
     How much Swap?  
     How are you connecting to the internet?--Wireless, broadband, etc. 
     If by any chance you happen to know how much power your PSU puts out, that might help also.
3.  Do you have any other OS's installed on your PC?  (for example Windows XP, Windows 7, Linux Mint, etc.)
4.  Have you tried booting off an older kernel at boot time, when GRUB first appears?

:confused:

Try to post an answer to these questions and we will be better able to help you out.

---

### Post by westie457 on 2011-09-05
@ userub

> There's a loud grinding noise from the computer when it's slow. I don't know why it's doing any of this.

This is the worrying part of your problem. It is caused either by a failing hard drive or the cooling fan is seizing.

The first one is easy to check with Disc Utility and taking a look at SMART monitor. If you are using the Unity interface click on the big symbol at the top left corner and type in disk utility,
If using classic interface System > Administration > Disk Utility select your hard drive from the left pane.
Here there will be a line with SMART Status and an option to run self tests.

The second is harder to check however it will not hurt to clean the ventilation whole in the case.

---

### Post by userub on 2011-09-05
> **oscarivera9 said:**
> I'd like to help you but in order for me to do that I first have to find out a few things. 
1. My first thought is this, do you have Ubuntu installed on your HDD or are you using a Live CD?
If you are using a Live CD that answers everything because the PC is running off an OS that hasn't been installed on a hard drive yet which is naturally much slower than if it were installed on a hard disk.  Still, it shouldn't be that slow anyway.  Let's continue.
2. What kind of setup are you using?  In other words, what kind of computer do you have?  
     What's your CPU?  
     How much RAM?  
     How much Swap?  
     How are you connecting to the internet?--Wireless, broadband, etc. 
     If by any chance you happen to know how much power your PSU puts out, that might help also.
3.  Do you have any other OS's installed on your PC?  (for example Windows XP, Windows 7, Linux Mint, etc.)
4.  Have you tried booting off an older kernel at boot time, when GRUB first appears?

:confused:

Try to post an answer to these questions and we will be better able to help you out.

1. No, Ubuntu is running from the hard drive.
2. I ran 'lshw' in Terminal and I see that RAM is 486 MiB. I'm not sure about the other two specs.
3. Yes, I have a dual-boot set-up with Windows Vista.
4. I don't have any other kernels. I've uninstalled all of them.

---

### Post by mmsmc on 2011-09-05
> **userub said:**
> 1. No, Ubuntu is running from the hard drive.
2. I ran 'lshw' in Terminal and I see that RAM is 486 MiB. I'm not sure about the other two specs.
3. Yes, I have a dual-boot set-up with Windows Vista.
4. I don't have any other kernels. I've uninstalled all of them.
and im assuming this does not happen in vista?

---

### Post by userub on 2011-09-05
> **mmsmc said:**
> and im assuming this does not happen in vista?
Vista is also slow. It's the main reason I switched to Ubuntu, 8.04 at the time. At first Vista and Ubuntu were quick; they've gotten very slow over time.

---

### Post by mmsmc on 2011-09-05
> **userub said:**
> Vista is also slow. It's the main reason I switched to Ubuntu, 8.04 at the time. At first Vista and Ubuntu were quick; they've gotten very slow over time.
ok, tell me a few things
1. how old is your computer/ what are the specs
2. do you here the grinding noise in vista?
3. aside from ram, how much hd space do you have?

---

### Post by userub on 2011-09-05
> **westie457 said:**
> @ userub



This is the worrying part of your problem. It is caused either by a failing hard drive or the cooling fan is seizing.

The first one is easy to check with Disc Utility and taking a look at  SMART monitor. If you are using the Unity interface click on the big  symbol at the top left corner and type in disk utility,
If using classic interface System > Administration > Disk Utility select your hard drive from the left pane.
Here there will be a line with SMART Status and an option to run self tests.

The second is harder to check however it will not hurt to clean the ventilation whole in the case.

I clicked on the self-test button. It says most of the list is Good or N/A. The only warning is for Reallocated Sector Count.

> **mmsmc said:**
> ok, tell me a few things
1. how old is your computer/ what are the specs
2. do you here the grinding noise in vista?
3. aside from ram, how much hd space do you have?

1. It's over three years old. And other than 486 MiB RAM, I don't know how to find the specs.
2. Yes. In both systems, when the computer is frozen.
3. I have 271 MB free. It's an 80 GB machine, with Ubuntu and Vista each taking around 40 GB.

---

### Post by mmsmc on 2011-09-05
well, i do suggest you wait for others opinions on this, but i think either your hdd or a fan is dying. for now back up all your data and wait. but it definitely is a hardware issue

---

### Post by nothingspecial on 2011-09-05
> **userub said:**
> 



1. It's over three years old. And other than 486 MiB RAM, I don't know how to find the specs.

3. I have 271 MB free. It's an 80 GB machine, with Ubuntu and Vista each taking around 40 GB.

You could do with adding more ram or running a lighter desktop environment.

You need to free up some space.

---

### Post by whatthefunk on 2011-09-05
I dont think you have enough RAM to run Ubuntu.  Maybe you should try a lightweight distro like Lubuntu.

---

### Post by axatrikx on 2011-09-05
its probably free space issues. for windows check the free space in C and in ubuntu do the same for the root partition. 
use 'df' command to see the used space for each partition. If the free space is low, thats the reason for the slow system.

---

### Post by oscarivera9 on 2011-09-05
> The first one is easy to check with Disc Utility and taking a look at  SMART monitor. If you are using the Unity interface click on the big  symbol at the top left corner and type in disk utility,
If using classic interface System > Administration > Disk Utility select your hard drive from the left pane.
Here there will be a line with SMART Status and an option to run self tests.

Definitely check your SMART status.  The instructions up above for how to do it are pretty accurate.  
However, from the info you've given me I can tell you right away that you definitely need to add more RAM to your computer.  Back in the days of Pentium computers, 512 MB of RAM might have been more than enough but nowadays it is next to nothing.  When I saw the number you posted right away it didn't look good .  My current PC is using about 16 times the amount of RAM that you are using.  I have 8 GB in my setup.  If you have Windows Vista installed and that is also malfunctioning, I can assume two more things.  First, you have at least a duo core processor, which means that you definitely need more RAM.  Second, the fact that Vista is also suffering means that you definitely need more RAM.  You may also want to run the Windows Experience Index through Windows Vista (found in the Control Panel) to see what it tells you about your Memory.  If the score it gives you is less than 2, then it is basically telling you the same thing that I am saying, which is: get more RAM.  You also, want to find out how much Swap Space you are using (In Ubuntu you can find that by going to the Disk Utility as well when you are checking your SMART score, it is quite simply a partition on your hard drive labeled as Swap which preferably should be the same amount as your RAM).  
Prescription:
I recommend 2 GB of RAM and 2 GB of Swap, take them with a full glass of water on an empty stomach and call me in the morning it the symptoms continue.#-o
If your problem is what I think it is, then the fix is simple and nothing to worry about.  To find out what kind of RAM you need, I like going to this website that runs a scan of your computer and tells you exactly what you have and then it recommends what you need, just write everything down and then take that paper with you  to your local store that sells computer parts (or do it online if you so prefer).  
Go here: [http://www.crucial.com/](http://www.crucial.com/)
Just follow the instructions they tell you to run the Memory Diagnostics, and if you want you can even order from them, unless you are more inclined to go to a different place like newegg.com or even Amazon.com
If your problem is not your RAM, don't worry, we'll help you get it fixed.

---

### Post by NightwishFan on 2011-09-05
In my opinion 400-500mb of ram is pushing it even to run 32-bit Ubuntu. I second you try a lighter environment such as Xubuntu/Lubuntu/Zenix. The grinding noise is probably just page faults because the system is swapping out to page/swap file.

I agree you should check the hard disk though.

Also, do you have a swap file/partition on Ubuntu? You will need on if you have such low ram. We can see the ram situation, boot into Ubuntu and type this in a terminal:
```
free -m
```

---

### Post by userub on 2011-09-05
Wow, I like the detail in these replies.

I'll check out my options for getting more RAM, though I'm hesitant about installing internal hardware. In the meantime, I'll look into the lighter distros.

I ran 'free -m' and this is what came up:

             total       used       free     shared    buffers     cached
Mem:           486        430         55          0          4        171
-/+ buffers/cache:        254        232
Swap:         1427         38       1388

How bad is it?

---

### Post by NightwishFan on 2011-09-05
To be honest, it isnt so terrible, but I doubt you will get far with big apps like Firefox. Generally you should not swap at all, but you have less swap used than I thought. Then again I bet the moment you open Firefox it begins to lag? That is why, simply not enough ram.

---

### Post by cheapodonuts on 2011-12-21
This is an interesting thread, as I have several old PCs hanging around and will try fresh installs in each one over Xmas. But how was the problem 'solved'? Could you please tell us how you fixed it? Thanks. :)

My advice would have been to wipe Windows completely, and that 500mb RAM isn't really enough for Ubuntu efficiently.. ;)

Try [COLOR=Blue]**_[Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")_**[/COLOR]. It's cool and uses almost zero resources.

---

### Post by oscarivera9 on 2011-12-21
> **cheapodonuts said:**
> This is an interesting thread, as I have several old PCs hanging around and will try fresh installs in each one over Xmas. But how was the problem 'solved'? Could you please tell us how you fixed it? Thanks. :)

My advice would have been to wipe Windows completely, and that 500mb RAM isn't really enough for Ubuntu efficiently.. ;)

Try [COLOR=Blue]**_[Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")_**[/COLOR]. It's cool and uses almost zero resources.

YES, Yes, yes!!!
I would _also_ like to know how it was that your problem was "Solved".  I like to give back to the community by helping if I can, and then there comes a time when I'm the one who needs the help; when that's the case I am ever so grateful to all of those who helped along the way.  I also think of people who may eventually have the same problems that I might have had and so I make it a point to post on the threads that I start how it was that I was finally able to solve the problem.

Always remember: when you have a problem and you post it on the forums, you are not only helping yourself, but you also help others along the way.
):P

---

