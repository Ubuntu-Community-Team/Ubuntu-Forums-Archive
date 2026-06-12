---
title: "Trying to rescue a computer with Ubuntu!"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Arleas on 2009-04-18
Hi there,

My partner's laptop recently BSOD'd and we can no longer get into Windows. Windows can't repair the installation (same BSOD error) so I booted up the 9.04 ubuntu LiveCD. It mounts the Windows partition and we can get all her stuff off the drive. Excellent!

We decided to install Ubuntu - it was quick and seems reliable, but for some reason it won't partition the Windows installation to allow Ubuntu on. The guided partition option is missing, and manual only allows me to delete the Windows partition. The only option is to erase the Windows partition - and all her stuff.

I've read this is because the Windows partition needs defragging. Unfortunately, we can't boot into Windows to defrag it...

Is the only option to back up the files to an external hard disk, and then format the HD?

Hope someone can help!

Edit: I forgot to mention that Ubuntu sees two Windows partitions - one small 5gb one labelled as Windows 2000/XP and then the larger 55gb Windows XP Media Center Edition (60gb hard disk). Cheers!

---

### Post by AlecJ on 2009-04-18
You could download and make the cd of Gparted 
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
This should allow you too resize the fat partition.
But if windows is broken and you have the data, why bother?

---

### Post by JK3mp on 2009-04-18
I find it odd that manual install only lets you erase the windows partition. I would probably just back everything in her users folder on windows into an external HDD or Flash drive etc. Then Just go through with the install. Only thing she won't have is any programs. All her files pictures music and the usual important documents will have been saved at least. There might be a program you can install or use through the live boot to defrag it, i've heard of it but can''t recall what its calld, if i find it or remember it i'll let you know, google around.

---

### Post by Tobine on 2009-04-18
If you can find out what's causing the problem you might be able to fix it with Ubuntu. When my brothers windows pc was effed we went in and replaced the corrupted file using an Ubuntu liveCD.

Boot into windows and google whatever the error message says and you might find the root of the problem. Best of luck!

---

### Post by Arleas on 2009-04-19
I transferred all her files onto an external hard disk and then used the Ubuntu installer to format and install itself. It went on with no problems. Thanks for the help!

Some notes:

I found that Gparted can be ran straight from the LiveCD, but it flagged up an error with the Windows partition. Unfortunately, there's no defragger on the LiveCD.

Ubuntu actually spots previous Windows XP users, and offers to transfer over all their personal files. I clicked 'yes', but it didn't actually do it. I've no idea how it would do it (after formatting the hard disk), but I guess its a feature to be added later.

Now all I need to do is find out where the MAC address is...

---

### Post by starcannon on 2009-04-19
To find the mac address of the network interface:


[LIST=1]
[*]R-click on nm-applet, its in the upper right corner of your desktop and looks like this:[IMG]http://img514.imageshack.us/img514/2758/nmappleticon.png[/IMG]or it will be some Blue Bars.
[*]Click on "Connection Information"
[*]The last listing "Hardware Address" will tell you your MAC.
[/LIST]
GL and have fun.

---

### Post by lisati on 2009-04-19
> **Arleas said:**
> 

Edit: I forgot to mention that Ubuntu sees two Windows partitions - one small 5gb one labelled as Windows 2000/XP and then the larger 55gb Windows XP Media Center Edition (60gb hard disk). Cheers!

The smaller partition is likely to be a Windows recovery partition. I'm wondering if that can be used as part of the troubleshooting process.

BTW: some machines have trouble with Windows XP SP3. I had to run a patch from my desktop's manufacturer BEFORE installing SP3. Not realizing this caused a major headache for me......

---

### Post by ugm6hr on 2009-04-19
This might be a hardware problem.

Run a HD diagnostic first.

If the Windows partition showed BSOD, you may be better off reinstalling after the HD check.

---

### Post by Arleas on 2009-04-20
> **starcannon said:**
> To find the mac address of the network interface:


[LIST=1]
[*]R-click on nm-applet, its in the upper right corner of your desktop and looks like this:[IMG]http://img514.imageshack.us/img514/2758/nmappleticon.png[/IMG]or it will be some Blue Bars.
[*]Click on "Connection Information"
[*]The last listing "Hardware Address" will tell you your MAC.
[/LIST]
GL and have fun.

Thanks for the help!

Unfortunately, 'connection information' is greyed out. This is bringing back rather confusing memories about the way Ubuntu handles administrators. There's only one user for the computer, but that user cannot access all the functions.

It doesn't make sense to me - anyone know how to transform the only user of the computer into an administrator?

Thanks again :)

---

### Post by ugm6hr on 2009-04-20
> **Arleas said:**
> Unfortunately, 'connection information' is greyed out. This is bringing back rather confusing memories about the way Ubuntu handles administrators. There's only one user for the computer, but that user cannot access all the functions.

It doesn't make sense to me - anyone know how to transform the only user of the computer into an administrator?

You can get a MAC address from Terminal with *ifconfig*

The user will have "sudo" rights if you need to use them.

Not really sure how the MAC address will help you with this problem...

---

### Post by Arleas on 2009-04-20
> **ugm6hr said:**
> You can get a MAC address from Terminal with *ifconfig*

The user will have "sudo" rights if you need to use them.

Not really sure how the MAC address will help you with this problem...

Thanks for that - I'll give it a try. I need the MAC address to connect to the wireless router.

The laptop is fine - there's no hardware fault. I mentioned earlier (i think?) that it was a corrupt registry problem under windows. There was (unbelievably) no fix for my situation, so formatting was the only way to go.

Is there any way to make the user a permanent admin, so that I can always access all the functions? Seems strange that you need to open the terminal up and type in code just to be able to look up a MAC address - it's like look but don't touch! :)

---

### Post by Ticketoride on 2009-04-20
> **Arleas said:**
> it won't partition the Windows installation to allow Ubuntu on. The guided partition option is missing, and manual only allows me to delete the Windows partition. The only option is to erase the Windows partition - and all her stuff.
What appears to separate Windows Partitioners from Linux' GParted, is that Partition Magic will move your Data corresponding to your Actions without deleting any of it.

Search Google for "Hiren's Boot CD 9.8" ... download, burn and then use any of the Partitioning Tools on Disk. They'll partition without deleting anything.

I always set up Linux Partitions through Windows first to register the Actions. Partition Magic will create Linux Ext2/3 & Swap and Windows will see them as valid Partitions. If you create Partitions via Linux, Windows may see it as a "Bad Partition Table Error". I even have WinXP fully registering Ext4 as a valid %BootDrive and won't mess with it after. Many of these Grub Errors are the direct Result of not first letting Windows see what has been done with the Drive first before installing Linux if you run Dual OSs.

I'll give you an example ...

You create 3 Linux Partitions on your 2nd. physical HDD, then Partition #4 an NTFS Volume as a logical Drive. Yet when you boot back into Windows the NTFS Partition is seen as a Primary Partition after GParted had created them under Linux and that Drive pulls up right under the C:\ Drive. Windows then comes along and recommends you fix a Disk Error, and after your Linux won't boot up anymore.

Had the 3 Linux Partitions been created in Windows, the NTFS Volume would have been properly recognized as a logical Drive and not yanked up under the C:\ 

Even worse for the unsuspecting Windows User ... he re-sets this NTFS Partition Order back to the Bottom of the Windows Drive Chain screwing up the Linux Partition even further. Next Thing, even if the Grub Bootloader is edited properly, he still can't boot up into Ubuntu.

Anyone running Windows alongside Linux on their Computer, exercise extreme Caution using Linux Partitioners.

---

### Post by ugm6hr on 2009-04-20
> **Arleas said:**
> Thanks for that - I'll give it a try. I need the MAC address to connect to the wireless router.

The laptop is fine - there's no hardware fault. I mentioned earlier (i think?) that it was a corrupt registry problem under windows. There was (unbelievably) no fix for my situation, so formatting was the only way to go.

Is there any way to make the user a permanent admin, so that I can always access all the functions? Seems strange that you need to open the terminal up and type in code just to be able to look up a MAC address - it's like look but don't touch! :)

If the laptop was previously connected to the wifi router during its Windows life, the MAC will be the same, so MAC filtering etc will not need to be changed.  The MAC is a hardware address (unless you deliberately try to change it).

Formatting does seem the way to go... An Ubuntu partition will ensure you have a usable computer if 1 OS goes down in the future (I have done this for my mum, to ensure she survives between my visits to fix the problems she encounters with Windows).

As for the permanent admin stuff... See the scattered details about the "root user" and "sudo" on Ubuntu.  While it is possible to enable the root user, it is not recommended for security reasons.  However, I suspect the reason that box is greyed is because it is not currently connected: "Connection Information" is predominantly to give details about your network connection, not MAC address. Hence: no connection, no information.  Sudo etc has nothing to do with this.

---

### Post by egalvan on 2009-04-20
> **Arleas said:**
> I need the MAC address to connect to the **wireless router**.

Since this is a laptop, there is a good chance the MAC WiFi info is on a sticker on the bottom of the machine...

> it was a corrupt registry problem under windows.
 There was (unbelievably) no fix for my situation,
 so formatting was the only way to go.

Yes, Windows is known to need "wipe-and-install" on a regular basis.

> 
Is there any way to **make the user a permanent admin**, so that I can always access all the functions?

In Ubuntu, this is frowned upon... it is considered a security risk.
In these forums, it is against the rules to discuss how to circumvent this... kind of  "if you need to ask how to use this dangerous tool, then you don't have the experience needed to use it"

Using sudo or gksudo is all you need for 99% of what you will be doing in Ubuntu.

Note that some distros have, and boot into, a ROOT account.
Not Ubuntu.

>  Seems strange that you need to open the terminal up and type in code just to be able to look up a MAC address - 
it's like look but don't touch! :)

Some things work differently in Linux than in Windows.
Normally, right-clicking on the network icon will show that info...
this works on all five of my Ubuntu machines,
yes I just checked.

You say that on your laptop that option is greyed out...
probably because the wifi card is not turned on;
either missing drivers, not configured, or there is a switch on the laptop that is "off".

So under Linux you have an alternative way to get the info you need.
[I]open terminal
type "ifconfig"
read info[/I]


And MAC address are normally set, and not changeable. So no need to "touch", only "look" :)

---

### Post by egalvan on 2009-04-20
> **Ticketoride said:**
> Many of these Grub Errors are the direct Result of not first letting Windows see what has been done with the Drive first before installing Linux if you run Dual OSs.

Well, I've been dual-booting WinXP & Ubuntu since 8.04.
On at least fifteen different machines.

On ALL OF THEM I used PartedMagic to partition the drives.
Gparted. Under Linux.
The drives are visible on ALL OF THEM, no GRUB errors.

Besides, what does GRUB have to do with Windows?
Other than chain-load it? :)

---

### Post by Ticketoride on 2009-04-21
> **egalvan said:**
> Well, I've been dual-booting WinXP & Ubuntu since 8.04.
On at least fifteen different machines.

On ALL OF THEM I used PartedMagic to partition the drives.
Gparted. Under Linux.
The drives are visible on ALL OF THEM, no GRUB errors.
Then your Experiences vastly differ from mine, as all FAT32/NTFS Drives which come after the Linux Partition were not recognized, but simply marked as "Bad". But setting them up as I stated above, avoids those Complications.

This has happened to me and other Machines on more than 1 Occasion, now I just play it by the Book, no further Problems.

> **egalvan said:**
> Besides, what does GRUB have to do with Windows?
Other than chain-load it? :)
Partition Table Changes in Windows have routinely caused Ubuntu Boot up Problems, such as deleting, merging, adding a Partition as well as File System Changes. It can change the Partition Order. There are Tons of FAQs throughout this Forum on this.

---

