---
title: "Help With Triple Boot Install"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by LuciferDarkWatch on 2011-02-07
Hi All

I Currently have Windows 7 and Ubuntu 10.10 on dual boot system,

But i want to change that

I want Win 7, openSuse 11.3 and Ubuntu 10.10 on a triple Boot

I have a 500gb sata hdd.

The Rough Plan was to 150gb for Win7, 150 for openSuse 11.3 (50gb for / and 100gb for /home) and same again for Ubuntu 10.10 and 50gb for Swap

Im using entire drive for 3 Operating Systems and Swap.

I have read a few guides and they all say install win7 then opensuse then ubuntu, and thats fine but none say anything about partitioning.

And one main problem is cant split into more than 4 different partitions

So any and all input would be great help.

Thank you in advanced

---

### Post by LewRockwellFAN on 2011-02-08
Why can't you split into more than 4 partitions?  You aren't confusing the limit on primary partitions with a limit on the total are you? Normally, you install Windows on the first partition which is a primary. Then you can either make one or two primary and one extended partition and put any more you need in the extended as logical partitions or just make one extended after the primary and put all the additional ones there which is how most people do it.

As for partitioning that scheme should work. Personally I'd not give anywhere near that much to Windows 'cause I wouldn't plan on storing data in the same partition as the OS and programs which just makes it harder to backup the OS and programs with a cloning tool.  I'd probably go with 30 GiB and use the rest for a data partition  but maybe you install a lot more software than I ever did. In the linuxes the same objective can be achieved by making the homes separate partitions which when you reinstall you will be careful not to reformat or if you use a cloning tool you don't clone home. A lot of people would probably try to make the two linuxes use the same home. I've never tried that so I don't know how easy or advisable it is. I boot two versions of Ubuntu, two versions of Sabayon, and Windows 2k, for a total of 5 OSs. I do not keep data in home. In home I just keep stuff like config files and icons I've made for launchers, the desktop background (which is simply black with text on it to remind me what OS I'm using). So since home is very small I can keep it in the root partition and clone it along with the OS and software. There are minor problems in having common data partitions for Windows and linuxes having to do with permissions not working the way you expect them to. But nothing terrible once you know to look for that as a source of the problem when you have permission problems and realize Linux will not respect the Windows read only attribute. I can't see any reason at all not to share a data area between two linuxes. The next time I start from scratch I'll try to give clonezilla its own partition so I can run it from the hard drive rather than the cd.

---

