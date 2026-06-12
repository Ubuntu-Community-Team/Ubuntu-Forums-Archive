---
title: "Absolute Disaster. Please Help"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by ProjectSynergy on 2009-11-21
I have installed Ubuntu 9.10 after a friend recommended it as an alternative to windows.
I have a pre-installed win 7 OS on a Hp laptop. I know NOTHING about scripting , in fact its worse , I freeze  with fear when ever Im asked to type something , it may be irrational but its like a phobia with me.
After reading some stuff on Ubuntu pages I have realised that it is not for me as it seems to entail having knowledge of computers workings and commands , neither of which I posess. I simply want to use it for working with. My problem is even though I installed Ubuntu with maximum care , following precisely the installation process and chosing to install it alongside my original OS , when I started up again I got a message saying 

Grub loading error: no such disk grub rescue. 
I have absolutely no idea what that means , but I do know that whatever I do I cannot get my win 7 running again , cant do it using the boot options in the bios thing  nor choosing System Recovery option on the HP start up choice menu , it just goes straight back to the 
Grub loading error.
The only thing I can seem to do is to put the installation cd back in and re/install ubuntu , however I am petrified this will make it worse.
I am not a good computer person , just a guy who needs to work on his laptop, if i have broken something there is a good chance I will lose my job as there is lots of stuff on the laptop that  is work related.
Please help!!

---

### Post by kansasnoob on 2009-11-21
The most helpful thing you could do for us is boot the Ubuntu Live CD choosing Try Ubuntu without changes ........ then from the Live Desktop run the Boot Info Script and post the results here as described in this thread:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Crossyboi on 2009-11-21
If you have alot of important data then your first priority is to retrieve it, I recommend that you use the live cd to find your files and then back them up onto a USB stick or external hard drive, what you could then do is re install ubuntu, without fear of loosing any files.

Ubuntu isn't all commands and extreme knowledge of computers! There are many different programs very much like some of the ones in windows, why don't you tell us what you need to do with your computer and we can all reccomend programs you can use, for example, open office is very much the same as Microsoft office, with spreadsheets and worksheets etc.

---

### Post by ProjectSynergy on 2009-11-21
Thank you for answering. I am a self-confessed lamer so please feel free to talk to me like a clueless child. I have booted from the cd again and can now see the desktop but I dont see anything about  a Boot Info Script , where will I find it ?

---

### Post by kansasnoob on 2009-11-21
The link I posted:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by ProjectSynergy on 2009-11-21
> **Crossyboi said:**
> If you have alot of important data then your first priority is to retrieve it, I recommend that you use the live cd to find your files and then back them up onto a USB stick or external hard drive, what you could then do is re install ubuntu, without fear of loosing any files.

Ubuntu isn't all commands and extreme knowledge of computers! There are many different programs very much like some of the ones in windows, why don't you tell us what you need to do with your computer and we can all reccomend programs you can use, for example, open office is very much the same as Microsoft office, with spreadsheets and worksheets etc.
Hi crossyboi. I have just given a BIG sigh of relief . I clicked on the icon 235 gb filesystem and was able to navigate to my files , they are being shipped to the usb as we speak. I feel a weight of my shoulders. I was really in a lot of trouble if I could not retrieve them.
The reason I chose Ubuntu was a friend recommended it precisley for the office functions that you described what I read about it seemed like exactly the non-fussy kind of software I could use. Of course as soon as the Grub message came up my heart sank.
I am now more calm as I can see the most important files on my usb stick now. 
However I still need to get back to being able to boot in Win 7 as its not my personal laptop.
I would like to be able to have the choice of booting both systems. However as I say my knowledge of script is non existent. Im looking for help on how to get back to win 7 boot up choice , for now I am getting the message No disk . Thank you for taking the time to help here

---

### Post by ProjectSynergy on 2009-11-21
> **kansasnoob said:**
> The link I posted:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Thank you kansasnoob , I will try this and get back with the file

---

### Post by camaron1 on 2009-11-21
Download the script from [here]("http://sourceforge.net/projects/bootinfoscript/")

and follow the instructions given to you in the previous link

---

### Post by JBAlaska on 2009-11-21
OP, don't panic! If you want your windoze 7 to boot follow these simple steps:

1. Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type **Bootrec.exe /FixMbr** and then press ENTER.
8. Reboot without the CD and windoze will be back in all it's glory...

---

### Post by Crossyboi on 2009-11-21
I'll leave the rest to Kansasnoob as I am not 100% sure on fixing this error, the only thing i can say is that during the installation of ubuntu your windows 7 partition was deleted, I could be wrong, hopefully I am! I read that you said that when going onto the recovery setup you said that it carries on booting the same, this could be a sign that the recovery partition was deleted. As far as I know windows 7 uses 2 partitions and recovery uses one, unless you setup ubuntu on a single partition then I reckon the recovery was deleted.

---

### Post by scorp123 on 2009-11-21
> **ProjectSynergy said:**
>  if i have broken something there is a good chance I will lose my job as there is lots of stuff on the laptop that  is work related.  Sorry to say so: but that was a stupid idea to begin with. **_Never ever install *private* stuff_** on a **[COLOR="Red"]CORPORATE[/COLOR]** laptop that belongs to your employer and not to you. Even if you had not had the technical problems you have now you could still have gotten into trouble when your IT department finds out you messed with your company laptop.

Never ever do that.

And to try out Ubuntu you could have used a private PC or even better: a virtual machine, e.g. under VMware, VirtualBox or Parallels, or something like that.

---

### Post by ProjectSynergy on 2009-11-21
Ok , I have followed the instructions and got a Resuts file, i have attached it

---

### Post by JBAlaska on 2009-11-21
@ProjectSynergy, trust me M8 you just need to fix your master boot record...easy. Follow my above instructions. If you do not have a windows 7 boot disk you can use this one [HERE](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

While it is *possible* that you overwrote your windoze partition, if you followed the Ubuntu installation carefully as you stated, your partition is most likely just fine.

Fixing the MBR will NOT make matters worse.

[COLOR="Blue"]Edit: just read your results file, your windows partitions are just fine. you can revert as per my above post or fix grub and try ubuntu. As I need to go to bed lol. I leave you in capable hands.[/COLOR]

---

### Post by ProjectSynergy on 2009-11-21
> **scorp123 said:**
> Sorry to say so: but that was a stupid idea to begin with. **_Never ever install *private* stuff_** on a **[COLOR=Red]CORPORATE[/COLOR]** laptop that belongs to your employer and not to you. Even if you had not had the technical problems you have now you could still have gotten into trouble when your IT department finds out you messed with your company laptop.

Never ever do that.

And to try out Ubuntu you could have used a private PC or even better: a virtual machine, e.g. under VMware, VirtualBox or Parallels, or something like that.

You are of course right , and no-one is recriminating with me more than myself for having done this. I did it because Win7 was making it impossible for me to run some stuff that I needed , and a friend said that Ubuntu would do it without a fuss, it was the need to get stuff finished that led me to install it, the idea was to finish the work in Ubuntu and then get back to windows and complaining about how crap it is later. ( it would have just sounded like making exuses for not gettting the work done , to the boss)

---

### Post by ProjectSynergy on 2009-11-21
I am now at the win 7 recovery disk download page, now the next lame question , which should I download , the 64 bit or 32 bit version , I understood that Win 7 was both

---

### Post by JBAlaska on 2009-11-21
For this MBR recovery it does not matter, but since your laptop may not be 64bit choose the 32bit version.

---

### Post by ProjectSynergy on 2009-11-21
big thanks for all your help , this is beyond appreciated, Downloading the disk now

---

### Post by JBAlaska on 2009-11-21
NP, I'll try to hang in a while in case you have a question. Make sure to burn the iso on a slow speed.

---

### Post by ProjectSynergy on 2009-11-21
Is there a prog inside ubuntu for burning cds ? Iso burning ?

---

### Post by Spiritof76 on 2009-11-21
Yes and it works well

---

### Post by Martje_001 on 2009-11-21
Just right-click the iso and choose 'Burn this image'.

---

### Post by JBAlaska on 2009-11-21
Brasero in sound and video, Choose "Burn Image" from menu

---

### Post by frenchn00b on 2009-11-21
> **ProjectSynergy said:**
> I have installed Ubuntu 9.10 after a friend recommended it as an alternative to windows.
I have a pre-installed win 7 OS on a Hp laptop. I know NOTHING about scripting , in fact its worse , I freeze  with fear when ever Im asked to type something , it may be irrational but its like a phobia with me.
After reading some stuff on Ubuntu pages I have realised that it is not for me as it seems to entail having knowledge of computers workings and commands , neither of which I posess. I simply want to use it for working with. My problem is even though I installed Ubuntu with maximum care , following precisely the installation process and chosing to install it alongside my original OS , when I started up again I got a message saying 

Grub loading error: no such disk grub rescue. 
I have absolutely no idea what that means , but I do know that whatever I do I cannot get my win 7 running again , cant do it using the boot options in the bios thing  nor choosing System Recovery option on the HP start up choice menu , it just goes straight back to the 
Grub loading error.
The only thing I can seem to do is to put the installation cd back in and re/install ubuntu , however I am petrified this will make it worse.
I am not a good computer person , just a guy who needs to work on his laptop, if i have broken something there is a good chance I will lose my job as there is lots of stuff on the laptop that  is work related.
Please help!!


you have to go to command line into the grub menu at boot

then 

help

root (hd0,  **[COLOR="Red"] press tab[/COLOR]**

to find your disk

here an example of commands:

> root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-k7
savedefault
boot


beware there is a grub2, the grub team, they changes all their commands, just to f * c k all newbies and make it harder or impossible.
Grub is nice, far nicer than lilo was. I like grub.


to run windows
you need to make the partition active and
do 
chainloader +1
boot
and you get windows
i forgot hte exact commands

can someone write the correct commands ?

---

### Post by ProjectSynergy on 2009-11-21
Ive burned the recovery disk i down loaded , now I get the message when trying to boot with the disk , THis version of System Recovery is not campatible with the version of windows you are trying to repair.

Im guessing I should try with the 64 bit version ?

---

### Post by ProjectSynergy on 2009-11-21
> **frenchn00b said:**
> you have to go to command line into the grub menu at boot

then 

help

root (hd0,  **[COLOR=Red] press tab[/COLOR]**

to find your disk

here an example of commands:



beware there is a grub2, the grub team, they changes all their commands, just to f * c k all newbies and make it harder or impossible.
Grub is nice, far nicer than lilo was. I like grub.


to run windows
you need to make the partition active and
do 
chainloader +1
boot
and you get windows
i forgot hte exact commands

can someone write the correct commands ?
  Thanks for your advice , unfortunately I dont understand what these commands mean , where i should do it etc , I really am that lame. I dont know if you mean I should type all of that or which part of it , its these kinds of commands that leave me totally lost in the ubuntu environment 
. But thanks for trying to offer a solution all the same

---

### Post by ProjectSynergy on 2009-11-21
Ok  , now this is wierd , I rebooted my comp after taking out the win 7 recovery disk and it is now , showing me a Grub menu with different options. I wasnt sure which to choose so I let it run on and it now seems to be loading something, going to give a running commentary in this post so that people know the sequence of things happening.

It did a lot of writing on the black command screen and is now just blank. Will wait to see if it does something else. Has now been black for 2 minutes , will wait more.

4 minutes  still blank screen , hmmmm. Should I wait more...? It feels like there is something there , not a complete black no screen , there is some light on screen but no image or writing or prompt at all

---

### Post by Bartender on 2009-11-21
Project -
Risking your job was ill-conceived, doubly so because your level of expertise in this area appears to be pretty thin.  I think you need to find a geek who you trust to try and help you out.
I certainly understand your desire to fix this as quietly as possible, but I think you're in over your head...

---

### Post by camaron1 on 2009-11-21
> **ProjectSynergy said:**
> Ok  , now this is wierd , I rebooted my comp after taking out the win 7 recovery disk and it is now , showing me a Grub menu with different options. I wasnt sure which to choose so I let it run on and it now seems to be loading something, going to give a running commentary in this post so that people know the sequence of things happening.

It did a lot of writing on the black command screen and is now just blank. Will wait to see if it does something else. Has now been black for 2 minutes , will wait more.

4 minutes  still blank screen , hmmmm. Should I wait more...? It feels like there is something there , not a complete black no screen , there is some light on screen but no image or writing or prompt at all

What options where you given in the grub menu?

---

### Post by ProjectSynergy on 2009-11-21
> **camaron1 said:**
> What options where you given in the grub menu?

Sorry dont recall , but I think it was different Linux types and a reference to windows.
Im going to try to reboot and will give the list of options here

Dam , I just did Alt ctrl del to restart and its not responding , should I just force shut down  with the off button? It is now 8 mins with no screen activity

---

### Post by camaron1 on 2009-11-21
> **ProjectSynergy said:**
> Sorry dont recall , but I think it was different Linux types and a reference to windows.
Im going to try to reboot and will give the list of options here

Dam , I just did Alt ctrl del to restart and its not responding , should I just force shut down  with the off button? It is now 8 mins with no screen activity

My advice: force a shutdown, restart, take note of the options, log into Ubuntu to make sure things ok, tell us the grub options, shut comuter and wait for advice.

---

### Post by ProjectSynergy on 2009-11-21
ok , I forced shut down and am now back getting the error no such disk message.

would someone be as kind as to walk me through what Im supposed to type in to rescue the grub ? I mean step by step , and to say clearly without jargon what exactly to type in 

appreciated

---

### Post by camaron1 on 2009-11-21
> **ProjectSynergy said:**
> ok , I forced shut down and am now back getting the error no such disk message.

would someone be as kind as to walk me through what Im supposed to type in to rescue the grub ? I mean step by step , and to say clearly without jargon what exactly to type in 

appreciated

It seems that after you inserted the recovery dvd (which was not recognized)your grub menu appeared again. Why don't you try that again. That can't cause any harm. If you get the grub menu again and are lucky enough one of the entries will be something like WINDOWS RECOVERY MODE and you go straight there.

---

### Post by ProjectSynergy on 2009-11-21
> **camaron1 said:**
> It seems that after you inserted the recovery dvd (which was not recognized)your grub menu appeared again. Why don't you try that again. That can't cause any harm. If you get the grub menu again and are lucky enough one of the entries will be something like WINDOWS RECOVERY MODE and you go straight there.
tried that , didnt happen this time ,  while I am waiting on the  64 bit version of win 7 recovery to download I have booted from the ubuntu cd and have just  pressed Check Disk Integrity , it is now performing that , although I get a message saying it may take some time. Will report back with the result. Dam I am such a dick !

---

### Post by camaron1 on 2009-11-21
That integrity check is only for the live cd, not much use for you right now. Try to calm down in the meanwhile. Your Windows partition is there, you'll be fine in the end.

---

### Post by ProjectSynergy on 2009-11-21
Ok I finally got the Win 7 recovery disk (64 bit ) to start up , I now have several options 

Start up Repair

System Restore 

System Image Recovery 

Windows Memory Diagnostic 

Command Prompt


my guess is Start up Repair ,  right ?

Im  worried about doing the wrong thing again and messing it up even further , which is why I am asking about each step

EDIT>  not sure if it is indicative of anything but it now states Windows is on D:  Local Disk whereas before it was on C:

---

### Post by ProjectSynergy on 2009-11-21
I ran the recovery disk , it says no problems found , restart , so I restarted and it went straight to the the Grub rescue prompt again. I am now at a total loss as to what to do now.

Im guessing the only way to resolve this is to try to use the rescue menu , but I dont have a clue what to do with it . Is there anyone who could walk me through it please

---

### Post by camaron1 on 2009-11-21
Come on people, there must be someone able to help him...?

---

### Post by ProjectSynergy on 2009-11-21
Thanks for the support Cameron. Ive just run the windows recovery and it doesnt seem to be much good to me , the simple recovery tells me that my files are fine and the system restore gives an error , says I need to re/install from back up , which of course I dont have nor a installation disk. Of course I have now established that the problem isnt with windows   but with the boot itself, I dont get the choice of  booting other OS at start up , it goes directly to the Grub Rescue command prompt where i get the error message.

The solution is going to have to be around making Grub fix itself ,but as  said before I dont have the foggiest idea how to do it , The links that people sent me for fixing it may as well be in chinese as I have no idea what they mean. 
I will check back every now and then to see if anyone is around that could walk  me through it. Thanks to all those who contributed to this

---

### Post by ProjectSynergy on 2009-11-21
Just wondering , would it be better to put a request for help with this on one of the main boards , perhaps not many people view the noobs section ?

---

### Post by camaron1 on 2009-11-21
Right, I'm gonna start googling for a grub restore solution, you could start doing the same. I'll let you know if i find something.

---

### Post by telovin on 2009-11-21
Hi Project synergy,
I found athread similar to urs in this forum.. posting the link for the same. Kindly go through the same and see if it helps..

[http://art.ubuntuforums.org/showthread.php?t=1321712](http://art.ubuntuforums.org/showthread.php?t=1321712)

---

### Post by ProjectSynergy on 2009-11-21
searched around , found the answer   (pasted  below ),  here.  But as I say it may as well be in chinese for me. 
I have tried typing some of the commands as suggested but the only one that seems to respond without the '' unknown command' message is the  ls command. which lets me see I have  hd0 , hd0,4  hd0.3 , hd0,2 and hd0,1  

but when I type in  

grub rescue> root (hd0,1) 

I get unknown command. When I try the  - insmod  -  command it says no module specified 

Here is the whole answer





Since you are at the "grub rescue" prompt when you try to boot from
your internal SSD you must have grub2
installed on your SSD.

grub rescue> ls

It should list your disk and its partitions.

grub rescue> root (hd0,X)
Where X is your "/" partition (or your "/boot" partition, if it is separate).

grub rescue> ls /boot
To confirm that you have "rooted" the correct partition.
If you have, you should see your kernel, initrd, etc and the grub directory.
If not, do another "root (hd0,X)" and try again.

Once you have the correct "root (hd0,X)".

grub rescue> insmod /boot/grub/normal.mod
To go to the normal grub prompt.

grub> insmod /boot/grub/ext2.mod
To load ext2 module.

grub> ls /boot
If you cannot see the output of the previous "ls /boot" and cannot
remember the file names of the kernel and initrd.

grub> linux /boot/vmlinuz-2.6.31-13-generic root=/dev/sda3 ro
To load the kernel.

grub> initrd /boot/initrd.img-2.6.31-13-generic
To load the initrd.

grub> boot
To boot.

You should boot into your SSD install.

Once booted, you should run "grub-install /dev/sda" to ensure that
your SSD's grub.cfg is updated/corrected and you should then check it.

Then connect the HDD and run "update-grub" to add the two HDD installs
to the SSD's grub.cfg.

(I would also check that the device.map and grub.cfg disk references
correspond.)

---

### Post by camaron1 on 2009-11-21
Unless someone comes along and guides you through all the heavy console stuff this is an idea for you to consider:

Get hold of a copy of Ubuntu 9.4 which comes with the previous (tested and stable) Grub. Install this over your existing 9.10 partition (that is, besides your still existing Windows partition).

Unless you made a different partition for your home folder when you installed ubuntu all your data WITHIN  Linux will be erased so you would obviously have to make a back up of this, although i think you have already done so. If you DO have a separate home partition then your data will be safe (but you STILL have to back up, just in case).

Unless someone corrects me here this has a high chance to solve the problem but I would still wait for someone to come up with technical help.

---

### Post by twisted_steel on 2009-11-21
ProjectSynergy, when you tried to boot from the Windows 7 disc, did you try JBAlaska's suggestion from this post: [http://ubuntuforums.org/showpost.php?p=8359589&postcount=9]("http://ubuntuforums.org/showpost.php?p=8359589&postcount=9?") ?

There are also some step-by-step pictures on this page: [http://www.winvistatips.com/fix-mbr-t116.html](http://www.winvistatips.com/fix-mbr-t116.html).  They are for Vista, but the process should be close to Windows 7.  I don't have a Windows 7 DVD here right now to test.

---

### Post by Crossyboi on 2009-11-21
Ok, there seems to be alot of confusion here!! You have all your files backed up, so, as much as I hate saying it, try a complete fresh install, and have just windows 7. There must be an option to delete partitions on the windows recovery disc.

---

### Post by davidryderuk on 2009-11-21
You could try using Supergrubdisk to boot into windows, although I'm pretty sure it won't boot Karmic koala (grub2 is too new). 

Edit:

For the record I realized the following version of supergrubdisk is better for fixing the windows mbr. 

[http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9799.iso](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9799.iso)

---

### Post by ProjectSynergy on 2009-11-21
> **twisted_steel said:**
> ProjectSynergy, when you tried to boot from the Windows 7 disc, did you try JBAlaska's suggestion from this post: [http://ubuntuforums.org/showpost.php?p=8359589&postcount=9]("http://ubuntuforums.org/showpost.php?p=8359589&postcount=9?") ?

There are also some step-by-step pictures on this page: [http://www.winvistatips.com/fix-mbr-t116.html](http://www.winvistatips.com/fix-mbr-t116.html).  They are for Vista, but the process should be close to Windows 7.  I don't have a Windows 7 DVD here right now to test.

Twisted ! Youre a champion !  I did see that earlier but as it was talking about an installation disk which I don t have I thought that it didnt apply to me , but I managed to do it with the recovery cd and have got windows back ! THANK YOU !!!!!!!!!!

and thanks to Jb Alaska for posting it in the first place. 

I was supposed to go home about 3 hours ago but didnt want to leave this as is. Three good things have  come out of this , Ive learned NEVER to mess around with stuff I dont know about , 2, I have learned quite a bit about how linux works whilst researching the solution and 3, with me being here so late my boss thinks Im a conscientious , diligent and valued member of his staff, LOL it could have turned to be soooooo different. I have aged 5 years today . Thanks all of you for your help and input.

I would still like to install Ubuntu as a secondary boot choice sometime in the future, what should I do to avoid a fiasco like today ? Im still not sure why what happened happened

---

### Post by ProjectSynergy on 2009-11-21
David , I was writing the  last post when you posted yours, as I said above I found a solution to getting back to windows using the commmand prompt withing the win 7 recovery disk.  I feel much lighter now. Thank  you for your suggested solution, I would be hammering away at it had I not been able to fix it with the other solution.

I asked above what I should do , or not do , to avoid the same situation if I were to try to install ubuntu in the future?  Im guessing I still have the partition that the installation used , how would I go about fixing that ?

---

### Post by davidryderuk on 2009-11-21
I would suggest trying out wubi. 

[http://wubi-installer.org/](http://wubi-installer.org/)

Although using 9.04 for the time being is also not a bad idea, given the amount of changes to grub that are in 9.10. Personally when I first started using linux supergrubdisk was useful as I never got a windows recovery disk with my computer.

Also you might want to make sure to completely back up your computer next time, just in case.

---

### Post by steveneddy on 2009-11-21
I have some very good advice for you, the Original Poster:

Please don't attempt feats of this nature unless it is a PC that can be trashed, one that means nothing to you or your work. 

You need to learn about computers first before undertaking anything like this again.

**Take the laptop to a computer shop and get them to repair this for you.** Consider the money you spent as [stupid tax]("http://www.daveramsey.com/articles/article-list/category/lifeandmoney_stupidtax_user_generated/"), so to speak. 

I do not discourage you to learn about operating systems and installing all types of software of your "play" machine, but don not attempt this on a production machine when you obviously don't have the required knowledge to complete the task.

Now get out to that computer shop now.

---

### Post by ProjectSynergy on 2009-11-21
> **davidryderuk said:**
> I would suggest trying out wubi. 

[http://wubi-installer.org/](http://wubi-installer.org/)

Although using 9.04 for the time being is also not a bad idea, given the amount of changes to grub that are in 9.10. Personally when I first started using linux supergrubdisk was useful as I never got a windows recovery disk with my computer.

Also you might want to make sure to completely back up your computer next time, just in case.
I will look into the wubi and 9.04 solutions when I get home and try it on my own laptop. I am still very interested in ubuntu despite todays scare. I will give 9.10 a miss for now untill the grub issues are resolved. Again , thanks /
As to the back up , I always back up my own stuff , and Im sure stuff is backed up at work , but of course to go and ask the techie guys about it would have blown the cover on my f'@@ up , I was anxious to resolve it without declaring to the boss that I was a bit of a dick.
WHich I have been able to do  and for which I am eternally grateful to the folks on here who took the time to help out.

---

### Post by steveneddy on 2009-11-21
I see you got this fixed. 

This is good news.

Do not use WUBI.

---

### Post by camaron1 on 2009-11-21
> **steveneddy said:**
> I have some very good advice for you, the Original Poster:

Please don't attempt feats of this nature unless it is a PC that can be trashed, one that means nothing to you or your work. 

You need to learn about computers first before undertaking anything like this again.

**Take the laptop to a computer shop and get them to repair this for you.** Consider the money you spent as [stupid tax]("http://www.daveramsey.com/articles/article-list/category/lifeandmoney_stupidtax_user_generated/"), so to speak. 

I do not discourage you to learn about operating systems and installing all types of software of your "play" machine, but don not attempt this on a production machine when you obviously don't have the required knowledge to complete the task.

Now get out to that computer shop now.


A bit patronizing isn't?

---

### Post by twisted_steel on 2009-11-21
> **ProjectSynergy said:**
> Twisted ! Youre a champion !  I did see that earlier but as it was talking about an installation disk which I don t have I thought that it didnt apply to me , but I managed to do it with the recovery cd and have got windows back ! THANK YOU !!!!!!!!!!

and thanks to Jb Alaska for posting it in the first place. 
...


Glad you got it back up and running.  I ran into a similar situation with the family's Windows 98 computer a while back.  Someone suggested I try overwriting the MBR with 512 bytes of zeroes, which did manage to fix it.

As far as what to do in the future, playing around on your own home machine as you suggested is probably the best bet.  However, you may want to talk to your IT department and see what their policies are.  They may not have a problem with you installing something like VirtualBox (free) or VMware Workstation ($$).  This has the added benefit of not touching important things like your boot record.  You can also save snapshots of the virtual machine.  This lets you easily roll back if you screw something up.  This is also a great way to start on your home machine.  As you get more comfortable, you can move to dual booting.

---

### Post by ProjectSynergy on 2009-11-21
> **steveneddy said:**
> I have some very good advice for you, the Original Poster:

Please don't attempt feats of this nature unless it is a PC that can be trashed, one that means nothing to you or your work. 

You need to learn about computers first before undertaking anything like this again.

**Take the laptop to a computer shop and get them to repair this for you.** Consider the money you spent as [stupid tax]("http://www.daveramsey.com/articles/article-list/category/lifeandmoney_stupidtax_user_generated/"), so to speak. 

I do not discourage you to learn about operating systems and installing all types of software of your "play" machine, but don not attempt this on a production machine when you obviously don't have the required knowledge to complete the task.

Now get out to that computer shop now.
Ive been my biggest critic on here today , I recognise that I messed up . Howver , I tried nothing more than installing a OS for dual boot , the stuff I read before doing it seemed pretty straight forward , I had no idea it was so complex, and again to be less hard on myself I noticed that this seems to be an issue for other folks since the 9.10 release. Had it not a problem with the boot then I would have had another OS to learn , and from what Im hearing it seems to be a worthwhile move. You are right in that I was mad to try something unknown on a work computer, but I was frustrated by what windows was not allowing me to do , when with Xp before they changed over last week to win 7 I could at least perform the tasks I wanted. A friend recommended Ubuntu and it sounded like the solution. 
I admit to having very limited knowledge of script and the inner workings of software and that I must have given a very good impression of being a bit of a clown today , however , well...., lets just say my talents lie elsewhere:)

EDIT: just seen your advice to stay away from WUBI , why do you advise this ?

---

### Post by ProjectSynergy on 2009-11-21
> **twisted_steel said:**
> Glad you got it back up and running.  I ran into a similar situation with the family's Windows 98 computer a while back.  Someone suggested I try overwriting the MBR with 512 bytes of zeroes, which did manage to fix it.

As far as what to do in the future, playing around on your own home machine as you suggested is probably the best bet.  However, you may want to talk to your IT department and see what their policies are.  They may not have a problem with you installing something like VirtualBox (free) or VMware Workstation ($$).  This has the added benefit of not touching important things like your boot record.  You can also save snapshots of the virtual machine.  This lets you easily roll back if you screw something up.  This is also a great way to start on your home machine.  As you get more comfortable, you can move to dual booting.

Thanks for all your input Twisted. One last thing before I go. Someone above advised me to stay away from Wubi?  What do you think the reason for that advice is?

CAMARON. Big thanks to you as well , your moral support was just as valuable as the technical support :)

---

### Post by emigrant on 2009-11-21
i spent a good laughing time going through this thread. :D
anyway im happy synergy secured his job.

---

### Post by camaron1 on 2009-11-21
you're welcome mate. 

Wubi is actualy a very easy and safe way to install ubuntu. You would't want Wubi IF Ubuntu is intended to be your main OS (not a hundred percent performance in terms of speed, by default will boot into Windows). Otherwise if you want to have a look at Ubuntu in a safe way go for it.

---

### Post by mvalviar on 2009-11-21
> **Spiritof76 said:**
> Yes and it works well
If you're referring to brasero please help me make it "work well" because I can't use it to burn discs.

---

### Post by Crossyboi on 2009-11-21
Glad to see you got it back up and running!

And by the way, don't listen to those people telling you to take it somewhere to get fixed, in sure 99% of people on here agree the best method of learning is by Reading up and trial and error. Look at what you have acheieved today! And you saved a bit of money in the process.

---

### Post by oldfred on 2009-11-21
From your results.txt your install was to sdb the 4GB drive, I assume a USB key, but the grub boot was to sda and it will not boot unless the USB key is in.
Also it looks like grub found all your bootable partitions, but may have mislabeled them. Boot from sda1 labled as win7 may be your recovery partition, sda2 labeled Vista may actually be your win7. It also shows a boot for sda3?

---

### Post by steveneddy on 2009-11-21
> **camaron1 said:**
> A bit patronizing isn't?

After reading most of the preceding thread I felt the best advice would be to get that machine to a competent computer shop and have it fixed there.

He was performing, for some, an elementary process on his computer and didn't possess enough knowledge to repair it himself. He admitted that he was unskilled in this area.

I was trying to offer the advice that no one else was willing to give, to take it to a professional, which, IMHO, is sometimes the best advice.

Sometimes the best medicine is the hardest to take.

I am not afraid to point to the most obvious.

---

### Post by steveneddy on 2009-11-21
> **ProjectSynergy said:**
> Ive been my biggest critic on here today , I recognise that I messed up . Howver , I tried nothing more than installing a OS for dual boot , the stuff I read before doing it seemed pretty straight forward , I had no idea it was so complex, and again to be less hard on myself I noticed that this seems to be an issue for other folks since the 9.10 release. Had it not a problem with the boot then I would have had another OS to learn , and from what Im hearing it seems to be a worthwhile move. You are right in that I was mad to try something unknown on a work computer, but I was frustrated by what windows was not allowing me to do , when with Xp before they changed over last week to win 7 I could at least perform the tasks I wanted. A friend recommended Ubuntu and it sounded like the solution. 
I admit to having very limited knowledge of script and the inner workings of software and that I must have given a very good impression of being a bit of a clown today , however , well...., lets just say my talents lie elsewhere:)

EDIT: just seen your advice to stay away from WUBI , why do you advise this ?

Just take my advice and purchase a laptop to play around on. try this again to determine the correct steps and focus on where you failed this time.

Knowledge is a great thing and the greatest bit of knowledge is to know when to stop and take it to a pro.

I never doubted that you yourself could get this repaired, but since this was a PC for work, it was entirely possible to totally hose the system entirely, which is what brought on the advice to take to the pro.

Don't stop learning and hacking away at your new play laptop.

---

### Post by Sealbhach on 2009-11-21
> **ProjectSynergy said:**
> 
I would still like to install Ubuntu as a secondary boot choice sometime in the future, what should I do to avoid a fiasco like today ? Im still not sure why what happened happened

I would suggest to create a Live USB installation of Linux Mint (based on Ubuntu but even more user friendly). You can boot up from the USB and explore the system, without any danger of changing anything on your regular computer. You can use [Unetbootin]("http://unetbootin.sourceforge.net/") to make the USB.

.

---

### Post by MisFitt on 2009-11-21
> **steveneddy said:**
> I see you got this fixed. 

This is good news.

Do not use WUBI.
Why should he not use WUBI?
I used WUBI in my XP and learned from scratch many things Ubuntu until I gained enough confidence to try a dual-boot.
WUBI I'm sure is invaluable for those like myself who knew nothing beyond choosing and using various programs in windows,in fact I wonder if I could have taken the plunge without it(at that point).
Now I'm enjoying the learning curve that is linux,very much so,in fact I find myself perusing the absolute beginner forum when I have spare time,such as now.
WUBI rocked my world

---

### Post by steveneddy on 2009-11-21
> **MisFitt said:**
> Why should he not use WUBI?

It's a work computer.

Do it the right way and learn faster.

opinion/

Wubi sucks

/opinion

---

### Post by JBAlaska on 2009-11-22
@ProjectSynergy, I knew you could do it! sorry I had to crash last night but i'd been up for about 16 hours lol.

While I do agree that installing a second OS on the work computer without permission is probably not a good idea, When you do get that permission or a computer to play with, Don't hesitate to try the windows wubi install. It's as safe as installing any program on windoze and the worse thing that could happen is a messed up MBR, and you now know how to fix that lol(but the computer would still boot windoze).

You DO still have Ubuntu installed on that laptop, and I'm sure it could be recovered using the LiveCD, but getting windoze back up was the most important thing at the time.

So your options are, get permission to try again after backing up mission critical data...Or Go home, paint the scratches on the tank, and forget last night ever happened (John Candy, movie 1941). :-)

**P.S. There is nothing wrong with trying Ubuntu through a wubi install, but be advised, If you try to use suspend/hibernate with it it will break.**

---

