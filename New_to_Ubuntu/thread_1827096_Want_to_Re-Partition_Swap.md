---
title: "Want to Re-Partition Swap"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by @zur3 on 2011-08-17
[FONT=Times New Roman]Hello everyone! :)
                     [/FONT]            [FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]After using Ubuntu for 10 months, I realized that there were a few things that I just could not do. Namely backing up my Black Berry, and configuring my iPad (through iTunes). The real problem that came up was when I needed to submit my dissertation, because I did not want any formating issues to come up with my supervisor (she already hates me [/FONT][FONT=Times New Roman]](*,)[/FONT][FONT=Times New Roman]). A small difference between LibreOffice and Word and it would have been my neck on the line![/FONT]
[FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]So! I went out and got an HP Mini 210-3000 , and went straight home to work on my paper. After a few days of working on windows I got sick and NEEDED my Ubuntu back, but I realized that I didn't have a spare USB around to work with, plus I used my money to get the new laptop...:([/FONT]
[FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]So I tried the Wubi installation method to install 11.04, and I must say, it did what it was supposed to! Until I tried to go into hibernate that is![/FONT]
[FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]Not enough swap space...:confused:[/FONT]
[FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]I've typed  in the 'free' command in terminal, and * GASP! * what is this?[/FONT]
[FONT=Times New Roman]
[/FONT] 
```
[FONT=Times New Roman]total       used       free     shared    buffers     cached [/FONT]
[FONT=Times New Roman]Mem:       2044660    2022980      21680          0     540552     879100 [/FONT]
[FONT=Times New Roman]-/+ buffers/cache:     603328    1441332 [/FONT]
[FONT=Times New Roman]Swap:       262136          8     262128 [/FONT]

```[FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]Didn't make sense to me why the swap space was 255 KB. It must be a Wubi installation mistake.[/FONT]
[FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]I've read some documentation about resizing swap partitions, but they all advise to use a LiveCD environment. There is one problem with that... my little buddy has no CD drive!  It's a Netbook with only 3 USB slots! So here comes the main question:[/FONT]
[FONT=Times New Roman]
[/FONT] 
[CENTER][FONT=Times New Roman]*    “Can a  swap partition resize only be achieved with a LiveCD? Or is it also possible with a         USB drive?”*[/FONT][/CENTER]
[FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman]If it _is_ possible with a USB drive, then can someone please run me through the steps needed to achieve my goal? I would be content with just the steps, if writing the code would be too much of a hassle or time consuming. Its just the fact that I found an entry in this forums that suggested that after running LiveCD, to turn off the swap space, or something like that. I'm afraid that I am just not familiar with this process,  so any help would be much appreciated.[/FONT]
[FONT=Times New Roman] 
Thank you in advance!:P
[/FONT]

---

### Post by CatKiller on 2011-08-17
You don't necessarily need to use a live anything, you just need the partition to not be mounted. Depending on what exactly you're trying to achieve (resizing the partition that you're running GParted from, for example), that might mean that you need a live environment.

I haven't used Wubi, but [this]("https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F") might help.

---

### Post by eriktheblu on 2011-08-17
Wubi seems to have several problems with hibernation. Doesn't seem to matter how much swap you allocated.

This may help: [http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html]("http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html"), but better if someone more versed in Wubi chimes in.

Myself, I use neither Wubi, nor hibernation.

---

### Post by Paqman on 2011-08-17
> **eriktheblu said:**
> Wubi seems to have several problems with hibernation.

Well sure, if by "problems" you mean it's completely unsupported. Lack of the ability to hibernate is one of the drawbacks of using Wubi.

If you want a system that hibernates, install it to it's own partition. trying to hack Wubi to do something it's not supposed to is asking for trouble IMO.

---

### Post by pi.boy.travis on 2011-08-17
A Wubi installation is not capable of hibernation by design. Messing around with the loopback drive Wubi creates will do more hard than good. Just give your Ubuntu install it's own partition.

---

### Post by @zur3 on 2011-08-17
[FONT=Times New Roman]Thank you for the replies everyone, I  really do appreciate it![/FONT]
 [FONT=Times New Roman]So it seems that the general consensus is that I need to ditch the Wubi installation all together?[/FONT]
 

 [FONT=Times New Roman]Hmmmm...[/FONT]
 

 [FONT=Times New Roman]I figured that ***would*** be plan B, didn't expect it to be in the first couple of replies though! lol:razz:[/FONT]
 

 [pi.boy.travis]("http://ubuntuforums.org/member.php?u=620077") and [FONT=Times New Roman][Paqman]("http://ubuntuforums.org/member.php?u=228590") pointed out that I need to install Ubuntu on a separate partition, that needs a bit of clearing up though. Am I to understand that Wubi installs Ubuntu in that same partition that Windows uses? If that is that case, then I am dreading the installation even more... :/[/FONT]
 

 [FONT=Times New Roman]Sigh...So first thing I need to do is go out and get me a USB drive, so I can conduct a 'proper' installation. Step 2 should be backing up data.[/FONT]
 

 [FONT=Times New Roman]Any ideas about step 3? How can I remove the Wubi installation?[/FONT]
 

 [FONT=Times New Roman]I'm guessing that I'm going to have to remove it before proceeding, or am I wrong in my assumption?[/FONT]
 

 [FONT=Times New Roman]On a side note: I submitted my dissertation! Yay for me!!!:lolflag:[/FONT]

---

### Post by @zur3 on 2011-08-18
Bumpity Bumps!

---

### Post by @zur3 on 2011-08-18
[FONT=Times New Roman]Ok to uninstall the Ubunti/Wubi installation, one needs to boot back into windows and:
Control Panel>Add remove programs> Uninstall Ubuntu

To answer my own question, Wubi installs Ubuntu into a virtual drive. So it's no wonder that there are swap issues...

Thank you for everyone that has contributed! 

Officially Solved!:popcorn:
[/FONT]

---

### Post by eriktheblu on 2011-08-18
> **@zur3 said:**
> So it seems that the general consensus is that I need to ditch the Wubi installation all together?
Ubuntu works best with the traditional installation, but you don't "need" to do it that way. You can use it without hibernation as people have been doing for many years. 

> Am I to understand that Wubi installs Ubuntu in that same partition that Windows uses?It is installed as a file(s) on your Windows partition.

> Sigh...So first thing I need to do is go out and get me a USB drive, so I can conduct a 'proper' installation. Step 2 should be backing up data.

Any ideas about step 3? How can I remove the Wubi installation?
Step 2.1: Ensure you have the ability to recover Windows from external storage.

Step 3:Remove Wubi with the uninstall utility in Windows.

Step 4: Defrag

Step 5: Resize your partitions in Windows to accommodate Ubuntu

Step 6: Turn your newly acquired USB disk into a bootable Ubuntu install disk

Step 7: Reboot, and employ your boot options or reconfigure BIOS to allow booting from USB

Step 8: Install Ubuntu in the free space you created
 
> I'm guessing that I'm going to have to remove it before proceeding, or am I wrong in my assumption? You don't have to, but it would be a waste of HDD space to have an unused OS.
 
> On a side note: I submitted my dissertation! Yay for me!!!:lolflag:I take it that's a good thing. Congrats.

---

