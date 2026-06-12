---
title: "Update manager wont update ???"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-10
I just got a flash update manager in my bottom panel so i clicked it... i got an extensive lists of updates with a total of 111.1 mb... i clicked install and got an error msg that said i didnt have enough ferr space on disc / and that i needed to empty my trash (its empty) and free up 365 mb...

im lost as i have just 1 partition on a 320 gb hdd !!!

is there a fix ???

i hope i explained this good enough to not confuse the issue as i have less than novice pc skills..

thanks for any help...

NOTAGEEK

---

### Post by Majorix on 2009-07-10
Could you please provide us with the output of
```
sudo fdisk -l
```

---

### Post by NOTAGEEK on 2009-07-10
I would be happy to do that and i copied and pasted it to my address bar but that is the wrong place to do that i think... how/where do i run this command from ??? thanks...

---

### Post by Majorix on 2009-07-10
OK memorize this procedure since you will be forwarded to there often.

Click Applications > Accessories > Terminal. Type the command there. It should give you the output, which you can then copy&paste here.

---

### Post by NOTAGEEK on 2009-07-10
> **Majorix said:**
> OK memorize this procedure since you will be forwarded to there often.

Click Applications > Accessories > Terminal. Type the command there. It should give you the output, which you can then copy&paste here.

   THANK YOU !!! I have been trying to figure that one out...   Disk /dev/sda: 320.0 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0xdc0fdc0f     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          13       38588   309848408    7  HPFS/NTFS /dev/sda2           38589       38913     2610562+   5  Extended /dev/sda5           38589       38891     2433816   83  Linux /dev/sda6           38892       38913      176683+  82  Linux swap / Solaris

---

### Post by NOTAGEEK on 2009-07-10
ANY HELP WITH THIS ???

DID I copy/paste the right info ??? i would like to do the updates-----thanks...

---

### Post by LewRockwell on 2009-07-10
> **NOTAGEEK said:**
> ANY HELP WITH THIS ???

DID I copy/paste the right info ??? i would like to do the updates-----thanks...

What's with the CAPS dude? No need to shout out demands to VOLUNTEERS...lest ye find no more willing to assist...

After following each and every one of your threads and posts I have one question.

Have you read this yet([http://www.ubuntupocketguide.com/index_main.html)?](http://www.ubuntupocketguide.com/index_main.html)?)

To wit, Ubuntu has more online and offline documentation, support, and tutorials than most other operating systems, both free and otherwise...which makes it highly suspicious when ANYONE comes to the forums with DEMANDS for free and volunteer assistance...

.

---

### Post by kansasnoob on 2009-07-10
> **NOTAGEEK said:**
> THANK YOU !!! I have been trying to figure that one out...   Disk /dev/sda: 320.0 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0xdc0fdc0f     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          13       38588   309848408    7  HPFS/NTFS /dev/sda2           38589       38913     2610562+   5  Extended /dev/sda5           38589       38891     2433816   83  Linux /dev/sda6           38892       38913      176683+  82  Linux swap / Solaris

That's in a horrible format, should look like this:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xdc0fdc0f 

Device Boot Start End Blocks Id System 
/dev/sda1 * 13 38588 309848408 7 HPFS/NTFS 
/dev/sda2 38589 38913 2610562+ 5 Extended 
/dev/sda5 38589 38891 2433816 83 Linux 
/dev/sda6 38892 38913 176683+ 82 Linux swap / Solaris



Which tells me that you appear to have a dual boot with Windows and sda5 does look small to me.

Please go back to terminal and run:

```
sudo apt-get install gparted
```

That will install Gparted aka: Partition Editor which will appear in System > Administration > Partition Editor.

Now, **I don't want you to make any changes with that!** I just want to see a screenshot of gparted like this:

[ATTACH]120579[/ATTACH]

The screenshot tool is in Accessories > Take Screenshot. You can attach using the paperclip icon at the top of the reply form.

Should resizing be necessary you'll need to use gparted from the Ubuntu Live CD, but let's first of all see what you have.

---

### Post by NOTAGEEK on 2009-07-10
> **LewRockwell said:**
> What's with the CAPS dude? No need to shout out demands to VOLUNTEERS...lest ye find no more willing to assist...

After following each and every one of your threads and posts I have one question.

Have you read this yet([http://www.ubuntupocketguide.com/index_main.html)?]("http://www.ubuntupocketguide.com/index_main.html%29?")

To wit, Ubuntu has more online and offline documentation, support, and tutorials than most other operating systems, both free and otherwise...which makes it highly suspicious when ANYONE comes to the forums with DEMANDS for free and volunteer assistance...

.


YES LEW and thank you for your help now and in the past !!!  i have a vision handicap and have problems with blurrrr...  i try to avoid upper case as much as possible but really have a hard time...  i dont have enough computer experience to understand much in that pocket guide and do better with hard copy reading too as i rhink most people do...

i hace many other physical handicaps also... thank you for being courteous... HAVE A NICE DAY !!

NOTAGEEK

---

### Post by kansasnoob on 2009-07-10
In case I'm away from my desk I'd like to add, where I said:

> Should resizing be necessary you'll need to use gparted from the Ubuntu Live CD, but let's first of all see what you have.


If that Windows OS is Vista (possibly Win 7, I have no experience with it) you are always better off resizing Vista partitions with Vista's own partitioning tools to prevent booting problems!

---

### Post by kansasnoob on 2009-07-10
Hey, we all start somewhere, and I'm legally blind so I can understand!

After a year and a half I still consider myself a nOOb!

---

### Post by NOTAGEEK on 2009-07-10
> **kansasnoob said:**
> That's in a horrible format, should look like this:



Which tells me that you appear to have a dual boot with Windows and sda5 does look small to me.

Please go back to terminal and run:

```
sudo apt-get install gparted
```That will install Gparted aka: Partition Editor which will appear in System > Administration > Partition Editor.

Now, **I don't want you to make any changes with that!** I just want to see a screenshot of gparted like this:

[ATTACH]120579[/ATTACH]

The screenshot tool is in Accessories > Take Screenshot. You can attach using the paperclip icon at the top of the reply form.

Should resizing be necessary you'll need to use gparted from the Ubuntu Live CD, but let's first of all see what you have.

> **kansasnoob said:**
> In case I'm away from my desk I'd like to add, where I said:



If that Windows OS is Vista (possibly Win 7, I have no experience with it) you are always better off resizing Vista partitions with Vista's own partitioning tools to prevent booting problems!



THank you kansasnoob i will go try that and be back asap...

---

### Post by NOTAGEEK on 2009-07-10
> **kansasnoob said:**
> In case I'm away from my desk I'd like to add, where I said:



If that Windows OS is Vista (possibly Win 7, I have no experience with it) you are always better off resizing Vista partitions with Vista's own partitioning tools to prevent booting problems!


KANSASNOOB,

I did what you said and got this----> failed to run/usr/sbin/gparted as user root

then it said----> unable to copy users xauthorization file


I might add my goal was to make 2 partitions and install ubuntu on the second one---what i got was 1 320 gig partition i give up why other than lack of pc know how...

i first tried to install win xp pro and locked the pc up lol... then tried win 7 beta build 7057 with similar results lol lol...

the pc is brand new with no os or documentation and quad core...  i feel lucky to get this far in a couple days...  thanks...

---

### Post by Elfy on 2009-07-10
Possibly it is completely full and thus it can't write the file.

Please open a terminal and run this command - copy and paste the result to a new post here 

```
df -h
```

It is very likely that you will be getting a crash course in resizing linux partitions.

If you do Ctrl + in firefox it will zoom in - you might find that better for your eyes :)

---

### Post by LewRockwell on 2009-07-10
From your previous posts it would seem that none of your installation attempts have gone as planned. Even though your hard drive partitions show the presence of some flavor(s) of windows, none of them work? Is that correct?

And if that is correct then you won't be terribly inconvenienced by the necessary repartitioning.

Gparted may be run from the Ubuntu LiveCD or from other distros and/or utility disks as well.

I'm still suspicious of the 64-bit/32-bit BIOS selectivity that your supplier continues to deny. You would do well to learn and become familiar with your BIOS and may find that one or two simple selection alterations may make all your subsequent installations go quite smoothly.

.

---

### Post by NOTAGEEK on 2009-07-10
> **forestpixie said:**
> Possibly it is completely full and thus it can't write the file.

Please open a terminal and run this command - copy and paste the result to a new post here 

```
df -h
```It is very likely that you will be getting a crash course in resizing linux partitions.

If you do Ctrl + in firefox it will zoom in - you might find that better for your eyes :)



forestpixie----i got this

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  144K  1.5G   1% /dev
tmpfs                 1.5G  444K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sr0              388K  388K     0 100% /media/cdrom0


crash courses are ok...  thanks for that cntrl+ tip it is very helpful...

---

### Post by Elfy on 2009-07-10
You will need to resize :)

Use the windows disk management thing to shrink that partition - leave the new space unallocated and boot the livecd. Then you will need to do a few things there, it looks worse than it is ;)

In order you will need to 

turn off swap - can be done by right clicking the swap partition in gparted - there is an option to turn off swap there

resize the extended partition to include the unallocated space

move sda5 to the left inside the extended partition

resize sda5 to take up the unallocated space

Gparted can take some time to work - especially resizing and moving partitions - _do not assume it has crashed_

---

### Post by NOTAGEEK on 2009-07-10
> **forestpixie said:**
> You will need to resize :)

Use the windows disk management thing to shrink that partition - leave the new space unallocated and boot the livecd. Then you will need to do a few things there, it looks worse than it is ;)

In order you will need to 

turn off swap - can be done by right clicking the swap partition in gparted - there is an option to turn off swap there

resize the extended partition to include the unallocated space

move sda5 to the left inside the extended partition

resize sda5 to take up the unallocated space

Gparted can take some time to work - especially resizing and moving partitions - _do not assume it has crashed_


ok if i need to resize but i have a problem with the 1st paragraph... i keep hearing windows being mentioned...  as far as i know i have no windows installed...  i think i have a 320 gig hdd with just 1 large partition and omly 9,04 installed... 

the rest of your directions are kinda understandable to me...  i think the rest can be done from my 9.04 disc ???





> **LewRockwell said:**
> From your previous posts it would seem that none of your installation attempts have gone as planned. Even though your hard drive partitions show the presence of some flavor(s) of windows, none of them work? Is that correct?

And if that is correct then you won't be terribly inconvenienced by the necessary repartitioning.

Gparted may be run from the Ubuntu LiveCD or from other distros and/or utility disks as well.

I'm still suspicious of the 64-bit/32-bit BIOS selectivity that your supplier continues to deny. You would do well to learn and become familiar with your BIOS and may find that one or two simple selection alterations may make all your subsequent installations go quite smoothly..


yes lew no windows work... perhaps some residue was left from my install arrempts ???

nope---at this p[oint i know more abt 9.04 than i do abt windows lol... i can partitiom away...

gparted from my 9.04 disc---ok...

i would look at my bios but wouldnt know what to look for... thanks...

---

### Post by kansasnoob on 2009-07-10
This:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc0fdc0f

Device Boot Start End Blocks Id System
/dev/sda1 * 13 38588 309848408 7 HPFS/NTFS
/dev/sda2 38589 38913 2610562+ 5 Extended
/dev/sda5 38589 38891 2433816 83 Linux
/dev/sda6 38892 38913 176683+ 82 Linux swap / Solaris

Does show windows is taking up most of the drive. In the disc description:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders

You can see the total "38913 cylinders" and as you read down the list of partitions:  

> Device Boot Start End Blocks Id System
/dev/sda1 * 13 38588 309848408 7 HPFS/NTFS
/dev/sda2 38589 38913 2610562+ 5 Extended
/dev/sda5 38589 38891 2433816 83 Linux
/dev/sda6 38892 38913 176683+ 82 Linux swap / Solaris

You can see the "38913" reflected in the "End" column.

sda1 is formatted as HPFS/NTFS indicating Windows which is using "38588" cylinders, whereas sda2 is an extended partition containing both of the Ubuntu partitions totaling "324" cylinders, or less than 10% of the entire drive.

But if you're wanting to end up with a dual boot of win and Ubuntu you should first figure out why the Windows installations are failing.

This guide:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

may be helpful when you get the Windows thing straightened out.

---

### Post by kansasnoob on 2009-07-10
If you want to just give up on installing Windows it would be easiest to just reinstall Ubuntu being sure to select "use entire disk":

[http://www.psychocats.net/ubuntu/images/installingjaunty09.png](http://www.psychocats.net/ubuntu/images/installingjaunty09.png)

Ignore the difference in "artwork" and just choose to use the whole disk!

---

### Post by kansasnoob on 2009-07-10
> **lewrockwell said:**
> from your previous posts it would seem that none of your installation attempts have gone as planned. Even though your hard drive partitions show the presence of some flavor(s) of windows, none of them work? Is that correct?

And if that is correct then you won't be terribly inconvenienced by the necessary repartitioning.

Gparted may be run from the ubuntu livecd or from other distros and/or utility disks as well.

I'm still suspicious of the 64-bit/32-bit bios selectivity that your supplier continues to deny. You would do well to learn and become familiar with your bios and may find that one or two simple selection alterations may make all your subsequent installations go quite smoothly.

.

+1!

---

### Post by Elfy on 2009-07-10
> ok if i need to resize but i have a problem with the 1st paragraph... i keep hearing windows being mentioned... as far as i know i have no windows installed... i think i have a 320 gig hdd with just 1 large partition and omly 9,04 installed...If you don't have a windows install but just an NTFS partition then it is all the easier - if you want to have space to install one in the future then make sure to keep some for it - it would be better to have the ntfs at the front where it is.

So if you do have only ubuntu installed fire up the livecd open the partiton editor from the sys admin menu and proceed to resize and move your partitions about.

---

### Post by NOTAGEEK on 2009-07-10
> **forestpixie said:**
> If you don't have a windows install but just an NTFS partition then it is all the easier - if you want to have space to install one in the future then make sure to keep some for it - it would be better to have the ntfs at the front where it is.

So if you do have only ubuntu installed fire up the livecd open the partiton editor from the sys admin menu and proceed to resize and move your partitions about.


FORESTPIXIE

sorry abt the delay in my reply i had a dr apointment...

i now have other issues with 9.04 missing back arrows etc...

i think i should just go to ubuntu.com and re-install the os in 64 bit as my disc is 32 bit... my quad core maybe should earn it;s keep ???

with some direction i think i can also re-install so 9.04 goes in on the second half of a hdd with 2 partitions...  that way in the future i can put windows in easier should i decide to do that...

is this a good idea/option ???  if so i will need help with the partition part and i think the rest should be pretty much automatic... thanks...

NOTAGEEK

---

### Post by Elfy on 2009-07-10
I think that it might be wise here to do that - it is likely that reinstalling will be quicker - if you have no windows then use the whole disk to install on as kansasnoob suggests.

Not sure what link he was tryingto give you - this one should help you out [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by NOTAGEEK on 2009-07-10
FP.

It must be early am where you are... much has happened arounf here...  

[http://ubuntuforums.org/showthread.php?t=1209972](http://ubuntuforums.org/showthread.php?t=1209972)

i have to rake my meds and callit a day here as its getting pretty late......

thanks so much for all your help...  i will carch up to you in a few hours...

---

### Post by Elfy on 2009-07-11
It is in fact stupid o'clock here.

Until you resize the partition you will keep getting odd things happen :) didn't read the whole of that thread to see if you have - if not then I suggest you deal with that next. It will likely make the whole experience a lot more enjoyable for you :)

---

### Post by NOTAGEEK on 2009-07-11
> **forestpixie said:**
> It is in fact stupid o'clock here.

Until you resize the partition you will keep getting odd things happen :) didn't read the whole of that thread to see if you have - if not then I suggest you deal with that next. It will likely make the whole experience a lot more enjoyable for you :)


yes my friend i am getting to the point where i likely will be ready to take that on next... 

yikes !!!

---

