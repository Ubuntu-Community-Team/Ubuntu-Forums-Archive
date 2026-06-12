---
title: "Grub"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Raistlin82 on 2011-05-04
Hi all

Sorry if there is already a thread answering this, I've been searching since last night! I have finally managed to upgrade to 11.04 and was looking forward to checking it out after rebooting.

Upon the reboot I was greeted with the Grub rescue prompt and was stuck there until I found my live cd.  I have now managed to get online as a result of this and tried lots and lots of ways to restore and afterwards reinstall grub.

I was dual booting Vista and Ubuntu and hope to again shortly!! I have I think un-installed grub-pc completely and installed grub.  However Grub cannot detect anything to boot from.... (you may now have guessed I'm a noob and somewhat out of my depth at the mo!)  

I'm not sure what information is helpful to identify the problem here or I would have posted, but from a frustrated and desperate person... PLEASE HELP! :-)

---

### Post by garvinrick4 on 2011-05-04
go into your live cd and run 
sudo fdisk -l (lower case L)
get your sda# that is your linux install.
Or copy and paste and I will look at it and get it for you and give you code to purge and reinstall grub-pc to your drive or really to its (mbr) master boot record.

---

### Post by Raistlin82 on 2011-05-04
Hi there, please see output from sudo fdisk -l below, code would be greatly appreciated!

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x42210970

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         702         893     1536000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             893       13504   101297852    7  HPFS/NTFS
/dev/sda4           13505       19457    47817410+   5  Extended
/dev/sda5           19209       19457     2000061   82  Linux swap / Solaris
/dev/sda6           13505       19208    45817317   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by garvinrick4 on 2011-05-04
We are going to just purge everything grub and reinstall just in case. Going to do it in whats called chroot or the root of your install. Works better for me. So copy and paste these in
a terminal in the Live CD with internet connection. There are a few commands here that
are redundant but just to be safe doing an few extra. Copy and paste these one at a time.
                          ```
sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 

 
``````
apt-get purge grub grub-common grub-pc
``````
apt-get install grub-common grub-pc
``````
grub-install /dev/sda
``````
update-grub
``````
dpkg --configure -a
``````
exit
```                          ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 

```Now reboot and should be a working system:
Here is a good link for you explains most everything Keep in bookmarks:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Raistlin82 on 2011-05-05
garvinrick4 Just wanted to say a MAAASSIIIVVEEE Thank you!! Booting up fine now with a fully functional grub! ;-)

---

### Post by pac4639 on 2011-05-05
Hello, 
I'm pretty much in the same boat as this post implies but with the following issues: I upgraded without a cd, did it online.  When I then rebooted I lost the windows7/ubuntu options.  Now my computer only boot into Unbuntu.  I'd really like to keep the dual boot options.  Can you help me?  Also, I'm a newbie, so be kind, thanks to you...John

---

### Post by kdnoel on 2011-05-05
Don't feel lonely... I upgraded via Internet and have lost my option to boot to Ubuntu or Xp.

I get an out of range message and then finally boot to Ubuntu.

I just noticed in the above signature a link to directions... both via live cd and internet update.

I'll go try it and see if it works.

---

### Post by wilee-nilee on 2011-05-05
> **pac4639 said:**
> Hello, 
I'm pretty much in the same boat as this post implies but with the following issues: I upgraded without a cd, did it online.  When I then rebooted I lost the windows7/ubuntu options.  Now my computer only boot into Unbuntu.  I'd really like to keep the dual boot options.  Can you help me?  Also, I'm a newbie, so be kind, thanks to you...John

So start a thread all your own, post the output as asked by the helper in this thread, make sure the header is relevant to the problem, ie grub, problem, Natty..etc 
sudo fdsik -l

If you noticed it was the information from this command that was used  to fix the problem.

And welcome aboard the forums, the life jackets are in the community cafe.;)

---

### Post by garvinrick4 on 2011-05-05
> **Raistlin82 said:**
> garvinrick4 Just wanted to say a MAAASSIIIVVEEE Thank you!! Booting up fine now with a fully functional grub! ;-) 
You are welcome Raistlin82 enjoy your Ubuntu Linux. 
Mark as Solved please in Thread tools in upper right
of your Thread. Have a nice day.

---

