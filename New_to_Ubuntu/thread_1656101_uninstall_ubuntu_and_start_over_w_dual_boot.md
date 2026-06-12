---
title: "uninstall ubuntu and start over w/ dual boot"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by woodeye3 on 2010-12-30
I recently installed 11.04 on a new TB HD. It seems to work OK,I'm still learning.
I've decided I'd like to dual boot from 1 HD (multiple partitions) or Ubuntu on 1 HD and Win7 on another. I've read that it is better to start fresh on a clean HD with win first and then put Ubuntu on a partition. I think it might be better to completely remove Ubuntu and start over. I don't know how to remove Ubuntu and If I try to load Win7 over Ubuntu I get an error that the HD format isn't recognized (needs to be NTSF?).
Help please 
Thanks Jeff

---

### Post by ElPuma27 on 2010-12-30
Here's a link to a video that shows how to remove any Linux system  from a dual boot.
[Delete Linux Partition]("http://www.youtube.com/watch?v=K95gKIX-BbI")
I found it useful, but after watching it, I suggest you first fix Windows Boot Loader to remove the Grub, and then lastly remove the partition, just in case you first encounter a problem with the boot loader. Also I found that only I needed to use the FixMbr, don't know if that's the case for you.
Hope this helps.

---

### Post by Zzl1xndd on 2010-12-30
I haven't really done much with Windows 7, However most older versions of Windows give you the option to format the drive during the Install, Windows 7 should also have this option.


Also was there some specific use you needed windows for? I know a lot of people do rather well with a VM. It would allow you to just fire up Windows when you need too without having to reboot.

I normally use [VirtualBox ]("http://www.virtualbox.org/")for my VMs.

---

### Post by woodeye3 on 2010-12-30
Hey thanks for the replies
First ELPUMA27
I'm not dual booting at this point. 
Ubuntu is all that is on the HD
I haven't looked at the link you gave yet I'll do that after I respond to you.
I'm not sure what you mean by fix win boot mgr to remove grub?
also what is the fix MBR
Next
 
tweakedenigma
I never saw a option to format the drive. All I got during the install process
was that Win couldn't install on the drive because it didn't recognize the format the drive was in.
I've read on the forums that Win only recognizes NTSF where Ubuntu will work with numerous file formats. (Another reason to use linux) 
the reason to use windows is that I want to install a TV capture card an the instructions only refere to WIn operating sys.
I know that the card will work with Mythbuntu but I'm still too green to start using it on linux.
 I'd like to play with the card to figure it out  as I'm learning Ubuntu. 
It took me the longest time to find the HD in Ubuntu this am. I'm used to just going to MY Computer and there the C drive is.
Re VM 
I have it on my laptop with WIn7 and XP on the VM. 
When the VM is open the computer is extremely slow and locks up frequently.
I'm not opposed to getting another HD 1 for each OS. But if it's not necessary..........
Thanks you guys I'll look forward to hearing back from you
Jeff

---

### Post by ElPuma27 on 2010-12-30
Sorry, I misread your threat, since I saw dual-boot, I though you had dual. I should read twice, still the info might help later on when you do have dual-boot.

Now here's what I'm looking at, if you have another computer running, either Windows or Linux, you can connect your hard drive directly and delete the Ubuntu partition, or format your hard drive to NTFS, then connected back to the original computer and install windows.
That's my theory. Also from searching the web I came across the following info:
if you boot from a LiveCD, you can then use the gparted tool to delete the partitions, after that the space will either become unallocated space or free space instead of the ext4 or whatever format Ubuntu might use. After that you can end the session of the LiveCD and install Windows. If you want to you can google, uninstall ubuntu single boot for more info.

As you might know I've always used dual boot, so I don't have first hand experience with deleting Ubuntu from single boot machines.

I just found another video, same guy from the previous link I gave you, but this time he shows how to install Windows and remove Linux, with the windows disk.
[http://www.youtube.com/watch?v=EElI9uHscTE](http://www.youtube.com/watch?v=EElI9uHscTE)

---

