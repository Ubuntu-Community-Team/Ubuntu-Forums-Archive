---
title: "i need help to find ANOTHER way to format my hdd and reinstall Ubuntu"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by myrnamynkoff on 2011-02-07
Hi everyone!

I have an Acer netbook computer, and about a year ago a friend installed Ubuntu on it, I loved it ever since.. but something happened last week and right now I can´t boot to the hdd.

So i created a USB live image, managed to back up all my data, and now i would like to format everything and reinstall Ubuntu from scratch. I only have one hard disk, and for some reason my computer is having a lot of trouble recognizing it. I tried reinstalling Ubuntu from the USB disk, but it will just froze right after the first options screen and nothing else happens after that.

I believe that evil Windows might be somewhere on that disk still and preventing me from accessing it. or maybe it's a physical problem? the original problem last week seemed to be right after i installed some updates. 
 
can anyone help me? I miss my computer very very much :(

thank you my friends :)

---

### Post by philinux on 2011-02-07
use the live usb and look in system admin disc utility. Check the HD is ok.

---

### Post by pqwoerituytrueiwoq on 2011-02-07
Use the disk utility and check it for errors
it is under system->Administration (may be preferences)
edit was beaten to the punch by [[COLOR=#d40000]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083")

---

### Post by myrnamynkoff on 2011-02-07
ok! i don't know if this helps or not but  i forgot to say that I used to have Ubuntu 10.04 and now I'm loading Ubuntu 10.10 on the usb live image.......



soooo....  when I try to find the disk it's not there, BUT if i plug my external  hdd it's like in order to load it, it opens an option that i can't see before that is 'File  Manager', and that's how i got to my hdd the first time in order to  remove my data from it. So now that you know that, yes, I went to Disk  Utility, and when I click on Check Filesystem i get the message that you can read on the screenshot...

maybe i can try formatting the disk from disk utility? i haven/t tried that yet...

---

### Post by hansolo4949 on 2011-02-07
Okay, first things first, do you care about wiping everything out in the drive? If so, just run an error check then format it. That will give you a nice clean slate to put your stuff on. If you still have stuff on there, run the error check. Can you access the drive? What happens when you try to boot?

---

### Post by myrnamynkoff on 2011-02-07
if i try to simply boot from the hdd it won´t boot at all. 

i did the Check Filesystem option on the 288GB and it says it's clean. I already did my backup so I'll format it right away... let's see....

---

### Post by myrnamynkoff on 2011-02-07
ok... wait..... i've never formatted a disk from ubuntu before.... which format should i give to it? Ext4? and if I want it to clean everything I should un-click the option that says 'encrypt underlying device' and leave the option that says 'take ownership of filesystem' clicked right?

also, i just found a green dot under Drive- ATA- that says 'Disk has a few bad sectors' :(

---

### Post by searchfgold6789 on 2011-02-07
Why not just start the Ubuntu installer, and select the option that lets you erase the disk automatically and use the entire thing for the installation?
Otherwise, yes, try using the disk utility - make sure that the disk is "Unmounted" first otherwise the option won't appear to erase it. Make sure you have a Swap partition (about 1GB is fine) as well as an ext4 partition.

---

### Post by myrnamynkoff on 2011-02-07
because when i tried to simply install ubuntu, it will froze right after the first options screen. it wouldn't even let me see the options to erase the disk. OK i will try to format it under Ext4 format then....ok?

i'm scared! :S

---

### Post by searchfgold6789 on 2011-02-07
It'll be fine. Just don't forget the Swap partition I told you about :)

---

### Post by myrnamynkoff on 2011-02-07
oK searchfgold6789!, so i formatted the 288GB disk and that was alright. it's now a 288GB Ext4 partition.

also I have one partition that says 'SWAP space' (2GB) and another one that says 'Extended 2GB'. 


now, i tried to do the same with the last partition that I see, that said 30GB Ext4', but when i tried to format it, i got the following error: 

[Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.12 (17-May-2010)
/dev/sda1 is apparently in use by the system; mke2fs forced anyway.
/dev/sda1: Device or resource busy while setting up superblock]

and now it doesn-t say '30GB Ext4' it says 'Unknown 30GB'


........ :confused:

---

### Post by myrnamynkoff on 2011-02-07
also, look at this new screeshot i uploaded.. so what now? :(

---

### Post by searchfgold6789 on 2011-02-07
Well, from your screenshot it becomes apparent that the hardware is encountering errors: it has relocated some data to another part of the hard disk to evade data integrity failure.
This will make partitioning a little tougher than usual, despite Ubuntu's apparent inoccent assesment.
Now what would help - Boot from your live USB and install GParted. Take a screenshot of your harddisk from that program and post it here.
One thing seems strange to me ... Despite the errors, it would seem to me that simply erasing all the partitions and starting anew would work. Is that what you did? Try just deleting the Unknown one, and post what happens... that should just *work*.
It must be frustrating, especially having to wait for all those big partitions to be made.
Also - Once you erase the partitions on the hard disk and replace them with the two required ones, ext4 and swap, remember to reboot. The Live CD will use the swap partition.
To unmount a swap partition, enter into a terminal and type ```
sudo swapoff
```

---

### Post by myrnamynkoff on 2011-02-08
thank you so much searchfgold6789!
here's a screenshot of Gparted.
So i tried to delete the partitions from the disk utility, no go at all.....
now i'm trying to do it from Gparted, so far I can't but i'm still trying.

i thought ubuntu and I were friends :(

---

### Post by myrnamynkoff on 2011-02-08
ok, so i didn´t do anything yet and the computer just turned off, and now it won't boot it just says:
error: no partition

:(

---

### Post by myrnamynkoff on 2011-02-08
SO....... i finally got to delete all the partitions, left except for 2: swap space, and another one ext4.

restarted it and never came back from there: it's just a black screen with a blinking cursor on it.

...is there anyone out there?

:(

---

### Post by searchfgold6789 on 2011-02-08
Before deleting the ext4 partition, right click and Unmount it. Before deleting the Swap partition, right click and click Swapoff. Then everything on the disk will be deletable.

---

### Post by myrnamynkoff on 2011-02-08
> **searchfgold6789 said:**
> Before deleting the ext4 partition, right click and Unmount it. Before deleting the Swap partition, right click and click Swapoff. Then everything on the disk will be deletable.

too late!!! now i can't exit that black screen with the blinking cursor :(

so.... how do i get out of that black screen?!

---

### Post by searchfgold6789 on 2011-02-08
So, new problem: now when you try to reboot your computer simply displays a black screen with a flashing white underscore symbol.


[LIST]
[*]Make sure it is set to boot from USB
[*]Try making another Live USB
[/LIST]
Those are the only two I can think of...

---

### Post by searchfgold6789 on 2011-02-08
Also, some systems do not shut the motherboard down all the way after there is an ACPI shutdown. Do a hard shutdown (hold down the power button) and wait 30 seconds. Then press the power button again and make sure it is set to boot from USB.
Unless the USB data is somehow flawed or deleted (in which case you will have to create another one) I see no reason why it should not work.

---

### Post by myrnamynkoff on 2011-02-08
> **searchfgold6789 said:**
> So, new problem: now when you try to reboot your computer simply displays a black screen with a flashing white underscore symbol.


[LIST]
[*]Make sure it is set to boot from USB
[*]Try making another Live USB
[/LIST]
Those are the only two I can think of...

ok! thank you so much for trying!!

i made the Live USB again and now it got to the main screen.

I'm trying once again to INSTALL ubuntu... i'm keeping my fingers crossed! :)

---

### Post by searchfgold6789 on 2011-02-08
I wish you luck! You are very welcome. If the installations proves to be successful, please use the Thread Tools menu to mark this as solved, otherwise please report back with any issues you may have.

---

### Post by myrnamynkoff on 2011-02-08
> **searchfgold6789 said:**
> I wish you luck! You are very welcome. If the installations proves to be successful, please use the Thread Tools menu to mark this as solved, otherwise please report back with any issues you may have.

i'm sorry.... i'm not there yet but i think i'm close! i got through some part of the installation, i'm at the screen where you get to write your name, your computer's name, password, etc.... i did all that, but the FORWARD option is disabled, and underneath it says 'ready when you are'.... it is expecting me to click FORWARD, but i can't! i'm sad :(

there's a command prompt underneath although it won't let me scroll down to read much about it, but maybe i can type the command for 'forward'? do you happen to know which command that is?
:confused:

---

### Post by searchfgold6789 on 2011-02-08
The command does not exist. Sorry! Most likely, one of the things you entered in is incorrect. Make sure everything matches the requirements. Password must be 8+ characters, etc.

---

### Post by searchfgold6789 on 2011-02-08
[HERE]("http://askubuntu.com/questions/14168/installer-gets-stuck-with-a-grayed-out-forward-button") is a good article that may solve your problem.

---

### Post by myrnamynkoff on 2011-02-09
> **searchfgold6789 said:**
> [HERE]("http://askubuntu.com/questions/14168/installer-gets-stuck-with-a-grayed-out-forward-button") is a good article that may solve your problem.

yes!!!!!!!!!!!! it's running!

i can't believe it, i'm happy!
thank you so much!!!! 


you :guitar: searchfgold6789


yey!

---

