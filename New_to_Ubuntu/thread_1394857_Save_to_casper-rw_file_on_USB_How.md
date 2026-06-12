---
title: "Save to casper-rw file on USB? How?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by nooby on 2010-01-31
I ahve ubuntu 9.10 on a usb mem stick prepared with or by UNetbootin. 

I added a casper-rw file there and changed syslinux.cfg so it has the word persistent at the end. 

But where on the usb is it suppose to be? D:/ or inside the Casper folder? 

Must I change something in preferences so it knows it should save changes? 
Must I be a root user with priv to do saving on casper-rw? 

How does one set up such?

---

### Post by nooby on 2010-01-31
Here is another suggestion on how to make persistent. 

[http://www.pendrivelinux.com/how-to-make-ubuntu-704-casper-persistent/]("http://www.pendrivelinux.com/how-to-make-ubuntu-704-casper-persistent/")

CLI work

> # Open a terminal and type sudo su (to become root)
# Type mkdir /projectinit (to make our project directory)
# Type cd /projectinit (to change to the project directory)
# Type gzip -dc /cdrom/casper/initrd.gz | cpio -i (to extract the initrd.gz)
# Type gedit init (to edit the init file)
and so on. 

Too advanced for a newbie like me but it shows that it should be possible to save despite being in frugal install. 

I have managed to do frugal install of both Linux Mint and Super OS which is a regular Ubuntu with bling bling, codex and three browsers instead of 1 and so on. I like SuperOS very much due to me as newbie usually fail to install things because I either make use of USB or frugal install to not wreck the windoe$. 

so I dearly hope somebody that can linux can help me going. 

Here is my current neogrub menu.lst 

> title superos 
find --set-root /casper/vmlinuz
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper splash --
initrd /casper/initrd.gz 
boot



title Linux Mint 
find --set-root /casper/vmlinuz
kernel /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper splash --
initrd /casper/initrd.gz 
boot



I only need to learn how to save changes. 

DrG suggested that frugal install should be one of two options wubi and frugal install when people are asked how they want to install Ubuntu without doing partitioning and dual boot on Vista and Win7 machines.

---

### Post by C.S.Cameron on 2010-01-31
Usb-creator puts the casper-rw in filesystem, or the root folder or if you are booting from the thumbdrive, filesystem/cdrom.
You can also make an ext2, 3 or 4 partition and name it casper-rw if you want more than 4GB of persistence.
A partition named home-rw will make itself available for persistent home folders.

Once you add persistent thus:
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper splash -- persistent
it looks for casper-rw and home-rw files or folders at boot.
If instead you hit F6 for options at the first boot screen and type <space>persistent you will get persistence for that session only.

---

### Post by nooby on 2010-02-01
Thanks, I will experiment with this to see if it works in frugal mode too. 

[B]kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper splash -- persistent
it looks for casper-rw and home-rw files or folders at boot.[/B]
where should I place the casper-rw then? in C:/ or inside casper folder/subdir? 

To format in something other than NTFS on a HDD then I need an external one or do a partition or to do a loopmounted one ? 
Like Wubi does but that is something TuxCantFly voted against. 

I found a text saying one could go into syslinux and add persistent in the right place and that would make a "live CD" able to save things in frugal install. 

It is too new to me now but maybe I learn how to use it within some months or so. 
I have an old computer that I could experiment on but it is so slow. and it has xp and they do grub in another way than Vista and Win7. 

And Ubuntu is going for grup 2 now which is more difficult to change using a simple plain text editor. 
I already have linux on XP and need to learn to have it on Vista/Win7 machines because that is what I can buy cheaply now.

Edit using SuperOS in frugal install, have added -- persistent to menu.lst and put a decent casper-rw in the root of C:/ 

But how do I tell Ubuntu "Save now". 

Or does it save once a minute not telling me or does it always save at shut down? 
should I go into pref and set it up to save? 

don't I have to create a new user instead of "automatically logged in as "live user" which most likely forbid any saving even if persistent is given. Over riding that command? 

okay the only way to find out is to reboot and see if it worked.

[B]Nope, sorry! 

It failed to save anything. Neither bookmarks no which keyboard layout. 

I guess one have to create a user that have priveledge to save things. 

How does one do that when I dont know the username and password for the automatic log in of 

live session user

last time I tried to add a user it seems me had to know such[/B]

---

### Post by C.S.Cameron on 2010-02-01
Casper-rw goes on the root directory of your memory stick.
I haven't tried to stick it on the internal HDD, I don't think that works.
The casper-rw and home-rw partitions are for the memory stick also.
You can partition your memory stick using gparted booting from the Live CD.
Your could make them ext2 to begin with.
That and adding "persistent" as mentioned is all that you need to do.
If you make your bootable flash drive with usb-creator, (from the Live CD), it will add the Casper-rw file by default.
Cork

---

### Post by nooby on 2010-02-02
thanks

I used this program to put Ubuntu910 on a 2GB memstick and that one does say it made it persistent but it doesnot save anything so my wild guess is that I use the worng iso? 

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

think like this. 

The "live session user" have not "rights" to save anything because a pre made CD can not save things. Writeable DVD could but only Puppy is set up by default to save on the DVD. 

So maybe this iso can only save when one have "installed" it from itself? So I have to install it on a virtual hdd or a DVD and then from that do the install to the USB? 

Why else would not the LILI program work as they say? 

Wild guess two.

Maybe one need to go into groups and set it up so I have the right to save? 

But I cant because I don't have password to "live session user" named Ubuntu and psw unknown to me

a year back or 6 month back it was ubuntu ubuntu but that did not work for me. So something has changed with 910

---

### Post by C.S.Cameron on 2010-02-02
I haven't tried LiLi yet but this is how I made a Unetbootin install to 4GB flash drive persistent, (for 2GB flashdrive use smaller partitions, Home-rw may be ommited.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and removed flash drive.
Shut down Live CD.
Started Windows.
Plugged in flashdrive.
Started Unetbootin, selected Diskimage, located the iso, Selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown Windows.
Booted flashdrive.
At boot menu hit Tab, then typed "<space>persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

---

### Post by nooby on 2010-02-03
Very good description. 

One year ago I had not understood what you wrote but now I almost do get it enough to maybe be able to replicate the moves and hopefully get the same result. 

I do have a 4GB mem stick that I could dedicate to SuperOS which is an Ubuntu that have most of the programs that I like, and to have persistence is what I need too. Swedish keyboard is a must and to be able to keep addons to firefox is a must so 


I most likely will do as you describe here and I do recognize that you or somebody else in other forum has also described this or a wiki did it maybe. 

I have to learn more first about my needs to decided on sizes of the different partitioning. 

And remember one thing. The standard Ubuntu expects a HDD and not a flash memory so it writes fairly often to the flash if one have it on a flash so one need to change that behavior. 

that was why they did a remix to use on netbooks and eeepc and such that makes use of SSD flash HDD. 

So I am in no hurry. 

I tested my frugal install today and this is third day it boots fine with no hickups despite me changed firefox a lot adding addons and so on. 

So the ideal would be to have both. frugal install with persistence and usb mem stick with persistence for portable purposes or as a back up of preferred install to do rescue things. 

Thanks indeed for describing what works for you. Looks very interesting to try out in due time. within a month most likely. 

I need to learn more about grub2 just now. grub legacy I almost get what that one do but grub2 has C like codes with curly { things. and EOF and new things to remember to include. common_40 or whatever. so much new to learn.

I set it as solved because on one install it did work for me.

---

### Post by Mickeyj4j on 2010-03-12
teh origional post was about unetbootin. not usb-creator. how can if you create a caster-rw file on teh hd you should be able to edit what it on teh usb to edit this. 

puppy linux has this feature built into the os so when you shutdown it asks if you would like to save the current session and where you would like to save it. 

so it should be possible to somehow work this out for ubuntu 9.10, mint 8 etc 

if anyone nows how we would all love to know how you did it

---

### Post by nooby on 2010-03-12
> so it should be possible to somehow work this out for ubuntu 9.10, mint 8 etc

if anyone nows how we would all love to know how you did it

The original post was about UNetbootin and since then I tested two or three more such programs and have achieved save of changes on USB sticks. 

But it fail to work on NTFS in frugal install unless one do it with wubi or something similar. 

Ago who is in charge of wubi answered me back in 2008? that wubi is a kind of frugal install and that it should be possible and he made a description of it too but it was too abstract to me to grasp what he wrote. 

I ahve not dared to ask him to give a step for step description of it. 

I don't share your optimism that others than you and me would love to have such. 99% of all linux users only accept to do full install and they see frugal install as something alien to them. 

Do it the right way they would tell you and me. 

If I remember I will try to find the post by Ago and link to it from here.

Ah here it is

[http://ubuntuforums.org/showpost.php?p=5635552&postcount=4]("http://ubuntuforums.org/showpost.php?p=5635552&postcount=4")

Ago says:

>  Re: WUBI vs Frugal install? Differences etc?
A loopinstallation is like a frugal installation but customized for your hardware as opposed to be a "generic" install (which is optimized for "portability"). In fact a loopinstallation is exactly like a real installation. That of course also means that a loop installation is far faster than a frugal installation.

So the frugal installation has little advantages over a loop installation other than the fact that the installation itself is quicker
(since there is no linux side installation) and it takes less space (the squashfs is compressed).

By the way, wubi already supports frugal installation (not r/w although it can be changed by adding a persistent file)... Run wubi.exe from windows, then when you reboot press ESC and choose the last option... That is a frugal installation... 


[B]
If you want it permanent simply make it the default boot option in ubuntu\install\boot\grub\menu.lst.[/B] 


Note the demo mode option is deleted after a linux side loop installation.
Last edited by ago; August 21st, 2008 at 03:08 PM.. 

I guess that was on the old 9.04 or something. So not sure who easy it is to do on grub2 on the 9.10 and 10.04 and so on. 

Grub2 is much more difficult. I spend a whole day trying to do a dual boot on grub2 and failed to make the 40_custom file active for the update_grub command. I have given up on it. I know too little to make it work. While it was rather easy to do in old grub4DOS

---

