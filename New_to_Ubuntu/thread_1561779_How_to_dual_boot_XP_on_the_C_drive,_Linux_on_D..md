---
title: "How to dual boot: XP on the C drive, Linux on D."
date: 2010-08-26
forum: New to Ubuntu
---

### Post by DanTheBib on 2010-08-26
Hey guys,

I had Ubuntu Karmic installed a while ago on my C drive, but because of windows xp eating up a lot of data it was slow and I got rid of it.

I've been reading lots of good stuff about 10.0.4 so decided to install it. I have it on a Boot-from-USB stick thing atm. I'm actually using it now :) 

However, when it comes to the full install, I'm a bit stumped.

I want to use my D drive (my C and D drive I believe are actually the same physical hdd, just been partitioned). I do not have a clue what to select when deciding where to install it. I don't want to wipe my HDD, but am unsure whether to select the option of basically "select own partition space" or the first option of boot with xp.

I'm worried because I seem to have 3 OS's installed. "Vista Boot loader" (what O_o), "XP", and then a random other bit. Sorry I can't be more specific.

Thanks for any responses guys,

- Dan

---

### Post by 29732 on 2010-08-26
hey
assuming you are new to ubuntu and this erm... "process", all i can say to this is:
1. windows cannot see ubuntu partition but ubuntu can see windows
2. it doesnt matter what the label of partition you make, the one you want to install on you have to erase to install on the free space (NTFS for windows, ext4 and swap for ubuntu, ubuntu will make the partition by itself)
it is based on my knowledge and anyone smarter than me can help you better but that is the way ill do it
good luck ^_^

---

### Post by 29732 on 2010-08-26
oh and adding to it, 
there will be this thing called "GRUB" which will be your default boot loader, if it messes up, maybe you can reinstall ubuntu

and there is a thing called BURG which is what i use, it basically is the same, just more pretty :P

---

### Post by DanTheBib on 2010-08-26
Thanks, I suppose I wasn't very clear. I'm not entirely sure where to install Ubuntu, and whether to just let it do it by itself (which is the first installation option) or to do the third thing and partition everything myself. 

The thing is I can't fit Ubuntu on my C drive, hence wanting to get to the D

---

### Post by 29732 on 2010-08-26
try erasing D drive, and then ubuntu will give you an extra option saying to install it on the free space\
ASSUMING THAT THERE IS NOTHING ON THAT DRIVE

---

### Post by wilee-nilee on 2010-08-26
Since you already understand that c drive and d drive are partitions and probably on the same HD lets refer to partitions. It is very vague in terms of what your doing to use the letters then actual partition information.

Post a screen shot of gparted from your live Ubuntu or a snip of the disc manger in windows.

---

### Post by DanTheBib on 2010-08-26
Well my D drive has 4 folders on it, which I have not placed there.

They are:

msdownld.tmp which contains nothing.

ede42548ca3aafd5922f5d15188a which contains folders called amd64 and i386. There are some .dll files within each of those folders, which makes me wary of deleting them. 

System volume information which contains a RESTORE folder, tracking.log file and Mount Point Manager Remote Database.

Also, there is RECYCLER which contains two folders. In each of these folders is desktop.ini and info2

Sorry for the long post again, I just don't want to risk deleting anything critical >_< Could I just copy that to the C drive?

EDIT: Sorry for being dumb, but what is gparted?

---

### Post by 29732 on 2010-08-26
you will have to leave that to the experts (in my opinion, i am thinking that all those files were created automatically with that partition)

---

### Post by DanTheBib on 2010-08-26
Found Gparted, sorry.

Here is what I get:

[http://i59.photobucket.com/albums/g316/Goku2212/Gparted.png](http://i59.photobucket.com/albums/g316/Goku2212/Gparted.png)

---

### Post by 29732 on 2010-08-26
i am thinking /dev/sda3 is the "D"  drive
hmmm
it uses up about 97.85MBs 
so,
 when you made that partition, did you move some stuff to it? because otherwise i think it should be safe to erase it..

---

### Post by 29732 on 2010-08-26
but to erase it you need to unmount it (right click on it and click unmount) then you just right click on that partition and click erase and then you click on that green checkmark (i suggest backing up your stuff before doing that)

---

### Post by DanTheBib on 2010-08-26
I didn't actually make the partition, it was on the pc when I got it, hence me being so reluctant to touch it. I think it would be fine, but I'm not sure...

---

### Post by 29732 on 2010-08-26
yeah, im not sure either 
i sec, imma format my flash drive as ntfs and then see what it has, brb

---

### Post by 29732 on 2010-08-26
mmk, it just shows me that system volume info folder
iiiiiiii think you should wait until an expert can tell you if its safe 
you can risk it, but you should back up what it has

---

### Post by 29732 on 2010-08-26
because if it screws up your pc, you can remake that "D:\" partition and then put all the files back

---

### Post by 29732 on 2010-08-26
and hey, if i dont reply within 1 hour, that means i have to go for about 24 hours
you'll have to rely on someone else

---

### Post by DanTheBib on 2010-08-26
That's okay, thanks for helping out man. I'm having a look for other people with these "random" folders on the D drive. Initial digging is people saying is part of an update that can be safely deleted.

---

### Post by 29732 on 2010-08-26
idk, it doesnt look like anything is installed on that not even xp recovery
i think it is safe to remove it
but it is your choice on erasing it, something might go wrong

---

### Post by DanTheBib on 2010-08-26
I copied them onto my C drive, and a lot of the files I copied were already on there, and I was asked to merge or replace..I merged some, but skipped the replaceable ones...

Am I safe to do this :S

---

### Post by 29732 on 2010-08-26
yah, i think it is ok
well try to copy all that into a desktop folder, then it shouldnt say that

---

### Post by DanTheBib on 2010-08-26
Did that. Right clicked, unmounted, but have no option to erase? Could I just delete the partition?

---

### Post by 29732 on 2010-08-26
ummm when you (left) click on that parttion, it should show that erm... red circle with a slash
click it

---

### Post by The Real Dave on 2010-08-26
The RECYCLER folder is simply your recycle bin. It is probable that the other folders are parts of downloaded Windows updates which are no longer needed. The rest of the 90MB is possibly a pagefile, Windows' equivalent of swap. 

All in all, I would not be worried about removing them. To be completely safe, ensure that there are no updates pending for your Windows install. 

As regards to installing Ubuntu, personally, I would use the following method (the one I use on the majority of my computers)

Begin the install process using the LiveCD, and when you get to the Partitioning section, select manual. 

Delete the /dev/sda3 partition, the one in question. In the now unallocated space, create an extended partition, using the full size of the unallocated space. 

Now create a 10GB ext4 partition at the beginning of that extended partition. It's mount point should automatically be set to "/". This partition will hold your system files, and should be more than enough for an "average" user. 

Create a swap partition at the end of the extended partition. This will leave the layout something like

      10GB ext4 
      Unallocated Space
      Swap Partition

The exact size of your swap partition will vary based on the amount of RAM your computer has. I find that for the average user with 1 or 2GB of RAM, 1Gb of swap should be plenty. My computer has 1.4GB of RAM with 1GB of swap and will handle extremely heavy loads, including virtualisation. I find that for an "average" user, more than 1GB of swap is a waste of harddrive space.

Finally, create a partition using the remaining unallocated space. This too can be ext4, and the mount point must be "/home". This will give a layout like

      10GB ext4 /
      61GB ext4 /home
      1GB swap

/home is where all your user data is stored, and the majority of your program settings also. Having seperate / and /home partitions gives an added layer of protection to your data in that a corrupt / filesystem will not destroy any of your personal files. It will also make re-installing or upgrading Ubuntu easier. This is how I have done things for the past 5 releases, and it's saved my bacon more than once. 

I feel that this would be the best approach for you. I hope that this is clear enough to follow, if not, please, don't hesitate to ask questions. I will advise you to double check everything before you click apply, to ensure that the correct partitions have been created/destroyed as a slip of the finger has lost people data in the past :(

Best of Luck mate :)

---

### Post by DanTheBib on 2010-08-26
I have nothing like that there..I left click, nothing happens. I right click, you get the usual then "mount", "format", "properties"

---

### Post by 29732 on 2010-08-26
erm, i think it is a bit too hard for him
i think deleting the "d" partition and then installing on the free space (with the installer, not that advanced section(it'll show when it sees free space)) is muuuuch easier

---

### Post by worldsayshi on 2010-08-26
I've just recently pulled off installing dual boot win 7 and ubuntu so I might give you some heads up on this, although I wouldn't call myself an Ubuntu expert just yet :p

I mostly followed this community tutorial:
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

With a little help from this on how to edit windows partitions:
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")

It sounds as if you should be able to muster those...

**About partitions (long home made explanation, somewhat accurate):**
You might need to know that partitions in windows and linux are treated a bit differently. In Windows, each partition is given a letter (C,D etc...), in linux/ubuntu they are "mounted" to a single file system, meaning that they will end up "as a" folder in the only file system. This means that while windows has multiple file system roots (not to be confused with the root user), linux has only one. The main partition is mounted to the file system root. The root is called simply '/' (a forward slash).

You might also need to know that partition can be formated to different types of *file systems*. Some are better with windows, some are better with linux. Some are incompatible with the other in one way or the other:
[http://en.wikipedia.org/wiki/File_system#Disk_file_systems]("http://en.wikipedia.org/wiki/File_system#Disk_file_systems")

I'm not sure what those files in D do (perhaps they are a [recovery partition]("http://en.wikipedia.org/wiki/Recovery_disc#Recovery_partitions")?), I would make sure that I had all files I wanted to preserve backed up and a recovery disk or two close at hand before going about. Have fun!

Oh, and another thing. What you should be aiming at is to create non-partitioned space on your drive, then let the ubuntu installer create its own partition using the free space (free as in unpartitioned, not as in free space on a partition ). Thats how I did. Maybe you could install ubuntu on an existing partition.

---

### Post by 29732 on 2010-08-26
> **DanTheBib said:**
> I have nothing like that there..I left click, nothing happens. I right click, you get the usual then "mount", "format", "properties"
hmmm.... 
that is so weird
i guess you will have to follow The Real Dave's advice

---

### Post by DanTheBib on 2010-08-26
Well bearing in mind I'm installing from the USB, how do I make Ubuntu install on the rest of the free space in the D drive? My thoughts atm are go onto Widows, shrink the partition that is the D drive currently, and let ubuntu partition the rest of the space? Will that work, or is there a way to just whack it in the free space now?

---

### Post by The Real Dave on 2010-08-26
> **DanTheBib said:**
> Well bearing in mind I'm installing from the USB, how do I make Ubuntu install on the rest of the free space in the D drive? My thoughts atm are go onto Widows, shrink the partition that is the D drive currently, and let ubuntu partition the rest of the space? Will that work, or is there a way to just whack it in the free space now?

There is, or at least should be. Though it strikes me as strange that there is no "delete" option in your Gparted when you right click on the partition. Are you sure the partition is unmounted? What does it show when you right click, and click Information?

---

### Post by rportnoy on 2010-08-26
Think the easiest way. use partition manager like partition magic, to resize your drive. I used to try use resize partition when installing jaunty but it can't save the data. ubuntu standard instalation takes almost 2 GB, for swap space usually 1.5 or 2 times of your RAM. recomended size I think about 5 GB. I ever had 4 operating system on my PC. win XP, win 98, Redhat, Mandrake, and suse, you only need one swap space for all distro.

Now I have Backtrack Linux (based on Ubuntu) and win XP installed on my computer, another computer jaunty, karmic and for server I use CentOS 5.
The partitioner on Backtrack Linux can resize partition without destroying data. I've done several times, but Backtrack standard installation takes about 7 GB. Although backtrack based on ubuntu it's not for newbie, almost everything must be set by our self, but you'll learn more...

Please note that resizing partition will take much time depend on data size, don't try do anything during the process, and back up first.

Sory for the long post...

---

### Post by 29732 on 2010-08-26
it will give you an option to delete the "d" partition (/dev/sda3)in the advanced partitioning option of the install "it gave it to me even on ntfs so it SHOULD have that option for you
follow The Real Dave's advice

---

### Post by The Real Dave on 2010-08-26
@Dan, I'm going to fire up a VirtualMachine, and follow the install process through that. I should then be able to give you step by step instructions. I can no longer remember the options off the top of my head. Bear with me just a moment.

---

### Post by 29732 on 2010-08-26
> **The Real Dave said:**
> @Dan, I'm going to fire up a VirtualMachine, and follow the install process through that. I should then be able to give you step by step instructions. I can no longer remember the options off the top of my head. Bare with me just a moment.
Bear not bare ;)
and btw, youll have to make an ntfs partition and try to remove it with gparted

---

### Post by The Real Dave on 2010-08-26
> **29732 said:**
> and btw, youll have to make an ntfs partition and try to remove it with gparted

Hold on, you just made me realise the problem I think.

Dan, can you please open Synaptic (System>Administration>Synaptic Package Manager) and search for ntfsprogs. If that package is not installed, you will not be able to manipulate NTFS partitions. It is possible that it is standard in 10.04, but I am not sure. If it's not installed, install it by right clicking, clicking Mark for Installation, and finally, clicking Apply.

---

### Post by 29732 on 2010-08-26
yay we figured it out! ^_^

---

### Post by wilee-nilee on 2010-08-26
My 2 cents shrink the sda3 partition with gparted with the swap off, leaving a open space and install Ubuntu to it. The aforementioned D partition=sda3 which will be shrunk can be read a  written by MS or Linux.

You always have to turn the swap off to resize or delete partitions.

---

### Post by 29732 on 2010-08-26
what?what?what?what?what?what?what?what?what?what?what?what?what?what?

---

### Post by The Real Dave on 2010-08-26
> **wilee-nilee said:**
> You always have to turn the swap off to resize or delete partitions.

Not necessarily, it depends on the layout of the partitions. If a partition is mounted below the one you are editing, you will indeed have to unmount it, or in this case, turn off the swap, but this is not always the case.

---

### Post by DanTheBib on 2010-08-26
Thanks guys, give me a minute, I've had to remake the usb, and then I'll run Ubuntu from it of course. So Dave, am I best deleting the D drive entirely, or shrinking it in the way that is mentioned by wilee-nilee? 

Back in a moment!

---

### Post by 29732 on 2010-08-26
deleting it is my best option

---

### Post by The Real Dave on 2010-08-26
> **DanTheBib said:**
> Thanks guys, give me a minute, I've had to remake the usb, and then I'll run Ubuntu from it of course. So Dave, am I best deleting the D drive entirely, or shrinking it in the way that is mentioned by wilee-nilee? 

Back in a moment!

That depends. If you want to have a shared storage between Ubuntu and Windows, shrinking it may be a good idea. Both Windows and Ubuntu can safely read and write to NTFS. However, remember, you can always simply mount your C drive in Ubuntu are write or read files stored there without any danger. 

It boils down to whether or not you reckon you need the storage space D drive offers to be available in Windows. Seeing as you havn't touched it so far, and still have plenty of space on C drive, I wouldn't say so. So personally, I'd simply delete the D drive, and any files that were needed on both Windows and Ubuntu could simply be stored on C.

---

### Post by DanTheBib on 2010-08-26
Well I just figured out how to shrink/delete etc, I was not looking through GParted. So now I have 72GB of "unallocated" state. 

What do I do now :D

---

### Post by wilee-nilee on 2010-08-26
> **DanTheBib said:**
> Thanks guys, give me a minute, I've had to remake the usb, and then I'll run Ubuntu from it of course. So Dave, am I best deleting the D drive entirely, or shrinking it in the way that is mentioned by wilee-nilee? 

Back in a moment!

I am not sure why you have been told to delete D unless you need ? partition. As it is you have 3 primary, you can have 4 max. So you make the forth with a auto install; into open space creating a extended with a logical=Ubuntu and a swap. You can within that extended shrink the original Ubuntu install and install others in custom logical partitions.

For example on my computer I have 2 primaries one W7 one ntfs for ms Linux shared partition. I then have a extended that has Lucid and maverick with a swap. 

If you use gparted from the live cd to resize sda3 **reboot the computer to MS** to make sure everything is working, before installing in the empty space left. I suggest a auto install to begin with it will set you up with the correct partitioning with a extended.

---

### Post by 29732 on 2010-08-26
> **The Real Dave said:**
> That depends. If you want to have a shared storage between Ubuntu and Windows, shrinking it may be a good idea. Both Windows and Ubuntu can safely read and write to NTFS. However, remember, you can always simply mount your C drive in Ubuntu are write or read files stored there without any danger. 

It boils down to whether or not you reckon you need the storage space D drive offers to be available in Windows. Seeing as you havn't touched it so far, and still have plenty of space on C drive, I wouldn't say so. So personally, I'd simply delete the D drive, and any files that were needed on both Windows and Ubuntu could simply be stored on C.
but windows wont be able to read ubuntu's contents
how bout making a FAT32 partition?

---

### Post by DanTheBib on 2010-08-26
So I'm going to go ahead and start windows to make sure it's fine. After that I'll just follow the Ubuntu install as much as I can. Then I'll post here assuming everything is ok :)

---

### Post by 29732 on 2010-08-26
mmk good ^_^

---

### Post by The Real Dave on 2010-08-26
> **29732 said:**
> but windows wont be able to read ubuntu's contents
how bout making a FAT32 partition?

That wouldn't change anything particularly. Windows still wouldn't be able to read Ubuntus material. What I said was that anything that needed to be accessed by both, should be stored on the C drive, which is mutually accessible. Either way, FAT32 has a 4.2GB file size limit, which once forced me to backup 200GB of Data simply to reformat.

@Dan, next thing to do is to run the installer, by double clicking on the Install Ubuntu icon on the desktop. The advice to check in Windows to ensure everything is functional is probably a good idea, it can't hurt at least.

@29732 Out of interest, what does mmk stand for?

---

### Post by 29732 on 2010-08-26
hmmm... 
hmmmmmmmmmmmmmmmmmmmmmmmmmmm....................
hm.
weird 
i was thinking that you would be able to put all your ubuntu docs onto the fat32 partition so windows would be able to see it forevah, and evah, and evah...
but i didnt know that 4.2GB file limit!

---

### Post by 29732 on 2010-08-26
looks like i was sorta, kinda, erm... dumb :P

---

### Post by The Real Dave on 2010-08-26
> **29732 said:**
> 
i was thinking that you would be able to put all your ubuntu docs onto the fat32 partition so windows would be able to see it forevah, and evah, and evah...


You could do the same with an NTFS partiton. Essentially, the method I described simply gets rid of having a seperate partition, and should be neater.

---

### Post by 29732 on 2010-08-26
you could still put all the stuff on the partition that already has windows instead making ANOTHER partition

---

### Post by The Real Dave on 2010-08-26
> **29732 said:**
> you could still put all the stuff on the partition that already has windows instead making ANOTHER partition

That's what I was getting at ;)

---

### Post by rportnoy on 2010-08-26
To read linux ext2 partition from window use this [URL="http://www.fs-driver.org/"]http://www.fs-driver.org/
[/URL]

---

### Post by 29732 on 2010-08-26
never mind, i read another article about it, it is backward compatible
(or was it another program?)

---

### Post by The Real Dave on 2010-08-26
> **rportnoy said:**
> To read linux partition from window use this [http://www.fs-driver.org/](http://www.fs-driver.org/)

That unfortunately is only compatible with ext2 and ext3. It would mean taking a performance hit moving down from ext4. Other than that, it's the OP's choice.

---

### Post by rportnoy on 2010-08-26
haha...yes... or use partition magic file browser

---

### Post by 29732 on 2010-08-26
> **rportnoy said:**
> haha...yes... or use partition magic file browser
they dont sell it anymore D:

---

### Post by rportnoy on 2010-08-26
what about this? [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by 29732 on 2010-08-26
> **rportnoy said:**
> what about this? [http://www.ext2fsd.com/](http://www.ext2fsd.com/)
yeah, that's the one i was looking at
o wait, it still doesnt support ext4

---

### Post by The Real Dave on 2010-08-26
> **rportnoy said:**
> what about this? [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Again, ext2 or ext3, not ext4.

---

### Post by rportnoy on 2010-08-26
> **29732 said:**
> yeah, that's the one i was looking at
o wait, it still doesnt support ext4
I read someone blog, and he told that it can read ext4 and compatible with windows 7

---

### Post by 29732 on 2010-08-26
he is using winXP
and i still do not think it will work well with  win7

---

### Post by The Real Dave on 2010-08-26
> **rportnoy said:**
> I read someone blog, and he told that it can read ext4 and compatible with windows 7

As far as I'm aware, reading ext4 filesystems from Windows is not yet possible, but I could be wrong. If you could find a link, I would be rather interested.

---

### Post by 29732 on 2010-08-26
[SIZE="7"]I FOUND IT![/SIZE]
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
:KS

---

### Post by The Real Dave on 2010-08-26
> **The Real Dave said:**
> As far as I'm aware, reading ext4 filesystems from Windows is not yet possible, but I could be wrong. If you could find a link, I would be rather interested.

I take it back. Though to be honest, it doesn't look hugely stable yet.

---

### Post by rportnoy on 2010-08-26
When creating the ext4 filesystem, make sure to add “-O ^extent” which  means disabling the “extent” feature bit. I’m not sure will work if your ext4 filesystem still has “extent” feature  enabled. ext2 and ext3 partitions should be fine.

---

### Post by 29732 on 2010-08-26
wheres the op?

---

### Post by rportnoy on 2010-08-26
I used to read it'll unable to change the option when the ext4 has been created.

---

### Post by 29732 on 2010-08-26
lol

---

### Post by DanTheBib on 2010-08-26
Well I just selected Linux to install on "rest of free space" or something to that effect. Updating everything, no problems so far. Actually, my boot menu is a bit odd. Before I just had "Boot Windows XP" and "Boot Linux" 

Now I have

"Boot Linux example 1"
"Boot Linux example 2"
"Boot Linux example 3"
"Boot Windows example 1"
"Boot Windows example 2"

Anyone know why this is? I'm guessing something to do with grub?

Sorry for the slower replies, have to install things and restart computer etc a lot.

---

### Post by 29732 on 2010-08-26
umm tell me what it shows when you type in the terminal:
sudo update-grub

---

### Post by rportnoy on 2010-08-26
> **DanTheBib said:**
> Well I just selected Linux to install on "rest of free space" or something to that effect. Updating everything, no problems so far. Actually, my boot menu is a bit odd. Before I just had "Boot Windows XP" and "Boot Linux" 

Now I have

"Boot Linux example 1"
"Boot Linux example 2"
"Boot Linux example 3"
"Boot Windows example 1"
"Boot Windows example 2"

Anyone know why this is? I'm guessing something to do with grub?

Sorry for the slower replies, have to install things and restart computer etc a lot.
Do you install ubuntu?

---

### Post by rportnoy on 2010-08-26
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by 29732 on 2010-08-26
> **rportnoy said:**
> [http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

that is windows seven 
he has windows xp

---

### Post by The Real Dave on 2010-08-26
> **DanTheBib said:**
> Well I just selected Linux to install on "rest of free space" or something to that effect. Updating everything, no problems so far. Actually, my boot menu is a bit odd. Before I just had "Boot Windows XP" and "Boot Linux" 

Now I have

"Boot Linux example 1"
"Boot Linux example 2"
"Boot Linux example 3"
"Boot Windows example 1"
"Boot Windows example 2"

Anyone know why this is? I'm guessing something to do with grub?

Sorry for the slower replies, have to install things and restart computer etc a lot.

What exactly does it say? It's possible that the Linux options is your standard install, and also a failsafe. Seeing as you've done some updates, you'll probably also have another kernel version already, which will give another option. 

As for having two Window's options, that's probably just a mistake on the bootloader's part, finding two options, when one exists. It's nothing to worry about. Removing unwanted entries is a fairly simply process.

EDIT: [This]("http://ubuntuforums.org/showthread.php?t=1195275") should explain all you need on editing your bootloader. 

I'm glad that you've now got a working system mate, and happy to be of help.

---

### Post by DanTheBib on 2010-08-26
I get 

"Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
done"

Thats basically what I see on startup now. It's not much of an inconvenience but it's bugging me >_>

Also, how to install Chrome? I downloaded it from the website, ran and installed it...and it's not anywhere?

---

### Post by rportnoy on 2010-08-26
> **29732 said:**
> that is windows seven 
he has windows xp
just advice, the guy tells it should be work. but ext2explore works on windows xp. I don't have ext4,  it may still have some bugs. [http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

---

### Post by 29732 on 2010-08-26
> **DanTheBib said:**
> I get 

"Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
done"

Thats basically what I see on startup now. It's not much of an inconvenience but it's bugging me >_>

Also, how to install Chrome? I downloaded it from the website, ran and installed it...and it's not anywhere?
you installed the .deb package?
then if it isnt in the internet section of applications, try
alt-f2 then type in google-chrome

---

### Post by rportnoy on 2010-08-26
> **DanTheBib said:**
> I get 

"Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
done"

Thats basically what I see on startup now. It's not much of an inconvenience but it's bugging me >_>

Also, how to install Chrome? I downloaded it from the website, ran and installed it...and it's not anywhere?
it should under application internet sub menu

---

### Post by DanTheBib on 2010-08-26
Yeah for some reason it hadn't installed properly the first time, tried again and have no problem.

Still got no idea about the bootup though >_>

---

### Post by 29732 on 2010-08-26
the bootup:
from reading your grub.cfg it will be like this:
Found linux image: /boot/vmlinuz-2.6.32-24-generic will be your ubuntu
Found initrd image: /boot/initrd.img-2.6.32-24-generic will be your ubuntu recovery
Found memtest86+ image: /boot/memtest86+.bin will be your memory tests
Found Windows Vista (loader) on /dev/sda1 windows vista recovery partition
Found Microsoft Windows XP Home Edition on /dev/sda2 windows xp

it should show you all that fairly clearly

---

### Post by The Real Dave on 2010-08-26
> **DanTheBib said:**
> Yeah for some reason it hadn't installed properly the first time, tried again and have no problem.

Still got no idea about the bootup though >_>

Take a read of [this]("http://ubuntuforums.org/showthread.php?t=1195275") mate, it should clarify everything.

---

### Post by 29732 on 2010-08-26
and you can always try burg, a more graphical boot loader

---

### Post by wilee-nilee on 2010-08-26
> **DanTheBib said:**
> I get 

"Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
done"

Thats basically what I see on startup now. It's not much of an inconvenience but it's bugging me >_>

Also, how to install Chrome? I downloaded it from the website, ran and installed it...and it's not anywhere?

Geez I wish the conversation on this thread would go to the irc, or get it's own thread.

Chrome will be in Ubuntu Software Center in the menu, most all of the installs you do will not be done directly from a source like chrome or FF, you get the tweaked versions from repositories. You can get these 3 ways the software center, synaptic in the system-admin menu, or apt-get in the terminal.

---

