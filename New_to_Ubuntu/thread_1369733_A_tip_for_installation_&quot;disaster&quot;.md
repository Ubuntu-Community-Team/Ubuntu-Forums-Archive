---
title: "A tip for installation &quot;disaster&quot;"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Drjim on 2010-01-01
I recently installed Ubuntu 9.10 remix on my netbook. I had to get rid of a primary partition in order to get a guided Ubuntu partitioning and installation. I was installing as a dual boot along with the OS that came with the netbook, Windows 7. 

I wasn't sure how to handle the partition deletion, but there is a very nice freeware program for this available at cnet.com called Easeus Partition Manager. 

After deleting a partition (being careful *not* to delete the one that had my windows 7 in it) and installing Remix, I saw that a menu would come up on booting giving the choice between Ubuntu or windows. It gave me the choice of both windows 7 and windows vista "loader". Both the Ubuntu and windows 7 boot worked ok but I was curious about the vista loader (never used vista, just xp). I tried the vista boot and my computer went nuts. It wouldn't boot either Ubuntu or win 7. I tried turning my computer off completely and then restarting, same thing. 

I thought, "Well curiosity killed the computer!". I then remembered that I had the netbook set for booting from a usb drive and the F2 settings key at least did work during the boot process. 

I was able to use the Remix ISO file on the usb drive to reinstall remix and everything worked fine including getting the menu back which allowed a windows 7 boot. 

The downside was that, during the guided reinstall, I ended up with two sets of Ubuntu remix with 4 partitions in my now sliced up hard drive. I used the partition mgr in windows to get rid of one of these and then my computer wouldn't boot again! I re-reinstalled remix which worked but still left me with a sliced up hard drive filled with stuff I didn't need and space I couldn't use. 

The last step was to go back to the Easeus partition mgr and delete everything except the C drive and the partition with windows 7 loader and re-re-reinstall remix. Now I have only the partitions needed to run windows and Ubuntu and all my hard drive usable.

Hopefully others aren't going to screw up their boot system this way but I wanted to post this just in case. In the above situation all is *not* lost and you don't have to take your computer to a specialist to have someone fix the screw-up (expensive as well as embarrassing!)

Jim

---

### Post by Temposs on 2010-01-01
Congratulations on fixing your problem by yourself :-)

Hopefully you can enjoy Ubuntu now :-)

---

### Post by candtalan on 2010-01-01
What was the Vista Loader doing in a Windows 7 laptop I wonder? Is it likely to be a standard feature to beware of if people dual boot (grub) in a windows 7 PC?
tia

---

### Post by Drjim on 2010-01-01
> **candtalan said:**
> What was the Vista Loader doing in a Windows 7 laptop I wonder? Is it likely to be a standard feature to beware of if people dual boot (grub) in a windows 7 PC?
tia

I never did figure that out. Seems odd, doesn't it? That's what tempted me to try booting it to disastrous effect! it may have something to do with Samsung's recovery system. Anyway, if you buy a Samsung netbook (which I think is a very good machine) watch out for this and don't try booting the Vista loader. 

Jim

---

