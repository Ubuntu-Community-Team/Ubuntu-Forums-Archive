---
title: "Uninstalling ubuntu"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by cf0531 on 2010-10-28
I had installed ubuntu on a friends laptop as a dual boot with windows vista. Turns out he doesn't reall;y care for ubuntu and now I need to figure out how to get it off. i triedexpanding vista over all the partitions on a desktop I had, but that caused propblems when my computer started looking for grub, so I just had to do a whole new install. I don't want to have my friend gop through that, so how do I keep vista intact and just remove ubuntu, thanks

---

### Post by uRock on 2010-10-28
Using a LiveCD, delete the ubuntu partitions, then follow these instructions. > **presence1960 said:**
> You can repair the MBR to a windows MBR from  ubuntu or the ubuntu live CD. Install lilo by running in terminal  ```
sudo apt-get install lilo
```Ignore the warning and next run in  terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your  disk/device, i.e. sda, sdb,sdc, etc

---

### Post by cf0531 on 2010-10-30
it's not recognizing his wireless chipset so he is unable to get acces to the internet so wont the apt-get command not work?

---

### Post by nitstorm on 2010-10-30
Pop in a Windows Recovery disc or use a windows vista installation disc and go to the recovery option there, there u type
```

fixmbr

```

That should do the trick hopefully...

---

### Post by uRock on 2010-10-30
> **cf0531 said:**
> it's not recognizing his wireless chipset so he is unable to get acces to the internet so wont the apt-get command not work?
Lilo is supposed to be on the LiveCD ISO. I am downloading it as I type and I will test to see if Lilo will install with no Network connection and reply again in a few minutes.

---

### Post by uRock on 2010-10-30
There is the possibility that ubuntu 9.10 LiveCD will work with the wireless, as it has a driver package that 10.04 and 10.10 doesn't have. 

I checked a few ISOs and they all require a network connection. You will either have to run the Windows repair disk or connect to a wired LAN and install lilo from a LiveCD using that.

Don't forget to delete the ubuntu install before installing Lilo or running the fixmbr via Windows.

---

### Post by cf0531 on 2010-11-01
> **uRock said:**
> There is the possibility that ubuntu 9.10 LiveCD will work with the wireless, as it has a driver package that 10.04 and 10.10 doesn't have. 
 
I checked a few ISOs and they all require a network connection. You will either have to run the Windows repair disk or connect to a wired LAN and install lilo from a LiveCD using that.
 
Don't forget to delete the ubuntu install before installing Lilo or running the fixmbr via Windows.
 
where can I download the past distro iso's?
 
and can I just delete the ubuntu stuff in windows and run fixmbr?

---

### Post by uRock on 2010-11-01
You may download from here [http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Yes, you can delete the ubuntu partitions and run the fixmbr command in Windows. If you have a Windows repair CD, then you are good to go, if not, then you may want to create one just in case there are problems.

If you pan to install Ubuntu 9.10, then you do not have to delete partitions first. You can install the system in the used EXT partition(s).

---

### Post by cf0531 on 2010-11-01
Forgive me for dragging this on, I just want to be absolutely sure I get this right since its not my computer.

In vista, I can delete all partitions made by the ubuntu install the grub loader, the swap space, everything. then go to the run and type in "fixmbr"?

do I need a recovery disk to do this?
if I dont need one and I do this is the probability high that something might go wrong?

Am I better off just waiting to download the 9.10 distro and seeing if I can do it that way before I try doing it through windows?

and to clarify the live cd process.

i'd go through as if I'm installing ubuntu and when I get to the partition management utility I'd just delete everything ubuntu-related including grub, then duck out of the install process, run terminal and run the commands you gave me, correct?

I appreciate your patience with me and the time taken to help me. Hope I'm not being annoying, I just want to make sure I do this correctly. Thank you.

---

### Post by uRock on 2010-11-01
Being it isn't your system, I'd recommend running a backup and creating the system repair disk.

---

