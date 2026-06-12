---
title: "How do I uninstall Ubuntu 10.04 and not kill 9.10?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by aceracer24 on 2010-03-09
As the title suggests, I have installed Ubuntu 10.04 along side of 9.10. I would now like to uninstall 10.04 without destroying 9.10. What is the best way to do this?

---

### Post by Bölvaður on 2010-03-09
Depends on how you control the boot up.
Where is your active /boot at? is it at 10.04 or 9.10?

to find out which one it is you can press alt+f2 ant type```
gksu nautilus /boot
```
in either one of them and look for a file called **/boot/grub/grub.cfg** (in case of grub2 being installed) or **/boot/grub/menu.lst** (in case of the old grub)

if you have grub2 then edit the title of one of these
```
menuentry "Debian GNU/Linux (5.0.3) (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set c3fcfb48-b67c-406a-8e23-f0f277e814c6
	linux /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sdb7
	initrd /boot/initrd.img-2.6.26-2-amd64
}
```

and just change the title into something fun like *Debian GNU/Linux THIS IS THE CORRECT ONE*

in the good old grub you just add this to the bottom of this document
```
title		THIS IS THE CORRECT ONE
root
```


Now restart and see if this partition is the correct one.
If "THIS IS THE CORRECT ONE" does not show up then the other partition is housing the active /boot


It is ok to just remove the partition of 10.04 and extend the other one over that one without seeing any difference if the 9.10 has the active /boot
If it does not you can look around on this forum for "restore grub live cd". With that method you can restore grub in the unactive /boot.

---

### Post by aceracer24 on 2010-03-09
Wow....I wasn't expecting the answer to be so complicated sounding lol!

Ok just to add some additional info:

Ubuntu 9.10 was installed to the entire drive of my computer using the default instalation and partition. I just installed 10.04 last night as a "side by side" install using the default install and partition method. It resized the 9.10 partition to make room for the 10.04 install. I didn't do any manual partitioning or resizing. 

So again, 9.10 was installed first and then 10.04 installed along side of it. Also in case it matter, I was given the option to import the user information from 9.10 and I selected not to import anything. 

Hope this helps in descovering a simple easy to understand method for uninstalling 10.04. Thank you.

---

### Post by Bölvaður on 2010-03-09
> **aceracer24 said:**
> Wow....I wasn't expecting the answer to be so complicated sounding lol!

well it's just finding out which one it is booting from. But by what you said it is probably 10.04 as it came later.

there are only 2 things you will have to do:

0. (prepare)
get a live cd and boot it up.


1.
**Now go to System &#8594; Administration &#8594; Gparted** (or partition editor...) (you can also alt+f2 and type *gksu gparted*)

Delete the partition of 10.04. You can identify it in many ways if you dont know it's name. First of all... size, check properties in the top directory (named "/")

Now extend the old partition over the empty space and apply changes.



2.
Listen to Nixi, but DO NOT FOLLOW THIS MINDLESSLY, she is using grub but not grub2, so it will not work unless if you install grub  while you are on the live cd. check out the proper links below on how it is really done, but you will get the impression of how easy it is in Nixi's video.
[http://www.youtube.com/watch?v=WtBBl6HvdpM]("http://www.youtube.com/watch?v=WtBBl6HvdpM")


useful links:

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

[http://ubuntuforums.org/showthread.php?t=1419274&highlight=grub+recover+live+cd]("http://ubuntuforums.org/showthread.php?t=1419274&highlight=grub+recover+live+cd")


oh btw if everything fails you can always google "super grub disk" and burn it. it is a live cd that lets you boot into the grub that might be "inactive"

---

### Post by aceracer24 on 2010-03-09
> **Bölvaður said:**
> 
oh btw if everything fails you can always google "super grub disk" and burn it. it is a live cd that lets you boot into the grub that might be "inactive"

If everything fails, I will be forced to reinstall 9.10 as I won't have another computer to use. 

So if I am to understand:

1. boot a liveCD and delete the 10.04 partion and resize 9.10 partition. 

I get part 1. I am confused on what it is I need to do for part 2 though. Obviously I need to do something with Grub but since I have Grub2, it will be different then Grub.... I just don't get what it is I need to do.

---

### Post by Bölvaður on 2010-03-10
> **aceracer24 said:**
> 
I get part 1. I am confused on what it is I need to do for part 2 though. Obviously I need to do something with Grub but since I have Grub2, it will be different then Grub.... I just don't get what it is I need to do.

That is why I included links for you to read.





[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")
> 
1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
2. Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
3. Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".

[I]sudo fdisk -l
[/I]
4. Mount the partition containing the Ubuntu installation. (you can find all the hard disks under Places on the panel, just click the correct one and it will be mounted)

5. Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

*sudo grub-install --root-directory=/mnt/ /dev/***sdX** (find out the name of the partition, possibly by System &#8594; Administration &#8594; Gparted)

6. Reboot
7. Refresh the GRUB 2 menu with *sudo update-grub*
8. If the user wishes to explore why the system failed, refer to Post-Restoration Commands section below.



---

### Post by Mudge1946 on 2010-05-17
I think I have basically the same question, but I'm not even sure of that. Over the weekend I got a message saying there was a new upgrade to 10.04 LTS, and didn't see the fine print (if there was any) that this was intended for servers. Be that as it may, I clicked "Install," which I ran overnight. When I rebooted in the morning, the new version came up-- but my desktop doesn't work (it just shows my wallpaper and nothing else), my desktop isn't clickable to anything, the bottom bar is missing, the icons in the upper left that let me do things is gone, and my desktop folders are gone. Also, there was a message that something called OAFIID_GoHome (or something close to that) failed to load. So I've got a bunch of questions:
 
1) How do I get the desktop active, when there are no buttons/icons/commands, etc?
2) Do I need to uninstall this "Server" version? (I'm not running a server, just my ordinary home computer.) Or can it be made workable? 
3) When I boot up, the boot screen shows about six versions, some of which are recovery versions, but the up-and-down arrows don't work, and I can't scroll on this screen. And the F2 and F12 keys don't work (Never have, unless there's a trick I don't know.)
4) I don't have any kind of boot disk or recovery disk. Can I make one here at work and take it home to fix whatever I need to fix?
 
I should say that every time I've upgraded an Ubuntu version, starting with the 7-whatever, I've had a ton of problems, and things that ought to default (such as the desktop folders showing up and being active, etc.) don't. This is the third time I've upgraded, and none have gone smoothly. I never thought in a million years I'd say this, but I'm almost ready to go back to Windows -- and I loathe and despise Microsoft and all its evil works and minions. But I am so tired of tinkering with all the hundreds of Ubuntu tweaks I can't see straight. 
 
Help!! (And thanks in advance for same.)

---

