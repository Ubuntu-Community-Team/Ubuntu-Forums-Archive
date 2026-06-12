---
title: "Choices for Manual Install"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by jezebel on 2009-01-29
Yay - I'm nearly there!

I want to install Ubuntu 8.1, and have gotten part way there. 

I have to choose the 'manual' option for installing due to my complicated partitions.

So, qu4estion: When doing using Ubuntu disk and creating a partition, I have choices that I don't understand.

For 'Use As' - do I choose the default 'EXT3 journaling file system', or EXT2, or FAT32...or what?? I'm baffled here.

For the mount point, what should I select? /, /home, /boot, etc...???

Please, any pointers would be appreciated. I don't want to mess this up:-)

---

### Post by Elfy on 2009-01-29
ext3 is the default - you could use other's - just not windows types

/ for the moutpoint, I assume that you just have the one partition for the install.

---

### Post by jezebel on 2009-01-29
Thank you, forestpixie -

that was the info I needed. 

I entered those options, but now I have a window that says, 

No mount point is assigned for ntfs file system in partition #3 of SCSi1 (0,0,0) (sda).

If you do not go back to the partioning menu and assign a mount point for there, this partition will not be used at all

MY setup = I have a 1tb disk, partitioned 100 gigs for Vista, 250 photos, 250 for Docs; and 40 gigs mistakenly partitioned in Vista with nothing (intended for ubuntu).

With Ubuntu, I didn't touch that ntfs partition, I did slice away 40 gigs from the other 360 gigs, unformatted.

So that's where I'm at...

---

### Post by Elfy on 2009-01-29
Ok - not exactly sure what the system thinks you want to do there - you haven't edited any of the win partitions in anyway - ie - maybe telling it to be used as ntfs for instance

You don't need to tell the system anything about the ntfs drives - just completely ignore them. You can deal with access to them later, if that was what you were trying to achieve

If you're not sure then I would exit the install and start again - if you start doing anything to the existing ntfs you could end up with nothing on them

---

### Post by jezebel on 2009-01-29
Ergh..

I chose to go ahead and have whatever that ntfs partition was just be ignored. But then I was prompted about the swap partition. I hadn't made one, so I could either go back and fix the prob, or continue..

I went back, tried to make a smaller swap partition, but there was an error in resizing....

I'm two bottles of red wine down, and sleepy - I'll work on this more tomorrow, but please, forestpixie (or others), what do you think?

J.

---

### Post by Elfy on 2009-01-29
I think a clear head tomorrow will help, you'll need to have a swap 
> 
I have to choose the 'manual' option for installing due to my complicated partitions.
Perhaps post the result of running this from a terminal

```
sudo fdisk -l
```

---

### Post by jezebel on 2009-01-29
Okay - so to get to the terminal before I've installed Ubuntu - would I be able to access the terminal and install when running live disc? (This is a clean install).

Also, I have to be in safe graphics mode, since my card is, apparently, not palatable to Ubuntu:-)

J.

---

### Post by hyper_ch on 2009-01-29
there are a few requirements:

(1) you need at least one partition that is mounted as "/" and it will require a linux filesystem that supports default linux permissions and ownerships (normally you will select ext3 for that)

---

(2) you may also want to use SWAP - this provides virtual ram. It requires no mountpoint but as "filesystem" you select swap

(3) you might want to also make a seperate /home partition. Again you'll require a linux filesystem for that. Some people think it makes it easier to re-setup a computer, I don't think so and tht's why I don't use it

as for the rest, well, you're pretty much free to do what you want.

So question now is: What do you want to achieve, what do your partitions look like etc.

---

### Post by Elfy on 2009-01-29
> would I be able to access the terminal and install when running live discYes - you can do almost anything on the livecd

---

### Post by jezebel on 2009-01-29
Hyper_ch 

Your info was helpful - I see that I need a swap. 

Okay.

What I want to achieve - a dual boot system, Vista installed first, Ubuntu second ('cause Vista's already there!).

Partitions:
1TB like this:
100 gb = Vista (ntfs)
250 gb= Photos (ntfs)
250 gb=Documents (ntfs)
40 gb=empty (ntfs)
360=non used or formatted

With ubuntu install disk, I tried to take 40 GB (from the 360 gigs)to install the system on; that's when I got confused by all the options.

Also, how should I make a swap part?

Should I do that first or second??

I don't think I need a separate /home; I'm not worried about changed pcs, etc...

J.

---

### Post by hyper_ch on 2009-01-29
problem is, you can only have 4 primary partitions. So you'll need to create an extended partition and inside there you can create more logical ones.

---

### Post by Elfy on 2009-01-29
please post the fdisk -l otherwise we can only guess :)

---

### Post by jezebel on 2009-01-29
Ah..

Okay. First, how and where do I create an extended partition?

And forestpixie - I'll do that, and post it; it will have to wait about 6 hours though 'cause yer right, I'll need a clear head. I just seem to think I know what I'm doing better after a wine and cheese party!

Okay - I'll do that tomorrow (it's 10 pm here now).

Thanks.

---

### Post by jezebel on 2009-01-29
Here's the fdisk -l results:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbbdeb64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13056   104872288+   7  HPFS/NTFS
/dev/sda2           13057       78327   524289307+   5  Extended
/dev/sda5           13057       45691   262140606    7  HPFS/NTFS
/dev/sda6           45692       78327   262148638+   7  HPFS/NTFS

Not sure what it means myself...;)

---

### Post by Elfy on 2009-01-30
You need to make sure that your "40 gigs mistakenly partitioned in Vista with nothing" is available inside  the extended partition (sda2 - no idea what vista might call it)

then make 2 new partitions inside the extended partitions - sda7 and sda8, one as swap and one as the install partition

---

### Post by jezebel on 2009-01-30
Forestpixie -

Thanks for keeping up with my thread.

Now, would you mind talking to me like I'm a moron ('cause I am!) - 
How do I make sure the 40 gigs are available inside an extended partition?

To make the other two partitions, how exactly do I do that? When I've tried partitioning during the Ubuntu install, I get a message saying unable to resize the partition...

I've also somehow 'lost' 40 gb, when messing around in windows and deleting a partion...blah blah blah

---

### Post by Elfy on 2009-01-30
Ok - this is going to sound more complicated than it is and if you get lost have another read :)

If you really can't get it then post a screenshot of the gparted window - open partition editor from the system admin menu - screenshot tool is in applications accessories menu

To be able to resize the extended partition ( or indeed any partition) the empty/unallocated space has to be contiguous to the partition you wish to resize - that is next to it

For example

partition 1 | partition 2 | empty space | partition 3

to resize partition 1 it needs to look like

partition 1 | empty space | partition 2 | partition 3

The way to do that is to move partitions before you can resize

FYI you might be interested in [https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events/02012009](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events/02012009) it's on IRC - there's a bit on IRC [here]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Resources") - it's going to cover what you are trying to do

---

### Post by bill1971 on 2009-01-31
I've been following this thread, because I'm in somewhat the same boat that Jezebel is in (minus the wine and cheese - lol).

I've built and /or repaired/upgraded many Windows PCs over the past 12 years or so, but using Windows somehow "dumbs us all down," IMHO, as far as understanding programs and languages - which I guess was Microsoft's intention all along. 

I have avoided Vista like the plaque, but did recently dwnld and install Windows 7 beta, just to get a feel for it, on a dedicated PC build. I did create an unformatted 180 GB Primary partition to install Xubuntu, while partitioning the hard drive for the Windows 7 install, so I don't have to move anything. but I was as stumped just as J-bel was when it came to installing Xubuntu.

I'll continue to follow this thread, and at the risk of thread-crapping, may I ask this question: Using Gparted from the Live CD to manually set up the partition(s) for the Xubuntu install, do I have to delete that 180 GB partition and start over, in order to use the "New Partition" button or tab? Should I start a new thread? Once again, sorry for the intrusion, and many thanks for your help.

Oh, and looking at J-bel's screenshot. why are there two swap partitions? and, how large should the swap partiton be? Is 3 GB a typical size? Thanks again.

- Bill

---

### Post by Elfy on 2009-02-01
> ...do I have to delete that 180 GB partition and start over...If the 180Gb partition doesn't have anything of importnace on it then it would be quicker to delete and start again. If it's not formatted yet then just make your partitions.

> Oh, and looking at J-bel's screenshot. why are there two swap partitions? and, how large should the swap partiton be? Is 3 GB a typical size?Where is the screenshot? - I can't see it.

You only need one - and how big depends -
if you hibernate then swap should be equal to or greater than RAM
if not then if you have more than 1GbRAM I wouldn't have a swap much bigger than 512Mb, less than 1Gb RAM and swap = 1.5 or 2x RAM

But if you have more than 4Gb and 32 bit then default ubuntu would not see more than about 3.8Gb or so

---

### Post by jezebel on 2009-02-08
Forestpixie - again, thank you so much!

I am up and running with a clean install of Ubuntu (Vista dual boot).

Your comment about needing to have the empty space be contiguous triggered something in my brain. 

So, here's how I got the manual install to work, without affecting my other (Windows) partitions.

My Setup (if you remember) was 1TB hdd (100 gb = Vista, 250 - Documents, 250 - Photos (all ntfs windows), the rest was empty and unallocated).

After messing around before and during these posts, I finally did end up with a 40gb partition that I created in Vista. That left roughly 350 gb unallocated.

From the Ubuntu disk, during install, I still chose manual, then, in a stroke of genius, I highlighted the 350 gb, chose to create a partition, and made that little partition my swap file. THEN, I went to the 40gb partition (pre-created in windows), chose to set it to ext3, format, mount point / ...

That did it. I didn't get any errors about not having a swap drive or anything. It went fine! (Previously, I'd been trying to partition the 40gb to create a swap, and that wouldn't work).

Okay, hope this is clear for anyone looking for answers to the same issue.

Again, thanks for all the help and for keeping up with the thread.

---

