---
title: "Another noob question regarding installs, partitions, and uninstalls."
date: 2009-06-27
forum: New to Ubuntu
---

### Post by wanderin on 2009-06-27
Hello everybody and thank you for taking time to view this.  Recently I received a free computer and wanted to partition the hd so I can run xp pro and kubuntu 9.04.  I was running the install for Kubuntu, and was proceeding through the install where I got to the point where I was asked about partitioning the hard drive.  I chose to automatically partition the hd 50/50 (I am sorry I do not have a screenshot to provide).  The partition was progressing quite slowly, and then it finished with no progress information showing.  The screen proceeded with the next prompts (username, time zone, etc).  Kubuntu now seems to be installed, however I do not see the hard drive partitioned.  When I go into xp I do not see it either.  Kubuntu will occaisionally pop a window up with information regarding my memory being low, and whether or not I would like to prceed with removing files.

Can I repartition the hard drive in kubuntu?  Can I uninstall kubuntu and start over again?  If so, then How?  :confused:

Thanks again for your time.

---

### Post by synapsys on 2009-06-27
Open up a terminal in kubuntu and post the output of:

```
sudo fdisk -l
```

---

### Post by freebeer on 2009-06-27
It's not surprising that Windows can't see it... Windows is like that.  If it isn't Windows, it doesn't exist.  (at least until you install addition software that allows it to)

Not sure what your issue is, but you should be able to re-install kubuntu onto the existing partition that you created (assuming it was created successfully the first time).

---

### Post by rcayea on 2009-06-27
> **wanderin said:**
> Hello everybody and thank you for taking time to view this.  Recently I received a free computer and wanted to partition the hd so I can run xp pro and kubuntu 9.04.  I was running the install for Kubuntu, and was proceeding through the install where I got to the point where I was asked about partitioning the hard drive.  I chose to automatically partition the hd 50/50 (I am sorry I do not have a screenshot to provide).  The partition was progressing quite slowly, and then it finished with no progress information showing.  The screen proceeded with the next prompts (username, time zone, etc).  Kubuntu now seems to be installed, however I do not see the hard drive partitioned.  When I go into xp I do not see it either.  Kubuntu will occaisionally pop a window up with information regarding my memory being low, and whether or not I would like to prceed with removing files.

Can I repartition the hard drive in kubuntu?  Can I uninstall kubuntu and start over again?  If so, then How?  :confused:

Thanks again for your time.

I believe to uninstall Kubuntu, the only way to do this, is to go back to windows, partition the drive to be completely windows. This way you will start brand new. Then you do the Kubuntu install. 

How big is the hard drive?

---

### Post by Sef on 2009-06-27
> Open up a terminal in kubuntu and post the output of:

 	Code:
 	sudo fdisk -l 


That is not quite correct.  With Kubuntu, the command is this:

```
kdesu fdisk -l
```

Copy and paste that into Konsole and then copy and paste the output.

Sudo is for Ubuntu and Xubuntu.

---

### Post by QIII on 2009-06-27
rcayea is putting you on the right track.

It is MUCH easier to install Ubuntu AFTER Windoze.

(I prefer to do it on separate hard drives so I don't have to worry, but it sounds like you are doing a dual boot on a single physical drive.)

The LiveCD is pretty straight forward, but it certainly wouldn't hurt to search the forums for a tutorial.

Usually when you set up a dual boot, you want to defrag you Windows drive a couple of times.

But with a fresh Windows install, you won't have to worry about that.

---

### Post by wanderin on 2009-06-27
> **synapsys said:**
> Open up a terminal in kubuntu and post the output of:

```
sudo fdisk -l
```

I opened up a terminal, and typed fdisk -1.

it said:

fdisk: invalid option -- '1'

Usage:  fdisk [-b SSZ]  [-u] DISK    Change Partition Table
            fdisk -l [-b SSZ] [-u] DISK  List Partition Table(s)
            fdisk -s PARTITION             Give Partition Size (s) in blocks  
            fdisk -v                              Give fdisk version
Here DISK is somehting like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048:  (for certain MO disks) use 2048byte sectors

Thanks for your time.

---

### Post by synapsys on 2009-06-27
My bad.... the correct syntax is below. (by the way thats an L not a 1)
> **Sef said:**
> That is not quite correct.  With Kubuntu, the command is this:

```
kdesu fdisk -l
```Copy and paste that into Konsole and then copy and paste the output.

Sudo is for Ubuntu and Xubuntu.

---

### Post by wanderin on 2009-06-27
> **rcayea said:**
> I believe to uninstall Kubuntu, the only way to do this, is to go back to windows, partition the drive to be completely windows. This way you will start brand new. Then you do the Kubuntu install. 

How big is the hard drive?  It is 80gb.

I thought about getting another hd and setting it up so one hd will work for kubuntu, and the other for windows.  However, I was confident this will be a smooth transition.  :)

I will look into repartitioning windows and starting the install over as well.  Is there an uninstall feature in kubuntu?

I will be scouring the boards and tutorials as much as I can this weekend.

---

### Post by kixome on 2009-06-27
(warning- you need your windows installdisk to accomplish this)
To go back to windows, use a partition editor to delete the linux partition, and resize the windows partition to take up all the space.(you must do this from a live cd like ubuntu using gparted or a rescue cd.) After doing this boot your computer with the windows disc in the drive and press enter when asked to boot to cd. After the windows disc loads files, select the "repair" (not recovery) console. when asked, choose your installation and then it will ask you to login. after login run these commands back to back:
fixmbr
fixboot

After this windows will be bootable again! Cheers, Also this will completely uninstall kubuntu, as it will be deleted when you delete and resize your partitions (warning: K/Ubuntu is retarded when it comes to having both sata and IDE hard drives in your computer! It always installs the boot loader to the IDE drive by default, and most of the time when you change where to install grub it still doesn't work properly. Love ubuntu, but naming all drive sdx is pretty lame. All devices should be labeld as what type they are I.e SDx for sata, HDx for IDE and SCx should be for scuzzy.

---

### Post by wanderin on 2009-06-27
I pasted the info into Console and it said

fdisk: invalid option -- '1'

***bash: fdisk: : command not found***

Usage:  fdisk [-b SSZ]  [-u] DISK    Change Partition Table

[I]**bash: fdisk: : command not found**

[/I]             fdisk -l [-b SSZ] [-u] DISK  List Partition Table(s)

[I][B]bash: syntax error near unexpected token `('
[/B]
[/I]             fdisk -s PARTITION             Give Partition Size (s) in blocks

 [I][B]bash: syntax error near unexpected token `('

[/B]
[/I]             fdisk -v                              Give fdisk version
Here DISK is somehting like /dev/hdb or /dev/sda
[B]bash: Here: command not found
[/B]
and PARTITION is something like /dev/hda7
The program 'and' is currently not installed.  You can install it by typing sudo apt-get install and 

[B]bash:  and: command not found
[/B]
-u: give Start and End in sector (instead of cylinder) units
[B]bash: syntax error near unexpected token `('
[/B]

-b 2048:  (for certain MO disks) use 2048byte sectors
**bash: syntax error near unexpected token `('**

I type sudo apt-get install and I enter my password

[B][I]The screen saus reading package lists .... Done
Building Dependency Tree ... Done
Reading state information ... Done
E:  Couldn't find package and [/I][/B]

Bold and Italics used to differentiate the fdisk-1 copy and paste from the bash responses.

I hope this helps to help.  Thank You.

---

### Post by wanderin on 2009-06-27
Thanks kixome, sef, synapsys, QIII, rcayea, freebeer for your help.  This is an amazing forum.  I am glad to have found this resource.  May I one day be able to offer advice to noobs like myself.

---

### Post by QIII on 2009-06-27
You may be be typing  -1 (one) rather than small -l (el).


BTW -- Often you will find that it is not the same people who will help you all the way through a problem.  Everyone spends time here when they can, and they leave when they need to.  Don't take it as a snub if someone bows out of a thread for a while.  It's a bit like a bar in here.  You come in, have a few beers, and the wife calls to tell you to come home.

---

