---
title: "Unable to restart,suspend and hibernate"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by John Phang on 2010-03-05
lately i have install kubuntu on my laptop, i found that kubuntu that on my laptop were unable to restart,suspend and hibernate. 
what should i do to enable these function to be use?
:confused:
can anyone please help me :)

---

### Post by Paddy Landau on 2010-03-05
Please be specific: Were those options missing from your shutdown menu, or did you find that when you tried, there was some error?

---

### Post by John Phang on 2010-03-05
It doesn't has any error message, it just hang and the screen turns black in color.
no matter on restart,suspend or hibernate it just has the same problem.

---

### Post by Paddy Landau on 2010-03-05
> **John Phang said:**
> It doesn't has any error message, it just hang and the screen turns black in color.
no matter on restart,suspend or hibernate it just has the same problem.
Are you saying that you press Restart, Suspend or Hibernate, and the screen just goes black?

Or does it close down the computer and only when it tries to restart (automatically for Restart or manually for Suspend or Hibernate) it goes black?

If it's the second, do you see the Ubuntu loading screen first? Does the computer go through the correct booting sequence (the BIOS stuff that shows you that the hardware is working before it starts to load Ubuntu or Windows or whatever)?

Or does something else happen?

We really need you to be *specific*, otherwise we're guessing and will probably give you totally wrong information.

---

### Post by John Phang on 2010-03-06
Yes, the screen just gone black. and it does not show anything. It just gone black and it stays like that till i shut down it manually.

---

### Post by switch10 on 2010-03-06
Make sure your swap partition is large enough.  It should be 2x the amount of ram you have.  

For example, in my desktop pc I have 8gb of RAM, so my swap is at least 16gb.  You can resize a partition with gparted.

Some hardware does not support hibernating.

---

### Post by Paddy Landau on 2010-03-06
> **switch10 said:**
> Make sure your swap partition is large enough.  It should be 2x the amount of ram you have.
That's quite contentious. You only need the amount of RAM to be able to hibernate, but with a recommended minimum of (depending who tells you) 512Kb or 1Gb. But if you have a large enough disk, it certainly won't hurt to have 2xRAM.

So, John...

[LIST]
[*]How much RAM does your machine have? If you don't know, then type the following command into your terminal and post the results.```
sudo lshw -class memory
```
[*]How large is your swap partition? If you don't know, then start GParted (Administration > System > Partition Editor or GParted) and post a screen-shot.
[/LIST]
 
> **switch10 said:**
> Some hardware does not support hibernating.
Yes, this may explain it. Let's wait for John to post his swap space and RAM size.

---

### Post by switch10 on 2010-03-06
> **Paddy Landau said:**
> That's quite contentious. You only need the amount of RAM to be able to hibernate, but with a recommended minimum of (depending who tells you) 512Kb or 1Gb. But if you have a large enough disk, it certainly won't hurt to have 2xRAM.

My system does not wake up from hibernate, or sleep, if my swap is not at least twice the size of my RAM.  I originally had an 8gb swap, waking from hibernation would not work....

---

### Post by Paddy Landau on 2010-03-06
> **switch10 said:**
> My system does not wake up from hibernate, or sleep, if my swap is not at least twice the size of my RAM.  I originally had an 8gb swap, waking from hibernation would not work....
That's really interesting; another piece to add to the chorus of opinions, thank you! I wish that I could find a definitive answer in Ubuntu's documentation.

---

### Post by agnes on 2010-03-06
I have 4GB RAM and 1GB swap, but it worked in Ubuntu 9.10 after installing the correct driver for my graphic card.
Tips 
- Check if your graphics driver is installed (sudo lshw -c display)
- Don't boot with the parameter "acpi=off" or "noacpi" (see /boot/grub/menu.lst)
- Also check if you have installed the packages 'uswsusp' and 'hibernate'.

---

### Post by soryu on 2010-03-06
- Don't boot with the parameter "acpi=off" or "noacpi" (see /boot/grub/menu.lst)
- Also check if you have installed the packages 'uswsusp' and 'hibernate'.

How do you do change ACPI=off or noacpi in menu.1st?
how do you check if installed? synaptic?
how do i know if correct driver is installed?
i installed what karmic says.

---

### Post by John Phang on 2010-03-06
Paddy, this is from terminal that after i type the code you give me
(sudo lshw -class memory) 

*-firmware                           
       description: BIOS               
       vendor: TOSHIBA                 
       physical id: 0                  
       version: Version 1.60 (08/05/2003)
       size: 128KiB                      
       capacity: 448KiB                  
       capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 12
       slot: CPU Internal
       size: 32KiB
       capacity: 32KiB
       clock: 1GHz (1.0ns)
       capabilities: internal write-back
  *-cache:1
       description: L2 cache
       physical id: 13
       slot: CPU Internal
       size: 256KiB
       capacity: 256KiB
       clock: 1GHz (1.0ns)
       capabilities: internal write-back
  *-memory
       description: System Memory
       physical id: 81
       slot: System board or motherboard
       size: 1GiB
       capacity: 1GiB
     *-bank:0
          description: SODIMM SDRAM Synchronous
          physical id: 0
          slot: DIMM 0
          size: 512MiB
          width: 64 bits
     *-bank:1
          description: SODIMM SDRAM Synchronous
          physical id: 1
          slot: DIMM 1
          size: 512MiB
          width: 64 bits

then i don't have Gparted on my kubuntu and i would like to know how to install it on kubuntu? 

Agnes,
sorry but i dont don't know how to check the acpi.. :P
but i hve check the graphic card that you told me (sudo lshw -c display)

*-display UNCLAIMED
       description: VGA compatible controller
       product: CyberBlade XPAi1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=8
       resources: memory:fc000000-fdffffff memory:fbc00000-fbffffff memory:f8000000-f9ffffff memory:f7ff8000-f7ffffff memory:58000000-5800ffff(prefetchable)

---

### Post by agnes on 2010-03-06
> **soryu said:**
> 
How do you do change ACPI=off or noacpi in menu.1st?
how do you check if installed? synaptic?
how do i know if correct driver is installed?


1. In Terminal, type "sudo gedit /boot/grub/menu.lst". First there are a lot of comments, then you see your configuration of the GRUB boot menu. You see e.g. the line ```
kernel /boot/vmlinuz-2.6.31-19-generic root=UUID=99dd5168-8b47-4201-8752-3622ae8c43b2 ro quiet splash
```. If acpi was disabled you would see ```
kernel /boot/vmlinuz-2.6.31-19-generic root=UUID=99dd5168-8b47-4201-8752-3622ae8c43b2 ro quiet splash noacpi acpi=off
``` acpi should not be disabled.

2. Yes, just type the package name (in this case 'uswsusp' and 'hibernate') in Synaptic, see if it's installed (checked). If not, install them.

3. In Terminal, type "sudo lshw -c display", under "product" you should see the name of your graphics card (e.g. "Mobility Radeon HD 3650"). If you don't see the correct name , the correct driver isn't installed. 
For the name of your graphics card you can type "lspci | grep VGA".
So you can check if they match. If not, you need to install the  correct driver.

Btw after this it may still not work... AFAIK a lot of people have issues with it.

---

### Post by John Phang on 2010-03-06
when i type (sudo gedit /boot/grub/menu.lst) in terminal it comes out like this :

sudo gedit /boot/grub/menu.lst
[sudo] password for john:
sudo: gedit: command not found

and i have check the graphic card driver and when i type (sudo lshw -c display) it come out like this :

  *-display UNCLAIMED
       description: VGA compatible controller
       product: CyberBlade XPAi1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=8
       resources: memory:fc000000-fdffffff memory:fbc00000-fbffffff memory:f8000000-f9ffffff memory:f7ff8000-f7ffffff memory:58000000-5800ffff(prefetchable)

under product its got the graphic card name, is this means that i have installed the correct driver for the graphic card?

---

### Post by Paddy Landau on 2010-03-07
> **John Phang said:**
> size: 1GiB
That means that you have 1GiB of memory, which is enough.

> **John Phang said:**
> then i don't have Gparted on my kubuntu and i would like to know how to install it on kubuntu?
If you enter the following command and post the output, we can see your partitions, unless your partition is not on sda.
```
sudo parted /dev/sda print
```If you want to install GParted (you don't have to), then simply install through Synaptic. System > Administration > Synaptic Package Manager.

---

### Post by John Phang on 2010-03-07
when i enter the code (sudo parted /dev/sda print) on terminal it comes out something like this:

Model: ATA IBM-DJSA-220 (scsi)
Disk /dev/sda: 20.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  12.6GB  12.6GB  primary   fat32           lba
 2      14.6GB  20.0GB  5363MB  extended
 5      14.6GB  19.7GB  5075MB  logical   ext4
 6      19.7GB  20.0GB  288MB   logical   linux-swap(v1)

---

### Post by Paddy Landau on 2010-03-07
You have a small disk at only 20Gb.

Right, so we know already that you have 1Gb RAM.

According to an [earlier post]("http://ubuntuforums.org/showthread.php?p=8925920#post8925920"), you need twice your RAM as swap, i.e. 2Gb (at the absolute least, you need the same amount, at 1Gb).

You have only...
> **John Phang said:**
> 6      19.7GB  20.0GB  288MB   logical   linux-swap(v1)
... a seventh of that (288Mb).

There is no way that your system can hibernate like that. I don't know whether that affects your suspend or restart.

I'm also a bit concerned about your partitions.

[LIST]
[*]Your primary partition is FAT32 at 12.6Gb. What do you keep there?
[*]Your second partition, ext4, comes in at 5Gb. I presume that's your Kubuntu?
[*]Your third partition is your swap at 288Mb.
[/LIST]
In order to free an extra 1760Mb RAM (to allow for 2Gb swap space), you need to take the space from somewhere else. I wouldn't advise taking it from your Kubuntu, because it will reduce it to a mere 3Gb (approx.), which would be a bit small.

That's why I want to know what's in your primary partition, the FAT32, so that a suitable plan can be made.

---

### Post by agnes on 2010-03-08
> **John Phang said:**
> when i type (sudo gedit /boot/grub/menu.lst) in terminal it comes out like this :

sudo gedit /boot/grub/menu.lst
[sudo] password for john:
sudo: gedit: command not found
That just means you don't have the text-editor program "gedit" installed.
My fault, I forgot you were running **K**ubuntu.
You can open the file with kate (sudo kate /boot/grub/menu.lst), or with kile.

> **John Phang said:**
> 
under product its got the graphic card name, is this means that i have installed the correct driver for the graphic card?
Yes. But isn't that quite an old card? See also [these search results]("http://www.google.nl/search?hl=nl&client=firefox-a&hs=7ZS&rls=com.ubuntu%3Aen-US%3Aofficial&q=site%3Aubuntuforums.org+CyberBlade+XP+Ai1&btnG=Zoeken&meta=&aq=f&oq="), maybe your problem is somewhere. However, simple as it may be, it should at least be able to restart. 

So I'd say, install the packages I mentioned before if you haven't already; if it still doesn't work, then another solution could indeed be what Paddy Landau is saying about the ram/swap.

Though I'd have to say (@Landau) that for me the "swap need to be 2 times your memory"-rule did not apply anytime for hibernating nor suspend, so it isn't an absolute rule.

---

### Post by Iowan on 2010-03-08
You're using which version of Kubuntu? 
[Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by John Phang on 2010-03-08
Paddy Landau,
the primary partition i'm keeping for windows xp, and you are right the second partition i'm using for kubuntu, then you said i need the swap partition to be 2gb? then how could i enlarge the swap partition without formatting?

Agnes,
sorry (i'm new on this) , but i'm not quite sure what information did i get from that forum you sent me... :P

Iowan, 
kubuntu 9.10

---

### Post by Paddy Landau on 2010-03-09
> **agnes said:**
> Though I'd have to say (@Landau) that for me the "swap need to be 2 times your memory"-rule did not apply anytime for hibernating nor suspend, so it isn't an absolute rule.
Agreed. There are cases where 1xRAM isn't enough (so much is going on that the swap is already quite full), but for the average user it must be rare indeed.

> **John Phang said:**
> ... the second partition i'm using for kubuntu, then you said i need the swap partition to be 2gb? then how could i enlarge the swap partition without formatting?
You're in a bit of a difficult place. You can't reasonably reduce partition 1, because Windows takes so much space.

Yet, partition 5 is about as small as you can reasonably make for Kubuntu.

The only way to increase your swap is to decrease your Kubuntu, and I'm guessing that that will leave you with too little space.

You may have to accept that you cannot hibernate. The restart and suspend problem may be related to hardware incompatibility rather than swap space; I don't know, but your computer does seem pretty old. Is it?

If -- and only if -- you have enough spare space on your Kubuntu partition, then you can boot off the Live CD, and run GParted to shrink the Kubuntu partition and expand the swap partition. But bearing in mind your restricted space, I wouldn't make the swap any larger than your RAM, i.e. 1Gb. *Note that although this is a low-risk operation, there is some risk, so you would be well advised to do a full backup first. If you have an external hard drive, I recommend [CloneZilla]("http://clonezilla.org/") for a full disk backup.*

To find out how much space you've used and how much is available on your Kubuntu partition, enter this command.
```
df -h /
```There are some things that you can do to reduce the space already used on Kubuntu. Use these two commands (they get rid of obsolete dependencies and redundant package archives).
```
sudo apt-get autoremove
sudo apt-get clean
```Then try [FONT=Courier New][COLOR=Navy]df -h /[/COLOR][/FONT] again.

In your case, I'd be tempted to save up for a new or reconditioned computer.

---

### Post by John Phang on 2010-03-10
Paddy Landau,
when i enter the code you give me (sudo apt-get autoremove) it come out something like this :

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntuone-client-gnome: Depends: ubuntuone-client (= 1.1.1+r321-0ubuntu1~ppa1~jaunty) but 1.1.2+r407-0ubuntu2~ppa1~jaunty is installed
E: Unmet dependencies. Try using -f.

then i enter (apt-get -f install) it come out something like this:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

actually i do i need to install (apt-get -f install) ?

---

### Post by Paddy Landau on 2010-03-10
> **John Phang said:**
> The following packages have unmet dependencies:
I'm not much of an expert on unmet dependencies. Do the following to find whether it fixes it:

[LIST=1]
[*]System > Administration > Synaptic Package Manager
[*]Press "Reload"
[*]Edit > Fix Broken Packages
[*]Press "Apply"
[*]Press "Reload" (again)
[*]Press "Mark All Upgrades"
[*]If available, press "Apply"
[*]Close Synaptic Package Manager
[*]You may need to reboot.
[/LIST]
Then try again with the sudo commands. Tell us what happens.

---

### Post by myoungf1 on 2010-03-10
I am having the same problem with either shutting down or restarting.  I get the restart to go I get a black screen and my monitor goes to sleep then a system beep and nothing.  Only when I do a ctrl + alt + del do I get a restart.  I only started to have this problem when I installed a new Nvidia GEforce 9800 GT 1024 Mb video card.  I have checked all that has been previously been posted and all is in order but still have the problem.

---

### Post by John Phang on 2010-03-11
Paddy Landau,
After i use the step you gave me, and i enter the code again it come out something like this:

Reading package lists... Done          
Building dependency tree               
Reading state information... Done      
The following packages will be REMOVED:
  compiz-wrapper libaudclient2 libdecoration0 libmcs1 libmowgli1
  libnautilus-extension1 libnotify1 libprotobuf3 libsexy2 libwnck-common
  libwnck22 libxres1 linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic
  mesa-utils notification-daemon protobuf-compiler python-configglue        
  python-gnomekeyring python-notify python-openssl python-pam python-protobuf
  python-pyinotify python-serial python-twisted-bin python-twisted-core      
  python-twisted-names python-twisted-web python-ubuntuone-client            
  python-ubuntuone-storageprotocol ubuntuone-client                          
0 upgraded, 0 newly installed, 32 to remove and 0 not upgraded.              
After this operation, 99.6MB disk space will be freed.                       
Do you want to continue [Y/n]? Y                                             
(Reading database ... 130370 files and directories currently installed.)     
Removing compiz-wrapper ...                                                  
Removing libaudclient2 ...                                                   
Removing libdecoration0 ...                                                  
Removing libmcs1 ...                                                         
Removing libmowgli1 ...                                                      
Removing libnautilus-extension1 ...
Removing ubuntuone-client ...
Removing python-ubuntuone-client ...
Removing python-notify ...
Removing notification-daemon ...
Removing libnotify1 ...
Removing protobuf-compiler ...
Removing libprotobuf3 ...
Removing libsexy2 ...
Removing libwnck22 ...
Removing libwnck-common ...
Removing libxres1 ...
Removing linux-headers-2.6.31-19-generic ...
Removing linux-headers-2.6.31-19 ...
Removing mesa-utils ...
Removing python-configglue ...
Removing python-gnomekeyring ...
Removing python-ubuntuone-storageprotocol ...
Removing python-openssl ...
Removing python-pam ...
Removing python-protobuf ...
Removing python-pyinotify ...
Removing python-serial ...
Removing python-twisted-web ...
Removing python-twisted-names ...
Removing python-twisted-core ...
Removing python-twisted-bin ...
dpkg: warning: while removing python-twisted-bin, directory '/usr/lib/python2.6/dist-packages/twisted' not empty so not removed.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
Processing triggers for hicolor-icon-theme ...

Then i enter (sudo apt-get clean) it doesn't come out anything

sudo apt-get clean
john@Toshiba:~$

---

### Post by Paddy Landau on 2010-03-11
> **John Phang said:**
> After i use the step you gave me, and i enter the code again it come out something like this ...
Good, it looks OK now.

Enter
```
df -h /
```and post the results. That will tell us how much space you have available.

---

### Post by John Phang on 2010-03-12
Paddy Landau,
I have enter the code 
df -h /then it shows:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.7G  3.9G  578M  88% /

---

### Post by Paddy Landau on 2010-03-12
> **John Phang said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.7G  3.9G  578M  88% /
OK, this shows that your Ubuntu partition is nearly full; you have a mere 578Mb free.

John, I think that you're going to have to accept that your computer cannot restart, suspend or hibernate with Ubuntu, simple as that.

You have a few choices that I see:

[LIST=1]
[*]Get rid of Windows. Of course, that can apply only if you no longer use Windows!
[*]Upgrade the hard disk in your computer. That's probably not going to be cost-effective.
[*]Get an external hard drive, and install Ubuntu there instead. Bearing in mind the age of your computer, that may make Ubuntu much too slow.
[*]Install Ubuntu onto a 4Gb USB disk and boot from there; use your hard drive for swap and /home. Again, that will probably slow down your Ubuntu too much -- and it may be quite fiddly to get it working at first.
[*]Save up to buy a new or reconditioned computer. You could use your old computer for Windows and your new for Ubuntu; or your old for Ubuntu and your new for Windows; or get rid of your old and use your new for both Windows and Ubuntu.
[*]Just live with what you have.
[/LIST]
Unfortunately, points 1-4 do not guarantee that your computer will be able to suspend, restart or hibernate, because we haven't managed to rule out a hardware problem!

Point 5 is probably your best bet.

Sorry to be the bearer of bad news, John, but I think that your computer is just too old to run both Windows and Ubuntu. It would need to be one or the other.

---

### Post by John Phang on 2010-03-13
Paddy Landau,
Thank You very much, and i'm so sorry for wasting your time, I'll try to format my laptop (if i got some free time).
Anyway, Thank You very much :)

Cheers,
       John

---

### Post by Paddy Landau on 2010-03-13
> **John Phang said:**
> Thank You very much, and i'm so sorry for wasting your time, I'll try to format my laptop (if i got some free time).
It's not a waste of time. We all try to help each other, as I'm sure you will do one day when you get better at Ubuntu.

You realise that formatting your hard drive will remove your Windows and all your data? Please remember to make a full backup, first!

---

### Post by John Phang on 2010-03-14
Paddy Landau,
Ok, thanks for your advise. :)

---

### Post by unknowndude on 2010-03-14
disable your networking and then try to hibernate,restart etc etc.that should work.......

---

### Post by unknowndude on 2010-03-14
disable networking and then try to hibernate,restart etc.tell me if it doesn't work.

---

### Post by John Phang on 2010-03-19
unknowndude,
I have tried, but it still can't restart,suspend and hibernate...

---

