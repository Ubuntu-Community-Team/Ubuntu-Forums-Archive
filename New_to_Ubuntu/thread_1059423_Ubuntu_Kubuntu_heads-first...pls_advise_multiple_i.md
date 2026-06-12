---
title: "Ubuntu/ Kubuntu heads-first...pls advise multiple issues"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Sabz on 2009-02-03
helloo unix experts,
i'm proud to finally be apart of this community, ive been a tecky for a long time now and i though its about time a take the plunge for open source, choosing ubuntu as my first distro flavor, i highlighted the questions for the lazy folks... i feel ya! lol

Ive been using the infamous microsoft windows since... too long if u ask me!

ive been reading and researching all about the OS and community for months now and i feel my OS should be aligned with my beliefs; free information from the hoarders and captives. still getting to grips with the terminal and doing some C/C++ studying... can some1 refer me to a guide for X windows users. ive read the Kier Thomas one though.

I have 2 machines currently and have had some good fun (and agony) trying to install *ubuntu and get things running on both. unfortunately i hit a few walls which i'm sure with some assistance from the good people here will soon be overcome.
i have divided the post in to 2 parts depending on the problems found on each machine.

[INDENT]Machine 1: Desktop- Dualboot
Mobo: ASUS p5l2d-vm
CPU: P4 prescott @ 4ghz
RAM: OCZ 2x2 reaper 1066
GFX: ATI powercolor 4870 1gb
HDD's: IDE 160 gb, sATA 320gb and 640 gb
OS's: winXp sp3 & Kubuntu 8.10 -intall using wubi[/INDENT]

ok ill jump quickly into the questions and problem so this thread doesn't end up like a blog. The machine installed kubuntu with in windows as mention how ever it isn't recognizing my video card on boot so as soon as i choose kubuntu (from windows MBR) its starts loading then  very shortly the screen turns white and stays, i hear the welcome screen tune. i believe this can be fixed by making sure grub/sgrub handles boot operations then i can boot into kubuntu (VGA troubleshooting) and download ATI proprietary software (where? link?).... i assume this is the easiest and best way? pls correct me if i'm wrong.
[B]
1)how do i make grub handle boot without access to Kubuntu?[/B]

Concerning machine 1 is there anything other compatibility issues i should know about; this is a temporary setup as i have a new mobo/cpu on the way. and will probably have a proper dualboot with Oses on separate hdds
its a shame we still need windows for the on/off gamer.. GO openAL :)

Also as i was browsing the kubuntu install through windows i noticed a few folders hinting to an AMD 64 installation could wubi have mixed up and downloaded the wrong iso? i understand it should be a "i836" copy correct?
[B]
2) could wubi have mixed up and downloaded the wrong iso? (i386 Vs Amd64[/B])
==================================================================================================
[INDENT]Machine 2: laptop 
HP Pavilion dv4000
Hdd: 80 gb
ram: 1gb ddr i think
cpu; intel M 1.8ghz
gfx: who cares lol
OS: win xp originally then failed to dual boot so now ububtu 8.10 only[/INDENT]


The laptop was my first unix installation it had winXP running and suffering BADLY. put Intrepid Ibex live CD rebooted, had some partitioning problem but resolved by wiping windows all together. its running well so far, subscribed to a few medi repositories and codecs, checked for the Load_cycle_count issue, don't seem to be affected..  strangely enough. 
As for partitioning, the current situation is that i have root "/" on a 20Gb partition which leaves ~70gb ..used to be winxp now reformatted to ext3 however i don't seem to have write permission on  /media/disk because it won't copy or move anything to the other partition. is there some sort of restriction i'm missing here.
the permission at the command line (drwxr-xr-x) seem to verify that i required root powers to write and access the mountable 70gbs hdd however no prompt is given just a error msg stating "you do not have permissions" 
so...

**3)do i try to add the 70gb partition to the root directory with Gparted cuz of some access restriction or do i just have to do it through the command line using sudo? and how do i give root powers through GUI (Gnome and KDE)?**
[B]
4) Is it possible to dual boot ubuntu and Mac Osx on the lappy, from my research it has to be a X86 kernel moded copy, and not the kalaway flavour i have lying around here some where? is it advisable in terms of stability under day-to-day operations... (links?..) [/B]

wow you made it this far, i salute u sir and thank you kindly for your support. it has been a love-hate relationship so far; waiting to catch that learning curve though.

Thanks
Sabz
all your help is much appreciated.. more as it unfolds

---

### Post by Xbehave on 2009-02-03
> As for partitioning, the current situation is that i have root "/" on a 20Gb partition which leaves ~70gb ..used to be winxp now reformatted to ext3 however i don't seem to have write permission on /media/disk because it won't copy or move anything to the other partition. is there some sort of restriction i'm missing here.
the permission at the command line (drwxr-xr-x) seem to verify that i required root powers to write and access the mountable 70gbs hdd however no prompt is given just a error msg stating "you do not have permissions"
so...
is the drive mounted & if you browse into it can you then see the files?
.
> 3)do i try to add the 70gb partition to the root directory with Gparted cuz of some access restriction or do i just have to do it through the command line using sudo? and how do i give root powers through GUI (Gnome and KDE)?gparted will need to be launched with gtksudo (i think perhaps its gtksu) or kdesudo gparted, sudo gparted could (again this is just what i think as ive never personally seen it happen) mess up your X session, but you should be able to get away with it anyway


> 4) Is it possible to dual boot ubuntu and Mac Osx on the lappy, from my research it has to be a X86 kernel moded copy, and not the kalaway flavour i have lying around here some where? is it advisable in terms of stability under day-to-day operations... (links?..) 
youd have took at how to setup macOS because its not entirely legal, but i think tis possible.

---

### Post by cariboo on 2009-02-03
> ok ill jump quickly into the questions and problem so this thread doesn't end up like a blog. The machine installed kubuntu with in windows as mention how ever it isn't recognizing my video card on boot so as soon as i choose kubuntu (from windows MBR) its starts loading then very shortly the screen turns white and stays, i hear the welcome screen tune. i believe this can be fixed by making sure grub/sgrub handles boot operations then i can boot into kubuntu (VGA troubleshooting) and download ATI proprietary software (where? link?).... i assume this is the easiest and best way? pls correct me if i'm wrong.



When you are at the grub menu, choose recovery mode, and at the the menu select xfix, once it is done select resume and you should boot to your desktop in default resolution. You can then load the correct video driver using System-->Administration-->Hardware Drivers.

> Concerning machine 1 is there anything other compatibility issues i should know about; this is a temporary setup as i have a new mobo/cpu on the way. and will probably have a proper dualboot with Oses on separate hdds
its a shame we still need windows for the on/off gamer.. GO openAL

Also as i was browsing the kubuntu install through windows i noticed a few folders hinting to an AMD 64 installation could wubi have mixed up and downloaded the wrong iso? i understand it should be a "i836" copy correct?

I hope i836 is a typo. The only way you could have installed an AMD64 version is if you downloaded the iso and burnt it yourself.

To check what version you have installed, open a Applications-->Accessories-->Terminal and type:

```
uname -a
```

For a 64bit version you should see something like this:

```
Linux jack 2.6.28-6-generic #17-Ubuntu SMP Fri Jan 30 15:35:08 UTC 2009 x86_64 GNU/Linux
```

note on my system the x86_64.

As an aside Linux has more in common with [Minix]("http://en.wikipedia.org/wiki/Minix") then [Unix]("http://en.wikipedia.org/wiki/Unix").

Jim

---

### Post by Sabz on 2009-02-04
> **Xbehave said:**
> is the drive mounted & if you browse into it can you then see the files?

Yes it is mounted! i can see only one directory "Lost+found" which i'm assuming is similar to windows recycle bin correct? 
.> 
gparted will need to be launched with gtksudo (i think perhaps its gtksu) or kdesudo gparted, sudo gparted could (again this is just what i think as ive never personally seen it happen) mess up your X session, but you should be able to get away with it anyway 

 i think u have me misunderstood, i have no problem launching Gparted, my issues is not being able to write to the extra 70gigs of space on "/media/disk" because of permissions. 
maybe this could be a solution:
 ```
 cd /media/disk | kdesudo mv "anyfile" 
``` or sthg like that, but surely there is way to do it bu using the GUI only and not terminal....[/QUOTE]


As for the mac OSx i though it was ok if i just stick a apple logo on the lappy :-p.. 
Should be looking into Jas "Osx86"?

---

### Post by Sabz on 2009-02-04
> **cariboo907 said:**
> When you are at the grub menu, choose recovery mode, and at the the menu select xfix, once it is done select resume and you should boot to your desktop in default resolution. You can then load the correct video driver using System-->Administration-->Hardware Drivers. 

Thanks everyone for you replies they have been very helpful, however i don't think i was clear enough. the problem here is that; the boot is handled by windows (MBR) so i don't get to see the grub menu at all just the boot option "XP" OR "Kubuntu" 
so how can i replace MBR with GRUB so i can boot in recovery mode.. and will it affect my dualboot when using wubi?


> 
I hope i836 is a typo. The only way you could have installed an AMD64 version is if you downloaded the iso and burnt it yourself. 

No i had wubi handle that. ill double check this when i manage to boot into kubuntu, but its probably nothing to worry about, as i mentioned earlier its probably some extra installation files.

---

### Post by avtolle on 2009-02-04
FWIW: if you are in a Wubi install; after you select Kubuntu from the Windows bootloader, you should then go to grub (at least that's how it works with my Ubuntu 8.10 install using Wubi w/in Vista) and have the option to press Esc to enter the menu (mine, be default has a ten second countdown) to select the recovery mode.

On the 70gb issue; when you installed Kubuntu within Windows, you selected the size of the "drive" to be created for the Kubuntu install. To enlarge, you need to use LVPM; please go to the Wubi sub-forum and read the LVPM sticky; you might also want to take a look at the Wubi FAQ sticky and follow the links therein contained. You will NOT be able to add the additional space to the Kubuntu partition/install in the traditional manner with a Wubi install.

On the 64 bit vs. 32 bit install; if you used Wubi.exe to d/l the iso, and your system is a 64 bit system, the 64 bit iso was downloaded and installed; again, take a look at the Wubi FAQ for a method to use a 32 bit iso, which, as I recall, involves downloading the iso and placing it within the same Windows directory as wubi.exe, then starting wubi and causing it to use the downloaded iso rather than downloading from the site automatically. Good luck.

---

### Post by Sabz on 2009-02-04
> **avtolle said:**
> FWIW: if you are in a Wubi install; after you select Kubuntu from the Windows bootloader, you should *then go to grub *(at least that's how it works with my Ubuntu 8.10 install using Wubi w/in Vista) and have the option to press Esc to enter the menu (mine, be default has a ten second countdown) to select the recovery mode.
when choosing Kubunbtu from XP bootloader all i get is a white screen and thats it, i belive its a driver issue due to the lack of suoport for ATI graphics cards. If i can get to the grub menu the issue can be resolved however the screen just stays white?????

> **avtolle said:**
> On the 70gb issue; when you installed Kubuntu within Windows, you selected the size of the "drive" to be created for the Kubuntu install. To enlarge, you need to use LVPM; please go to the Wubi sub-forum and read the LVPM sticky; you might also want to take a look at the Wubi FAQ sticky and follow the links therein contained. You will NOT be able to add the additional space to the Kubuntu partition/install in the traditional manner with a Wubi install. 

Hehehe the 70gb issues is on the laptop my friend, which was installed using the Ubuntu Live CD and NOT wubi or Kubuntu. its seems my classification wasn't as clear as i thought; everyone is mixing up problems between the 2 machines!... my bad.

Ive been doin some reading is there a way to have the rest of the partition (70gigs) mount as "/home" instead of "/media/disk" maybe that way i can get write privileges ??

> **avtolle said:**
> On the 64 bit vs. 32 bit install; if you used Wubi.exe to d/l the iso, and your system is a 64 bit system, the 64 bit iso was downloaded and installed; again, take a look at the Wubi FAQ for a method to use a 32 bit iso, which, as I recall, involves downloading the iso and placing it within the same Windows directory as wubi.exe, then starting wubi and causing it to use the downloaded iso rather than downloading from the site automatically. Good luck.

I doubt wubi installed the 64-bit iso, because as i understand it, the CPU running on that machine doesn't support 64 architectures anyways (i think.. P4 ).  as mention this issue will be double-checked when i manage to boot into Kubuntu first!

---

