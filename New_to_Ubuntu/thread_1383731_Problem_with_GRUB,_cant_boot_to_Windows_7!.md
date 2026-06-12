---
title: "Problem with GRUB, cant boot to Windows 7!"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Ira_S on 2010-01-17
i had just windows 7 on this computer,  then i decided to give ubuntu 9.10 a try.  

i installed them side by side.  now when i enter GRUB (when i turn the computer on)
i am given choices,   Several UBUNTU choices,  and then Windows 7 Loader,   

However, when i select the Windows 7 Loader,  GRUB has an error,  and it says "Unknown File System"   


i would realy like windows 7 back, I am willing to do anything exept format...  because i have programs and files that i want on windows 7.. THat only work on windows 7.

I dident know that Linux was so invasive in Operating systems....

please help!

---

### Post by warfacegod on 2010-01-17
Linux is not invasive, its actually Windows being invasive. Apparently Windows will "shut itself off" sometimes if you install a different OS next to it. Personally I think its a violation of Anti-trust laws but what do I know.

From a Terminal try:

```
sudo update-grub2
```

---

### Post by Ira_S on 2010-01-17
last time i did that,  it corrupted the whole boot loader.  and linux is the one thats invasive,  it has to put its own little loader, (GRUB) that is ugly, and doesent work..

does anyone know of a free partioner, so i can just delete the linux partition?  i used to have lots of respect of UBUNTU 9.10,  but the system is too complex.,


any free partitioners that i can mount on a DVD?

---

### Post by warfacegod on 2010-01-17
Use the CD you installed ubuntu with. It has a partitioner. Its called Gparted.

---

### Post by Ira_S on 2010-01-17
i downloaded with the software center,  how the heck do you run the stuff that you download with the software center?  where is it...    is there such thing as a standalone file on linux?? lol!


thats what i like about windows.  the .exe file

where can i run it?

---

### Post by garvinrick4 on 2010-01-17
Did you install MANUAL in gparted when you loaded Unbuntu 9.10 or pick your size of Linux on
disk and let gparted do the partitioning?

What does "sudo fdisk -l" without quotes, post in Thread.

---

### Post by Ira_S on 2010-01-17
i found it,  i hope this works,  ill reply again if it works

---

### Post by Ira_S on 2010-01-17
ok im on the Gparted program,   but i cant do anything with the list,  all the buttons and actions in the drop down menus are indented. (not pushable)   how do i run it from the disk? do i have to type it in in a terminal? when i boot FROM THE DISK?  as in "Try ubuntu without any changes to the computer"     

from there i will try formatting the partions, 

and if anyone wants to keep me with ubuntu, (i would love to have windows 7 and ubuntu coexist peacefully) then they should show me how to do it.

---

### Post by oldfred on 2010-01-17
Some links. Most of the how-to's for Vista and linux also work except now Karmic has grub2 which requires different commands if it needs updating.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by warfacegod on 2010-01-17
> **Ira_S said:**
> ok im on the Gparted program,   but i cant do anything with the list,  all the buttons and actions in the drop down menus are indented. (not pushable)   how do i run it from the disk? do i have to type it in in a terminal? when i boot FROM THE DISK?  as in "Try ubuntu without any changes to the computer"     

from there i will try formatting the partions, 

and if anyone wants to keep me with ubuntu, (i would love to have windows 7 and ubuntu coexist peacefully) then they should show me how to do it.

In LiveCD it should be in System> Admin.> Gaparted

If You like ubuntu and want it to coexist with 7, I suggest searching the forum tips and tutorials.

---

### Post by Ira_S on 2010-01-17
Ok,  ok, thanks for all the help people, but im gonna need loads more.   i formatted all the partitions exept for the NTFS (windows 7)  so now i have that, and "un allocated space"

HOWEVER now when i turn the computer on, GRUB still ******* loads... whats going on here.  did GRUB put itself on my NTFS ????   i have important information on there.   that i would rather not copy.

anyways,  when GRUB trys to load,  it just says error.  . and then somthing about grub rescue,      

how can i get rid of that? do i have to access the boot files using the CD UBUNTU? (what im using right now)


GRRR.....   please help

---

### Post by garvinrick4 on 2010-01-17
> **Ira_S said:**
> ok im on the Gparted program,   but i cant do anything with the list,  all the buttons and actions in the drop down menus are indented. (not pushable)   how do i run it from the disk? do i have to type it in in a terminal? when i boot FROM THE DISK?  as in "Try ubuntu without any changes to the computer"     

from there i will try formatting the partions, 

and if anyone wants to keep me with ubuntu, (i would love to have windows 7 and ubuntu coexist peacefully) then they should show me how to do it.

Here is a link you must read if you want to learn to partition a drive there is no secret to it.
It is an aquired skill. Linux is a fantastic OS but you cannot learn by osmosis. 



[GParted partitioning software - Full tutorial]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by Ira_S on 2010-01-17
I already did that,  like i said in my previous post, please read it  (on page 2)

---

### Post by garvinrick4 on 2010-01-17
Grub is the bootloader and takes over for Windows bcd bootloader and chainloads itself to
the Grub2.

If you want to reinstall I left link in last post. I truly have no idea what you have done or where
you are at. You have not explained just said it does not work. Do you have a 7 install anymore?
What does your partition table look like? Sounds like you made an absolute mess but maybe
not, tell these people what you have installed and what you have done.

---

### Post by Ira_S on 2010-01-17
like i said,  Windows 7 is the only thing installed,  the rest of the harddrive is UNALLOCATED SPACE..

when i turn it on, GRUB tryes to boot, but fails..

is there a way i can delete all of the GRUB files? or should i try reformating the Unallocated space.

---

### Post by warfacegod on 2010-01-17
Do a search on repairing Windows 7s Master Boot Record.

---

### Post by d3v1150m471c on 2010-01-17
> **Ira_S said:**
>  thats what i like about windows.  the .exe file 

I mean no offense in saying this but you have to understand linux is a whole other ballgame. .exe is simply an "executable" file exclusively for windows. However, Linux can execute all sorts of files if they're designed for it and given executable permissions. Check out bash scripts and batch files to name a couple executable files. Don't get discouraged. It's just a matter of learning what linux recognizes as executable and can execute. You'll find as far as scripts go that can execute, all operating systems can use multiple forms of these and most of them just use different names (granted the language will be different).

---

### Post by d3v1150m471c on 2010-01-17
Try pressing esc immediately after you pass the bios option and see if you cannot get to the grub menu. When i had vista on this a long while ago, utilizing that menu allowed you to choose from either ubuntu or windows.

---

### Post by baddog144 on 2010-01-17
GRUB installs itself on a special part of the hard drive called the Master Boot Record (MBR). You need to have your Windows 7 install CD handy to get the Windows 7 loader back. Normally a repair install will do it.

---

### Post by garvinrick4 on 2010-01-17
How to install Windows 7 boot loader is in this link. click on it and read it.


[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Ira_S on 2010-01-17
I got the Windows 7 DVD, and tryed doing an auto repair,   that did not work,  i did some updating using the windows DVD,     (bootsect/nt60 SYS) that stuff,  after i did that, it still had the GRUB error,  I whent back on the Windows DVD and did an Auto repair, THIS TIME,  it said that there was not any problems, (before it acted like it had fixed somthing) 


i am still working on it,  i will click on that previous link too.   I gotta do this, i  have been working on this for almost 5 hours....

---

### Post by Ira_S on 2010-01-17
Ok, NEW STATUS.    now when i turn on the computer without a DISC in it,  the GRUB does not come up,  now all i get is the black command screen, with the blinking cursor at the top left corner.

When i load auto boot repair with the windows 7 DVD,  it says no problems found,  i have also tryed some other manual CMD (Windows 7 DVD) ways. such as bootrec.exe,  and Bootsect/nt60 SYS


No that GRUB appears to be gone,  what should i do now? try REinstalling UBUNTU?

---

### Post by oldfred on 2010-01-18
You need to make sure your win7 boots normally before you install ubuntu/grub. All grub does is pass booting to a working windows, so if windows still has issues do not blame grub.

It also seems the windows repair only repairs one thing at a time:

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)

Hi there, dont worry, boot from Windows 7 dvd and select repair your computer at the Install Now screen.
Run Startup repair thrice and reboot.

---

### Post by MarkC502 on 2010-01-18
Actually Linux is no more invasive to your machine than other OSes, unlike MS who in their infinite wisdom/greed make all choices for you and do everything in their army of lawyers power to lock you into their way of doing things ( its the only way to stay around if you consistently abuse your customers ). Windows like Linux writes ( upon installing ) to your MBR ( master boot record ) at the beginning of your hard disk. GRUB's authors to my knowledge have always tried to include as many technologies as they can regardless of their creators or copyright owners, The same would be a sad attempt at a joke if it were said of the folks at Microsoft. They try to force proprietary standards they create on all they can ( how do you think that IE - probably the 3rd best browser at best stays with the most installs ).

Sorry to pontificate but I get deffensive of the Penguin since he represents the good hearted folks who are working on open source supporting all they can VS corporate greed where software usability and function rate far below profitability in importance to them. If Microsoft actually put out the best and safest software for their customers that they could I would live with the monopoly aspect. But unfortunately their products are only best in the sense that their ads say so, rarely in practice.

MY 3 CENTS

---

### Post by Zen_Spider on 2010-01-18
Well I have to say after downloading and installing Karmic Koala alongside my existing Win7 install over the weekend I can understand how people can get into trouble.
 
Didn't have any problems personally but there's always potential for disaster when you're fiddling with things like boot records and I didn't think the partioning utility was particularly newb-friendly; it does use some references and terms which your average Windows user isn't going to be familiar with.
 
Having said that and by way of encouragement, I've been pretty impressed by what I've seen from Ubuntu so far and it's well worth working through your problems Ira, it looks like a damn fine OS and a hobbyist's dream.
 
I'm rootin' for ya man!
 
:popcorn:

---

### Post by papuccino1 on 2010-01-18
> **Ira_S said:**
> Ok, NEW STATUS.    now when i turn on the computer without a DISC in it,  the GRUB does not come up,  now all i get is the black command screen, with the blinking cursor at the top left corner.

When i load auto boot repair with the windows 7 DVD,  it says no problems found,  i have also tryed some other manual CMD (Windows 7 DVD) ways. such as bootrec.exe,  and Bootsect/nt60 SYS


No that GRUB appears to be gone,  what should i do now? try REinstalling UBUNTU?


Hello Ira.

My honest recommendation is this:

> 
[LIST]
[*]Download [Puppy Linux]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm").
[*]Burn the .ISO image to a blank CD/DVD.
[*]Use that OS as a live version (meaning do not install it).
[*]Connect your computer to another computer or external hard drive and copy every single file on your information partition.
[*]Turn off your PC and insert the Windows 7 disc.
[*]Click to Install Windows 7.
[*]During the partition dialogs, delete **every single partition** until you get one giant unused space.
[*]Format things however you wish using Windows 7.
[*]Bam! Everything will now work as usual and **NO MORE GRUB PROBLEMS.**
[/LIST]


All the best bro!

---

