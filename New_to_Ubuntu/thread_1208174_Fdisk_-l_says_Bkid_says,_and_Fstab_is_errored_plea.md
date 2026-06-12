---
title: "Fdisk -l says Bkid says, and Fstab is errored please help PROBLEM."
date: 2009-07-08
forum: New to Ubuntu
---

### Post by jasonsmr on 2009-07-08
Hi Im really new to ubuntu, just installed it this week, and Im having difficulties with the mounting systems.

The info:
When I want to mount my drive marker Photo shop drive (thus labeled on install) It gives me multiple errors everything from the access denied in accessing the fstab file to the fstab line errors I apparently have after attempting and failing to attend to it properly.

Furthermore now since i played around with the fstab file I apparently make a few things wrong on the system, 
1. Bkid now recognizes TWO! Photoshop drives intact on the system. Perhaps this has something to do with safely removing the hard drive in windows according to the directions the computer help gave. by the way these drives are listed once in the fstab as one "PSS" drive. This is an external fire wire drive. maybe thats the reason why im having problems. I can also use it as a USB if thats easer I just haven't attempted it yet. oh I tried to use the USB and it positively shows up as one drive however it is still unable to mount.

2. My "System" Drive which is the remainder of the Drive that has windows on it and is labeled as System in the command Bkid. However this is labeled CORRECTLY in the fstab as Win and thats what I want it to be kept an mounted as in the future.

3. My internal SATA hard drive that Ubuntu was installed on and is my first boot drive is in correctly labeled in the Bkid as "DRV6_VOL1" and is correctly labeled in the fstab file as "System"./dev/sdc2 UUID=7e121c13-7f5b-47a7-afc2-aec6b889642e

4.There is also another mysterious drive listed as hte sdc2 drive labled Linux install its not my swap drive however its showing up as a entity in the Bkid command, so I had best mount that as viable drive space correct? I belive I labled this as "System0" in fstab >There is also another drive listed it could possabley be my HP photosmart drive showing up it shows in windows as a drive although I have never been able to read a SD card off of it, after I uninstalled Hp software sweet, anyway thats a seprate issue, thing is this drive  this is labeled as External in the Bkid I cant understand this one your guesses are open here, I have 4 drives listen when I installed Ubuntu, this is one of them , I believe its on the same drive volume as hte System and Swap of course, this is labeled Linux. Should I be mounting this?? what should be done? see below for detailes its labled as /dev/sdc2 UUID=7e121c13-7f5b-47a7-afc2-aec6b889642e

5.And my DVD Rom Drive also willnot show up , I have what is labeled a CDRom in the /media/ folder however it is not accessible outside of sudo privileges and even then it doesn't read the disks when i put one it! 

6.I dont even know where to start, so im posting this mess, in hopes some one else can figure out this tower game. I was never great at those anyhow. lol I would really appreciated any and all Ubuntu help
____________________________________________________________________________________

Directories created: (not these are empty directories created using sudo rights. ready to be mounted to.
(as listed in fstab)  NOTE: All fstab and directories are in the / directory not in the media directory. with the exception of the DVD drive, this is in the /media/ directory.
_     _   _    _     _     _     _     _     _                                                                    
PSS=my photoshop drive with art things
System= my Internal 500gig hard drive that holds the Ubuntu OS and some other files. 
System0= my other Linux partion on the same drive as System
Win= My 350 GIG windows drive.
DVDDrive=my dvd rom drive. listed in my fstab and on system in the /media/DVDDrive  folder

____________________________________________________________________________________
**Sudo Fdisk -l**
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16ce16ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004b0906

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30862   247898983+   7  HPFS/NTFS
/dev/sdc2   *       30863       60044   234404415   83  Linux
/dev/sdc3           60045       60801     6080602+   5  Extended
/dev/sdc5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9833c5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

**ls -l /dev/disk/by-uuid**
total 0
lrwxrwxrwx 1 root root 10 2009-07-08 21:42 70A8EA33A8E9F80C -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-07-08 15:14 7e121c13-7f5b-47a7-afc2-aec6b889642e -> ../../sdc2
lrwxrwxrwx 1 root root 10 2009-07-08 15:14 AEB0A309B0A2D75D -> ../../sdc1
lrwxrwxrwx 1 root root 10 2009-07-08 15:14 DC74D8C474D8A296 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-07-08 15:14 dff874e9-a3ca-4768-b87f-69ada9ad6b0b -> ../../sdc5

**blkid**
/dev/sda1: UUID="DC74D8C474D8A296" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sdc1: UUID="AEB0A309B0A2D75D" LABEL="DRV6_VOL1" TYPE="ntfs" 
/dev/sdc2: UUID="7e121c13-7f5b-47a7-afc2-aec6b889642e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="dff874e9-a3ca-4768-b87f-69ada9ad6b0b" 
/dev/sdb1: UUID="70A8EA33A8E9F80C" LABEL="Photoshop Drive" TYPE="ntfs" 

**Here is my fstab:**

# /etc/fstab static file system information.
# <file system> <mount point>   *fs-type*  <options>       <dump>  <pass>
proc            /proc           proc       defaults        0       0
/dev/sda1 UUID=70A8EA33A8E9F80C /PSS auto rw,suid,dev,exec,user,async.errors=remount-rw 0 2
/dev/sdb1 UUID=DC74D8C474D8A296 /Win ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdc2 UUID=7e121c13-7f5b-47a7-afc2-aec6b889642e /System0 auto rw,suid,dev,exec,user,async.errors=remount-rw 0 1
/dev/sdc1 UUID=AEB0A309B0A2D75D /System auto rw,suid,dev,exec,user,async.errors=remount-rw 0 1
/dev/sdb5 UUID=dff874e9-a3ca-4768-b87f-69ada9ad6b0b swap swap sw 0 0
/dev/hda /media/DVDrom udf,iso9660 user,noauto,exec 0 0
usbfs /proc/bus/usb usbfs auto rw,suid,dev,exec,user,async.errors=remount-rw 0 1

_____________________________________________________________________________________

---

### Post by Elfy on 2009-07-09
To start with try editing the fstab

```
gksudo gedit /etc/fstab
```

Remove the /dev/sxy from the lines which have UUID= - you don't want both.

The line for the dvd is wrong, at the moment it says /dev/hda - try /dev/scd0 if you only have the one drive.

I don't know if you have edited the file and have a backup of the original - have a look ```
ls /etc/fstab*
```

---

### Post by jasonsmr on 2009-07-09
OK, I figured that out last night looking at other peoples files, (I originally thought it was wrap) Goes to show dont assume!

I edited the fstab file and did a root mount -a with xterm.

Now im getting a line error and another error I dont know about.

Well Its the DVD ROM I have , This whole time I have been concentrating on the HD's I have and I did not see one post related to the DVD Roms people must have. Mine is mainly used for backup and for playing backups of music, to the (pc ) portion of the Machine, and for burning Backus~ like I said.  

Question is now How do I correctly mount this DVD disk for EXAMPLE:

for a cd ??
for a DVD??
For a PLAYSTATION GAME??
_____________________________________________________________________________________

**the infos on the new fstab is as follows:**

# /etc/fstab static file system information.
# <file system> <mount point>   *fs-type*  <options>       <dump>  <pass>

proc            /proc           proc       defaults        0       0

# /dev/sda1 
UUID=70A8EA33A8E9F80C /PSS auto rw,suid,dev,exec,user,async.errors=remount-rw 0 2

# /dev/sdb1 
UUID=DC74D8C474D8A296 /Win ntfs-3g defaults,locale=en_US.utf8 0 0

# /dev/sdc2 
UUID=7e121c13-7f5b-47a7-afc2-aec6b889642e /System0 auto rw,suid,dev,exec,user,async.errors=remount-rw 0 1

# /dev/sdc1 
UUID=AEB0A309B0A2D75D /System auto rw,suid,dev,exec,user,async.errors=remount-rw 0 1

# /dev/sdb5 
UUID=dff874e9-a3ca-4768-b87f-69ada9ad6b0b swap swap sw 0 0

/dev/hda /DVDDrive udf,iso9660 user,auto 0 0
usbfs /proc/bus/usb usbfs auto rw,suid,dev,exec,user,async.errors=remount-rw 0 1

_____________________________________________________________________________________
**THE ERROR WITH: sudo mount -a**

[mntent]: line 23 in /etc/fstab is bad
DVD it appears in the  COMPUTER:/// directory as DVDDrive now and I can read it.
I did a sudo nautilus apposed to the xterm thing and it gave an error however it does not do it again?? lol

Well it said something along the lines of 
However it now gives the error cannot access /dev/hda is a ro device = read only so my line in the new and improved fstab at 23 where it says rw" is being rejected and somehow replaced with ro when I do a mount -a?

please advise as I stated above I want to use this DVD burner lol. ;)
_____________________________________________________________________________________
im just guessing here however I need to somehow change the permissions on the device itself 
so I did this I used a **ls -l /dev/hda**  to list device and its permissions and sure enough it gave me:

brw-rw---- 1 root cdrom 3, 0 2009-07-09 01:38 /dev/hda

so this should be working properly?? what about that error message I got ,,??>>did it fix itself? lol cuz that would be COOL!

I haven't tried to burn anything blank with it yet ::>> BTW DOES ANY ONE KNOW where I can find Burning software (name for apt-get) that will burn a ps2 game and DVD's?? For backups or at least (LOL) how to manually back these things up for ARCHIVING PURPOSE? myself? THANKS!

Recall need:

CD ROM Burning
DVD ROM Burning
PS2 Burning
_____________________________________________________________________________________
**MY SITUATION PERSONAL /****JUST MY LETTER OF INTRODUCTION**
So far looking good > soon I was thinking about trying to make a job out of having a computer, I have never made money out of this thingsince I built it. Im a 30 year collage GRAD (in MI) currently looking to relocate anywhere. I have a current finance in Japan, she and I recently are engaged, well long story short, Im looking for business ops, and in japan I would like to go for future pursuit, ether by opening up a YK (branch store or office) or opening another there in a separate entity, thats the Big Dream, the short term is: OBTAINING A JOB! 

Im currently living in big rapids as I stated I am looking for gainful employment in any field that I can give my services to  for any company , apart unless there asking me to break a standards law or a Safety ANSI requirement in theory or practice, I have ethics. So that pretty much leaves out Crags list. (thats a Joke) 

There was one possibility for doing a project design on a RF Board, however I have no Idea how long that would take before I could contact a China manufacturer and have another company pick up on the Idea, Im a mechanical designer I know FEA, and manual calculations advanced algebra and matrix algebra, I know Sign Wave conversion Techniques, however these days so does my 16 year old daughter..lol I know theres a program called MATHLAB I have been din-king around with that, Im no electrical designer , However I did take 5 years Drafting , So Im a quick study on standards and layouts and logistics for electrical switching and complex logarithms, hence the Sin wave data study.

I really am looking for people where I can connect with others, companies, project. sources! and individuals with similar interests, as well as  outlooks. If anyone wants to help a excited Collage Grad out, let me know. I would like to get in contact with someone.
__________________________________________________________________________________________________

**WHAT I DO:**

What I DO. I am a Product design Engineer, I research a Idea for Uniqueness, need, demand, and my personal interest (I have to like what I do) and I develop the idea into a product, like a new and improved Ronco Plasma Laser! or you get the idea: It has to have a need or Improvement on existing or new product.  Then I design it, using Standards for the country im in. Then I prototype it. These things are also laid out in project reports a project proposal, and project plans, and timeliness, given to (some one) preferably with hiring power* hint. Or my BOSS... Then during prototyping phases it is necessarily to gain price quotes, and toolshop or manufacturing information, if all of it can be done together thats great! however in mechanical toolshops are for making molding for like cellphones and plastics injection and design stuffs. (most companies offer free quotes) Then after quotes and OPEN communication with other experts and companies and potential suppliers the manufacturing section of the final proposal come across. 
__________________________________________________________________________________________________
For the project reports I do: they generally contain all things required to make a corporate decision project costs,(reoccurring and non reoccurring) prototyping sections, patents section, research section, competition section, design section, alternative designs section, costs breakdown section, market analysis section, suppliers section, with links to BOM, Excel data and graphs, and maneuverability sections are preferable however those extend the length of the project report.

With manufacturing It may be wise to find advice from an expert, and company comparison, I mean you don't want to choose a company that makes your widget to be going bankrupt soon now do you. Finally in the final proposal everything is consolidated into the project report, and can be thought of as a absolute company Bible or Business Plan, 

That is what I do, I am Jason Rupright, Im currently looking for a job.

 Thanks mates,

Jason Rupright
[EMAIL="3jaysn@gmail.com"]3jaysn@gmail.com[/EMAIL]
231-796-0604
[EMAIL="3jaysn@gmail.com"][/EMAIL] 
An Eye For an Eye Makes The Whole World Blind~~Gandhi

---

