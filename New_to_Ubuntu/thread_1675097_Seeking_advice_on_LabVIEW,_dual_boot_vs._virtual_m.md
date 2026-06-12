---
title: "Seeking advice on LabVIEW, dual boot vs. virtual machine"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by cayleigh on 2011-01-25
[FONT="Arial"]Hi all! 

I am ready to take the plunge. I just bought a new laptop which already has Windows 7 installed, along with an unbelievable amount of crap from Sony, and I am trying to decide between dual booting or virtualization (the latter would be Ubuntu 10.10 as my host and Windows 7 as guest). I have my Ubuntu CD and my Windows 7 backed up so I am ready to go for either option. 

I am leaning towards virtualization at this point but my only hesitation is that I've heard there can be problems with USB devices. The one thing I am really keeping Windows around for is that I have to use LabVIEW Student Edition for a class, (there is a linux version but not for students - it is $4500!), and we'll be programming based on interface from real world input, such as measuring current through a circuit for example, which I think will be done through some sort of USB device (we obviously have not gotten to this section of the course yet or I would have a better idea of what I'm talking about).


My questions:

- Does anyone have experience using LabVIEW, and do you know if there would be any problems with the USB input or otherwise when running it from Windows 7 in a virtual machine?

- For a total beginner who is planning to do most computing on Ubuntu and just a few things on Windows (see below), but has zero experience with Linux, do you think virtualization or dual boot is the way to go?

- If I were to dual boot instead, what do you think of 50GB for windows, 20 GB for /, 8 GB for swap, and the rest for /home? I know this gets asked a lot, but as a beginner I would just feel better getting the green light before I do it.

I have been spending my last few days pouring through these forums, thanks so much for all of the help you've already given me! I just need a little personalized advice now. I can't wait to get rid of Windows! The other night I was working on a lab report in the starter version of Microsoft Word, and discovered that there is a !FLASHING! !ADVERTISEMENT! in the corner that can't be turned off. That was the last straw... 

Thanks so much and sorry for the long post,
Cayleigh



Here is some information about my computer and what I do on it in case this helps:
Sony VAIO VPCEB390X
Intel® Core™ i5-460M processor (2.53GHz) with Turbo Boost up to 2.80GHz
500 GB (5400rpm)
4 GB RAM
(OK I splurged a litte :) )

_Stuff I'll be doing:_
firefox
open office - writer,calc,the power point thingy
LT SPICE equivalent (circuit analyzation software)
MATLab
listening to music
watching movies
skyping
(possibly eventually some kind of AutoCAD equivalent as I get further in my degree but this is just speculation, not a deal breaker)

_stuff I'll be doing on Windows_
LabVIEW
Rosetta Stone (maybe)[/FONT]

---

### Post by LewRockwellFAN on 2011-01-25
Unless you have a lot of data you need all that space for, I'd dual boot. Why not? You've got plenty of room for it. If you want you can run a virtualbox with another installation of windows on it ALSO. So if you want to do some Windows thing without closing down the Ubuntu, you can. But if you plan to be using Windows more than trivially for a few hours you can reboot and work faster in the real deal. Your partition plan sounds quite workable to me but 8 giB of swap seems like real overkill. You might want to get some input from laptop users on that issue as I'm a desktop user and never hibernate. I would think more than 5 would be overkill even for that.  With 4 \giB of RAM I wouldn't use swap at all but many disagree. On using "[FONT=Arial]the rest for /home" you might want to think about the details before you do that. Depends on what you wind up doing with each OS but you might want a substantial partition for a data area usable by both OSs. I THINK you can use your home partition that way provided you use a filing system both OSs can understand. Windows can be taught to use some of the extN systems. I'm not sure if it can be taught to use all of them or to do so without problems. There are weird permission issues when you have files accessible to both OSs. No show stoppers but it can surprise you until you finally realize linux just can't deal properly with the permission schemes native to FAT and NTFS. And this is probably true the other way around but I haven't tried. Like forget about marking individual text files on a FAT or NTFS system read only to protect yourself from booboos. Linux won't notice. To me it has seemed easier to have a separate data partition and keep home small for linux stuff like configuration files, logs, and icons. But that could just be a reflection of my own ignorance. I'm no expert. Heck, I'm still trying to wrap my mind around symlinks and inodes. My 2cents, anyway. You'll probably have more erudite answers by the time I finish typing this cause I am the World's Slowest Touch Typist.. Good luck.
[/FONT]

---

### Post by cayleigh on 2011-01-25
[FONT="Arial"]Thanks for the advice. I had thought about doing a separate /data partition (probably NTFS) but in all honesty I don't think I'll really need to access my Ubuntu files from Windows, which as I understand it would be the only reason to do that since Linux can read the Windows files just fine (please correct me if I'm wrong). 

I guess it is hard to tell exactly how I will use it until I try it for awhile, so maybe the better question to ask is which option leaves me the most flexibility if I want to change it later? Does it make any sense to leave a section un-partitioned/empty in case I want to create /data later?

Regarding the 8 GB swap, I kept reading 1-2x RAM, so I figured I'd go 2X since I have lots of space.

I appreciate the advice, I am in the middle of a busy semester so I'm really trying to do it right the first time around. 
[/FONT]
Cayleigh

---

### Post by LewRockwellFAN on 2011-02-07
> **cayleigh said:**
> [FONT=Arial]
I guess it is hard to tell exactly how I will use it until I try it for awhile, so maybe the better question to ask is which option leaves me the most flexibility if I want to change it later? Does it make any sense to leave a section un-partitioned/empty in case I want to create /data later?[/FONT]
Cayleigh
Sure. Or, alternately, since if you have the space you might as well make it accessible since you might want to use it,you can split all the leftover space after you make your system (and maybe swap) partitions in half and make half /home and half /commondata. You can mount /commondata (or whatever you want to call it) as /media/commondata. You specify that in the installation process. There is a little drop down menu of choices of how to mount a partion but you aren't limited to those choices. You can type in whatever you want.   You can also change it later if you want. That's how I have it. I'm pretty sure you could also mount it under home as ~/commondata but I haven't tried that because the last time I installed I didn't understand you can pretty much mount it anywhere and I was just slavishly following some instructions I didn't totally understand. As I understand it now "where" you mount it is basically like putting a shortcut wherever you want in the filesystem that the linux in question is installed in. Meaning like everything under / ("root"). You can always use gparted to shrink one partition and grow another later. Or delete one and fill the space with the other.

As for reading any filesystem from either OS, linux has drivers to read and write to any of the MS file systems and there are Windows drivers for most (maybe all, I'm not sure about ext4) 'nix file systems. So that shouldn't be too big a deal EITHER way. BUT neither OS handles the permission systems of the other's file systems correctly. Not even for FAT32. So be wary of making assumptions that involve how permissions will work when dealing with a FAT or an NTFS from a 'nix or an extN from Windows. This usually isn't any big deal with data files. For me it is most noticeable and annoying in that I can't mark a text file read-only to protect myself from accidentally changing a text file when I read it with gedit.

As for how much swap, yeah, I've been seeing those same sorts of recommendations since long before hibernation was an issue, and outside of hibernation, I've never seen a rational justification for them that made sense to me. So the more memory I have the more I need a SUBSTITUTE to pinch hit for memory???!!!??? Never made any sense to me and still doesn't. I quit worrying about it when I saw some people far geekier than I who wrote that that rule of thumb was pure BS, MS official recommendations be darned, and seemed to have the same reasoning I did. Still, if you have space to waste so to speak, the only downside to having a swap I can think of is that if you have a program with a memory leak it might slow you down when you start using the swap but since things still would work you might not notice it and just work slower whereas without swap you would start tracking down the error. Now if it wasn't a correctable malfunction but just a program that legitimately used that much memory of course that would mean you really needed the swap to make effective use of the program in question. But once again, either way you do it, you can change it later without having to completely reinstall. But reinstallation isn't such a big deal anyway as long as you are careful to not overwrite your home, or, alternately, if you keep your data somewhere else. The only really bad mistake imo is to keep all your data in home without making home a separate partition. Then you need to be real careful not to reformat if you reinstall. Of course if home has your data you need to be careful not to reformat home itself anyway. Reinstallation is a breeze with clonezilla if the backup of the installation is on another partition of your hard drive. So, kinda hard to make a mistake you can't change pretty easily or work around no matter how you do it.

---

