---
title: "accessing folder inside Ubuntu installation"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by John Macnab on 2009-06-04
Hi everyone :)
I am very hopeless with linux and am trying to access some filed I d/l-ded from the net. Thing is, I installed windows XP anew and the starting up screen where I get the option for booting into which OS I want has disappeared. If possible, I'd like to copy the downloaded files in linux to windows partition and then delete Ubuntu. (I am hopeless with Linux). The thing is, I booted up from a Gutsy Gibbon version of CD and can go in upto the folder (named 'towritelin') but double clicking on it brings up a :-You do not have the permissions necessary to view the contents of "towritelin" message.How can I gain access to the folder? The folder is in computer>>disk1>>account name>>twowritelin. Hope I haven't confused you with my english, please do forgive me

---

### Post by pastalavista on 2009-06-04
Press alt-f2 and type 'gksu nautilus' and hit enter. That will give you a file browser with root permissions. Your other filesystem should show up in the tree as disk1 or maybe towritelin. I haven't booted from a live CD for a while.

---

### Post by cariboo on 2009-06-04
You could just fix grub, by following this [thread=224351]howto[/thread]. Then you would have to get rid of your Ubuntu installation. 

Remember how long it took you to learn how to use Windows? Ubuntu is different enough that you have to learn how to use your computer all over again.

---

### Post by John Macnab on 2009-06-05
Thank you for the replies sirs, appreciate that very much.Pastalavista I tried the 'gksu nautilus' command,sir, and then browsed into media>>disk>>username and got 'towritelin' but I cant seem to get to copy the 'towritelin' into one of my windows partitions. I wonder why? I click on 'towritelin' and click 'copy'and then when I click paste into my windows partition, nothing happens. What could I be doing wrong?
cariboo907, sir, how do I delete Ubuntu from my puter? After I copy 'towritelin' I want to get rid of Ubuntu.(I am afraid I dont have the aptitude to learn Ubuntu.Not that I am any good with Windows either*sigh*)

---

### Post by zvacet on 2009-06-05
You can try [fs-driver]("http://www.fs-driver.org/") to access Ubuntu partition from Windows and then copy your files to Windows partition.To uninstall ubuntu try [this.]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")After that you can remove Ubuntu partiotion with [Gparted live Cd.]("http://gparted.sourceforge.net/")

---

### Post by col48 on 2009-06-05
If, as I suspect, you are not being offered XP to boot up with, you may not be able to do what zvacet suggests.

Two possibilities:
1. (alternative to nautilus) open a Terminal and do
```
sudo cp /home/xx/yy /disk1/towritelin 
```
where xx/yy represents the source of what you want to copy and /media/towritelin the destination.  Using sudo means you have 'root' permissions.

2. it may be simpler to copy the files to an external medium (floppy or memory stick etc) which could be burn them to a CD/DVD.

If my suspicion is right, can you be sure you can boot up XP after you have deleted Ubuntu?

I have found Ubuntu very friendly and flexible, after a bit of a learning curve - and there are all these nice people in the forums to help with problems :D  - also most things can be done with free software which you don't have to pay for before you know whether it meets your requirements.

---

### Post by John Macnab on 2009-06-05
Thank you for the replies sirs.
zvacet, sir, I went to the fs-driver.org site and there it says it can do stuff with ext2 partitions but I think my linux partitions were ext3 :(
col48, sir, I can actually access XP, it is Ubuntu that I cant access now.(I imagine that is because I installed XP after ubuntu.) Well sir, I personally lack any computer skills unlike you folks who are so good at this stuff and I find Windows kinda easier-honestly I do.I am going to try the way you mentioned :)
Btw I came up with GParted on the net and seems it will help in deleting the linux partition?I have d/lded the live .iso for it but the FAQ says I need **Get parted** and **Gtkmm**for it and also some native tools for some file systems. How do I burn the live iso onto a cd along with the above tools?

Oops!I just tried to get grub back and now I get the choice of OS's to boot from but trying to boot into Ubuntu gives error:17,cannot mount selected partition. Now I have really messed it up!

Ugh I am really stupid but I am having problems with the **sudo cp /home/xx/yy /disk1/towritelin** code. I imagine you meant me to go into my installed unbuntu and then choose the file/folder I wanted but I am running Ubuntu from a live cd,(I am tryin hard to express myself but my english is terrible, do forgive me).So I dunno what to put in the home/xx/yy section of the command. I do have ubuntu installed but after my misadventure that I noted above, I just keep getting error 17

---

### Post by markharding557 on 2009-06-05
from your live cd you should get access to any partitions or folders using > gksu nautilus
gives root access to files

---

### Post by John Macnab on 2009-06-05
Sorry for being so dense,sir, but I did run 'gksu nautilus' and the folder 'towritelin' is accessible in that I can click on it and open it but when I click and select copy on it and then choose one of my Windows partitions and click 'paste' nothing happens.I'm sure that I must be doing something wrong but try as I can,I cannot understand what is preventing the folder from being copied

---

### Post by pastalavista on 2009-06-05
> **John Macnab said:**
> Sorry for being so dense,sir, but I did run 'gksu nautilus' and the folder 'towritelin' is accessible in that I can click on it and open it but when I click and select copy on it and then choose one of my Windows partitions and click 'paste' nothing happens.I'm sure that I must be doing something wrong but try as I can,I cannot understand what is preventing the folder from being copied

It is likely that Windows has "locked" the drive due to an improper shutdown of some program that was still active in some process, many times the anti-virus or Windows update. You should boot Windows, close all running programs manually and make sure they are closed and that there are no pending operations that need to be completed upon Windows restart. Then shutdown and reboot the Ubuntu CD again. You'll need the partition editor to reclaim the drive space that Ubuntu occupied.

---

### Post by John Macnab on 2009-06-05
Thank you for replying,sir.I am trying to salvage some data that I d/lded from the net which is in the folder 'towritelin'. By following your intstruction (alt+F2,gksu nautilus) I managed to gain  access to the folder but can't copy it over to one of my other windows partitions.Btw I also tried to run the **partition editor**in ubuntu live cd but the options to delete and format are greyed out when I try selecting the ubuntu partitions.Also, some partitions like the swap, /dev/sda10 (/media/disk-2) etc are showing a lock icon.I cant 'unmount' those partitions either.*really sorry for putting in so many topics*

---

### Post by pastalavista on 2009-06-05
> By following your intstruction (alt+F2,gksu nautilus) I managed to gain access to the folder but can't copy it over to one of my other windows partitions.Btw I also tried to run the partition editorin ubuntu live cd but the options to delete and format are greyed out when I try selecting the ubuntu partitions. I believe this is because your installation of Windows has made the entire hard disk 'read-only' or locked it until such time that it can complete running tasks or shut down stubborn programs. Did you understand my previous post? 
1. Boot into Windows XP
2. Allow Windows to fully load, finish updates and system checks
3. Manually exit all programs and confirm they aren't running (including anti-virus)
4. (optional) run Windows check disk and defrag and then shutdown.
5. Boot the Ubuntu live CD and try the file operations and partition editor again.

---

### Post by zvacet on 2009-06-05
@ **John Macnab**

If you can run Windows fs-driver will work with ext3 partition.

---

### Post by John Macnab on 2009-06-06
Thank you for the replies sirs. 
pastalavista,sir, I tried what you recommended step by step but it didn't help :(
zvacet,sir, thank you for clarifying that.
I got frustrated with trying to access the folder I wanted and I even tried to remove partitions using the partition editor but it showed a lock icon for some of the partitions.(what is the meaning of that **lock icon**??).(I mean a lock icon against some of the drives when the partition editor is being used) I ended up booting into windows and running compmgmt.msc and deleted the linux partitions from inside there.It then allowed me to format the resulting free space into an NTFS drive.I didn't get to copy the folder I wanted though:( But tyvm to everyone for helping :)

---

### Post by louieb on 2009-06-06
> **John Macnab said:**
> ...I went to the fs-driver.org site and there it says it can do stuff with ext2 partitions but I think my linux partitions were ext3 ...
ext3 is backward compatible with ext2. For what you want to do fs-driver will work just fine.

---

### Post by John Macnab on 2009-06-07
Ty for the reply sir.:) I still wonder why there were  those lock icons against some drives in my partition editor in the ubuntu live cd. And perhaps there must be a better way to deal with it than the way I did? I mean, I was able to bring up compmgmt.msc up because I happened to have Windows XP on the drive but if I hadn't have Windows how could I have removed Ubuntu? By using GParted? I would like to know-hope someone would enlighten me

---

