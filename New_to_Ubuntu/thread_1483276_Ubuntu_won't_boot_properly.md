---
title: "Ubuntu won't boot properly"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by BobbyDing on 2010-05-14
Hi folks.
Linux newbie here. Very green.

I have been having issues installing ubuntu. The machine has an Asus MB A7V8X-X with 1gb ram, Geforce 400 MMX video card, Standard EIDE and PCI busses, 20gb HD. The machine runs XP just fine. I actually have two of these machines that are identical with the exception of the drive brands. I have tried both drives.

After installing ubuntu (tried 9.04 thru 10.04 so far, all with the same issue) I can reboot (warm boot) and all is fine. However, cold boots yield the following errors:

[COLOR="Blue"]udevadm settle - timeout of 180 seconds reached, the event cue contains:
/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda (755)
/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda/sda1 (756)
/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda/sda2 (757)
/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda/sda5 (75

Gave up waiting for root device. Common problems:
- boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check rootdelay= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/96b486e8-1df5-4e2b-bb21-5968015f6ad8 does not exist.
Dropping to shell!

Busybox V1.13.3 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for list of built in commands.

(initramfs)
[/COLOR]

I can type 'exit' after a while (10 minutes) at the initramfs prompt and it will eventually boot. The screen does continue with other errors after the initramfs prompt, and I have to wait for those to complete (something about 'ata1: link is slow to respond, please be patiet'). All seem to be failures with drive access.

I've searched these forums and found similar issues and tried these fixes.....Adding 'rootdelay=90', as well as the one in this link which has me re-installing grub...

[http://ubuntuforums.org/showthread.php?t=981159&page=4]("http://ubuntuforums.org/showthread.php?t=981159&page=4")

Neither fix has worked. I started with 10.04 and dropped back to 9.10 and then to 9.04 just in case it was a grub issue. I tried the recovery selection under grub, and the last drivers to load before the error pops up are the USB drivers. There are no USB drives attached, and while there is a USB mouse, I've tried booting without any USB devices plugged in, just in case. Also, I have two identical machines, and both are having this issue.

Any suggestions?

Thanks!!

---

### Post by BobbyDing on 2010-05-15
Anybody?

---

### Post by Daniel Jorge on 2010-05-15
Hi!

My guess the last version of Grub is not supporting your hardware.
So install an earlier version of grub.;)

Try booting up with Ubuntu 8.10 live-cd and type on your shell:
```
sudo grub-install hda1
```
Probably is "hda1" but you can verify it on Gparted.

---

### Post by keroman on 2010-05-15
have you looked here you may want to read all of it , it sounds similar,I started looking by searching the last line of your text, I did this as you had no replies, unfortunately I am not clever enough to solve your problem
 >  [jadcox]("http://ubuntuforums.org/member.php?u=977916") 				 				 			
   			 First Cup of Ubuntu
  			 [IMG]http://ubuntuforums.org/images/rank_1.png[/IMG]
  			  			  			  				 
				Join Date: Dec 2009
 				 				 	  					Beans: 5 				
 			   				 				 				 				 				    
 			
   	 	 	 	 		 		 			 			  				 				**Re: boot issues after patch update** 			
  			  			 		   		 		 		 Solved!!  
 
Ok, so here's what I had to end up doing.
 
Boot system and press the "Esc" key when prompted to bring up the boot option menu
 
I chose one of the older recover options, and pressed "e" to edit it.
 
I changed the first line to "root=(hd0,0)
I changed the root=UUID=72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3 ro quiet  splash             to
                     root=/dev/sda1 ro quiet nosplash
 
It finally came up and performed a check disk on the sda1 disk
 
Next it came up with a menu that allowed me to  go through several options of running clean up commands.  After doing  this I rebooted the computer and everthing came up as normal!
 
Thank you all
 

---

### Post by BobbyDing on 2010-05-15
Thanks. I will try those this weekend and report back.
 
Any other suggestions welcome!!
 
Bob

---

### Post by drs305 on 2010-05-15
> ALERT! /dev/disk/by-uuid/96b486e8-1df5-4e2b-bb21-5968015f6ad8 does not exist.


Is this your Ubuntu root drive?

A bit more on what keroman wrote:

Do you get the Grub 2 menu? If not, and this is Grub 2, hold down the **SHIFT** key early in the boot process to get the menu. 

If you get the menu, press "e" with the Ubuntu selection highlighted. Use the arrow keys to move to the "search" line and hold down the DEL key to completely remove the line.

For any other lines with a UUID reference, replace it with the /dev/sdXY designation for your Ubuntu partition (example: root=UUID=<UUID>  to  root=/dev/sda1).

After making the changes, press CTRL-X and see if it boots that way.

---

### Post by BobbyDing on 2010-05-16
> **drs305 said:**
> Is this your Ubuntu root drive?
 
A bit more on what keroman wrote:
 
Do you get the Grub 2 menu? If not, and this is Grub 2, hold down the **SHIFT** key early in the boot process to get the menu. 
 
If you get the menu, press "e" with the Ubuntu selection highlighted. Use the arrow keys to move to the "search" line and hold down the DEL key to completely remove the line.
 
For any other lines with a UUID reference, replace it with the /dev/sdXY designation for your Ubuntu partition (example: root=UUID=<UUID> to root=/dev/sda1).
 
After making the changes, press CTRL-X and see if it boots that way.
 
 
OK, I removed the first reference to UUID and replaced the second with 'root=/dev/sda1'. The results were the same, except that it came up saying it cannot find device sda1 instead of the UUID. The last error to cross the screen before it would accept an 'exit' command was:
 
endrequest: I/O error, dev sda, sector 40132352
Buffer I/O error on dev sda, logical block 40132352
 
Then after I type 'exit' I get:
 
No resume image, doing normal boot..... 
 
And then the system comes up fine. I moved the drive to the other machine (identical) and all was the same. I notice during the (troubled) booting that the hard drive access light stays on solid, but the actual hard drive led only blinks every 30 seconds. So it does seem that the buss is searching, but cannot find the drive. I also removed all other IDE devices, so this drive is the only one in the machine. Lastly, I ran spinrite on the drive and it came up clean. The system works fine under XP.... But I don't want to use XP (*&^%$#@!). 
 
I also tried adding back root=(hd0,0) where I removed the first line. No Difference :confused:
 
Any further ideas are welcome!!!
 
Bob

---

### Post by keroman on 2010-05-17
I am sure its very annoying for you with this problem, type this in search,   [Neobuntu]("http://ubuntuforums.org/member.php?u=45839")

and look at the thread that has "all variants" in title,third one down, this may be of help. read it all first.

---

### Post by oldfred on 2010-05-17
I would also check your IDE configuration. Are you using cable select and is BIOS see both drives with 80 conductor cables. Or are you using 40 conductor cables and setting one drive as master and the other as slave?

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

---

### Post by BobbyDing on 2010-05-18
Thanks for the tips!!!

I followed your advice and checked out the IDE setup. I had the HD and DVDROM set to master/slave, but went ahead and set them to CS, and installed a fresh new cable. No difference. I have another thread going in the general problems. Since this has gone way past a simple newbie issue, I think I'll continue with that thread.

Thanks Again!!!

Bobby

Other Thread Here: [http://ubuntuforums.org/showthread.php?p=9322925#post9322925]("http://ubuntuforums.org/showthread.php?p=9322925#post9322925")

---

