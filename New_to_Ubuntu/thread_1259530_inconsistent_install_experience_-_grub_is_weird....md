---
title: "inconsistent install experience - grub is weird..."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by pablolie on 2009-09-06
i consider myself reasonably experienced with installing ubnuntu at this point in time, even though by no means an expert.

but i must say the inconsistent results i sometimes get with ubuntu installs are weird - and it always acts up at the end: grub sometimes sticks, sometimes it doesn't. and it is not because there is a lot of room to make mistakes: the alternate CD merely asks for confirmation on whether it is true there is another OS present (Vista) and whether it should install Grub... and that is that.

so while trying toi install a dual boot system on a new Intel X25 SSD, this is what happened...

1. i install Vista Ultimate 64 bit. it is lengthy and a pain in the b*tt. but it works and boots ok.

2. in vista, i shrink the volume to leave 10GB for Ubuntu. this new partition is left untouched now.

3. i pop in the alternate Ubuntu 64 9.04 disk. go through the motions.

4. partition time - i tell the partitioner that the 10GB ssd section is all for ubuntu. primary partition (i tried logical as well, doesn't make a difference), noatime, *not* bootable (since if doing so the entire system becomes unbootable, not an option).

5. everything goes fine. 

6. ah, grub decision time. i confirm that Vista is present, and tell the installer to install grub to the MBR. 

7. reboot time...

8. disappointment ensues. it boots into Vista only. Ubunt doesn't exist, install procedure obviously did not write Grub to the MBR, not correctly anyhow.

9. i try to correct this by tinkeruing with EasyBCD in Vista. EasyBCD sees the Linux partition, i set it up.

10. booting now i get a choice between Vista and Ubuntu. I can boot into Vista. Ubuntu is dead, it will fail to start up. it either boots into a grub text menu, or fails altogether, depending on whether i tell EasyBCD that grub is or isn't present.

so mny hunch is that there is a problem with the alternate Ubuntu 9.04 64 bit disk. that it does not install Ubuntu correctly. can anyone confirm if there is a known issues with that?

---

### Post by NoaHall on 2009-09-06
Why are you using the alternate Ubuntu disk?

---

### Post by pablolie on 2009-09-06
> **NoaHall said:**
> Why are you using the alternate Ubuntu disk?

is there a reason why i should not?

the reason is the standard 64 desktop installation disk has issues with something in my system and freezes. i think it is an intel chipset issue.

---

### Post by NoaHall on 2009-09-06
Well, I wouldn't use unless needed. 
Hm.. Two errors from two disks. Did you check the .iso file before burning it?
Also, what's your system's specs? Motherboard, cpu , gpu, ram etc.

---

### Post by pablolie on 2009-09-06
> **NoaHall said:**
> Well, I wouldn't use unless needed. 
Hm.. Two errors from two disks. Did you check the .iso file before burning it?
Also, what's your system's specs? Motherboard, cpu , gpu, ram etc.

the weird thing is that 8.04 was running on this system without a hitch. 9.04 was the end to my ability to run Ubuntu on this system. i thought by moving away from a RAID i'd be able to easily go dual boot again. no such luck, 9.04 is an issue for me. so right now i am about to try with 8.04.

the configuration is pretty vanilla:
asus p5q-em mobo
8gb of ram
intel x25 ssd
asus 9600gt silent video card

should run like a charm. doesn't. i will try to tinker with BIOS settings (perhaps the plug & play BIOS thing, but i have left them in standard settings)... 

in the end, what bugs me is the fact that the install fails at the very end, that Grub is NOT installed to the MBR despite the installer's insitence it did. that is the part i do not understand. i have never happen this in Ubuntu before - i have had it claim sole owenrship of my system and forget about vista, but never claim that it is installed and then be missing in action...

---

### Post by NoaHall on 2009-09-06
I think it's the SSD. I'd go with 8.04, and wait for 9.10 to come out before upgrading, and then do it with the update manager, not a fresh install (should prevent too much problems)

---

### Post by pablolie on 2009-09-06
> **NoaHall said:**
> I think it's the SSD. I'd go with 8.04, and wait for 9.10 to come out before upgrading, and then do it with the update manager, not a fresh install (should prevent too much problems)

The alternate 64 8.04 cd will not see any of my drives and asks for a driver, yikes. Guess I will have to comb the intel website for a linux driver with the integrated G45 chipset...

---

### Post by pablolie on 2009-09-06
> **pablolie said:**
> The alternate 64 8.04 cd will not see any of my drives and asks for a driver, yikes. Guess I will have to comb the intel website for a linux driver with the integrated G45 chipset...

i think the problem is that the grub is always installed to hd0... meaning sata port 0? but my c drive and thus the boot drive is sata port 1 and probably hd1? i have no idea why the install process gets this wrong given the fact that it correctly detect the vista partition *and* is installed on the same drive...?

just thinking out loud. i think i will make the ssd port 0 and see what happens.

---

### Post by mbzn on 2009-09-06
Try to just change the bootorder in the bios. I had a simular problem a wile back and after hours of struggle it took just 10 second to fix. Not saying it will work but its worth a try.

---

### Post by pablolie on 2009-09-06
> **mbzn said:**
> Try to just change the bootorder in the bios. I had a simular problem a wile back and after hours of struggle it took just 10 second to fix. Not saying it will work but its worth a try.

thanks for the suggestion - tried it and it does not seem to make a difference. hm. i am frustrated. it does install alright - it is just frustrating to see the dual boot does not work as it should despite a user (me) providing the correct information to the installation process.

i will crack this nut and provide the feedback to the development team. i think the way for Ubuntu to thrive is the dual boot environment, and that must work well and easily for users. the fact this is an SSD should not make an ounce of a difference.

my guess now is that the install process in some instances ignores the BIOS boot setting and stubbornly assumes the first SATA port is the boot drive, and thus installs the Grub dual boot record in a useless place...

---

### Post by mike555 on 2009-09-06
perhaps you should install grub to the partition your installing ubuntu to?? I don't use Vista so not sure ..

---

### Post by louieb on 2009-09-06
Since you've seem to know quite a bit about dual booting. I think the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") should help quite a bit. At least it will tell you which MBR grubs stage1 code is in (if any). 

These instructions are for the Ubuntu live cd but can be used with almost any live CD or hdd install. [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

BTW: the alt CD or net install CD is about all I ever use. Both use the Debian installer. Just my 2 cents - Wish the Live CD installer were as good.

---

### Post by pablolie on 2009-09-06
let us see, if i switched the SSD to the first SATA port on the mobo. have disabled every other drive on the mobo bios.

i shall report back in an hour or two. the suspense builds...

if this doesn't work, i will research EasyBCD to set things up again. the easy way didn't work. i just know the Ubuntu install is fine, it is just Grub and the MBR that wind up weird...

thanks a lot everybody for your help and ideas!

---

### Post by pablolie on 2009-09-06
well this is getting intensely frustrating.

there is an issue with ubuntu install from any live disk onto my system. not good.

i hjave ubuntu running on 2 other systems (one of them also with decreasing reliability), and am about to give up for this one (my main machine).

shame.

things have not been going well for me with Ubuntu since leaving 8.04 behind.

i do hope things get better again...

---

### Post by pi.boy.travis on 2009-09-06
Wait, so you *don't* set the bootable flag on the partition editor?  I believe that you render GRUB unable to boot Ubuntu.  Why is it that you can't set the bootable flag?

---

### Post by pablolie on 2009-09-06
> **pi.boy.travis said:**
> Wait, so you *don't* set the bootable flag on the partition editor?  I believe that you render GRUB unable to boot Ubuntu.  Why is it that you can't set the bootable flag?

there is a major warning - Ubuntu warns you that to set the bootable flag leads many BIOS to quit. it's there in big letters.

and when i tried (which i did) my entire system went to the dogs - and i had to reinstall vista from scratch.

---

### Post by pablolie on 2009-09-06
well, finally. one last try and it finally seems to work. grubs offers me ubuntu and vista and i can boot into ubuntu 64 9.04. cause for celebration (i have not yet tried to boot into the vista partition, but am confident i can).

but heck, this was unpredictable. i change some BIOS settings. boot once into the Ubu64 install CD... system freezes. do it again - success. very strange and does not fill me with confidence.

key BIOS settings i changed on the p5q-em board (and given the somewhat unpredictable system behavior i doubt they are all necessary)...

disable Plug & Play OS
set drive to IDE strict compatbility (not enhanced)
disable the C0-C1-C2 processor setting or something like that
make sure you boot drive is in SATA slot 1

i'll keep observing - it bugs me i can't truly find the logical linearity in this path to momentary success... but i am glad i am there.

---

### Post by louieb on 2009-09-07
> **pablolie said:**
> Ubuntu warns you that to set the bootable flag leads many BIOS to quit. it's there in big letters.

Just wondering where you saw that. Just my experience that Linux including Ubuntu does not care and makes no difference if the boot flag is set or not.

> **pi.boy.travis said:**
> Wait, so you *don't* set the bootable flag on the partition editor?
set or not makes no difference to Grub.  

The only OS I know that wants the boot flag set on its booting partition are  Windows versions up to and including XP. Not sure about Vista and Win 7 but do know that the Win 7 install did set the boot flag **on** for its partition.

---

### Post by pablolie on 2009-09-07
> **louieb said:**
> Just wondering where you saw that. Just my experience that Linux including Ubuntu does not care and makes no difference if the boot flag is set or not.

In the 9.04 alternate 64 install disk, the partition editor warns you loud and clear, telling you the bootable flag can consitute a big problem for most BIOS. It basically tells you not to set it.

but that was not the problem. in the end, i am not sure *what* the problem was. i tinkered a little with the BIOS settings. then stopped doing so. simply tried again after the installer had frozen. and then it worked.

very strange. but i am typing this from a dual boot system, just as i originally intended to.

---

