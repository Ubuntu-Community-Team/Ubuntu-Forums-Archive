---
title: "SAMBA Edgy icons dissapearing?"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Robvdl on 2006-10-27
I have just installed a clean install of Edgy Eft on two machines, and am experiencing the same problem on both machines with SAMBA (I think it's SAMBA related, or maybe Nautilus related).

I have been using SAMBA on Dapper Drake prior to this in the exact same way, and I didn't experience this on Dapper, networking with SAMBA worked great in Dapper.

If I go to "Places->Network Servers" and attempt to browse the Windows network, some of the computer and workgroup icons appear as blank icons (like a blank sheet of paper), double clicking on them won't work and produces errors similar to this:

Couldn't display "smb:///mshome".

The location is not a folder.

If I hit "Refresh" in Nautilus, the icon will change from the blank sheet of paper icon, to the normal icon, and then double clicking on it works like it should.

I have noticed if I press refresh a few times, the icon changes on and off between the blank icon and the proper icon, if the icon is a blank icon, I cannot double click on it as it will produce the error.

Very strange issue, I can work around it so it's not too great of a concern, just wondering if anyone has noticed this too, or knows of a workaround, maybe it's a bug, maybe it's something to do with a timing issue, but my network is pretty fast, it only has a few PC's on it.

Any hints? should I report it as a bug, and under what section would it need to be reported, would it be SAMBA, or Nautilus related, or something completely different?

The attached screenshot shows some of the icons as blank icons and some as proper icons, it also shows the error when you double click on one of these blank icons.

---

### Post by son_goku on 2006-10-27
same error here.

> 
Couldn't display "smb:///mshome".

The location is not a folder

someone plase help.

---

### Post by Furry_Fighter_20x66 on 2006-10-28
I am seeing it too. I can use smbclient though to FTP my way to my windows shares.

---

### Post by sbolte on 2006-10-28
same problem...does anyone have a fix?

sb

---

### Post by son_goku on 2006-10-28
are we the only ones with this problem?

---

### Post by wilberfan on 2006-10-28
Here's one more guy having the identical problem...  My Windows XP box can see my Ubuntu box fine, btw...

:-k

---

### Post by NZ-Wanderer on 2006-10-28
Add me to the list too..

My problem is a little more complex than yours, but part of it is the network thing..

Mind you, when I keep clicking like you do till the folder comes up in network, it then tells me it cannot load the files from my network..

Here is my thread if you interested.

[http://www.ubuntuforums.org/showthread.php?t=286839](http://www.ubuntuforums.org/showthread.php?t=286839)

---

### Post by compuguy1088 on 2006-10-29
Same here, having the same problem, thoug originally I thought it was connected to the fact that I'm using a wireless connection, but I guess not..

---

### Post by graz848 on 2006-10-29
Exactly the same problem. Open "Windows network", then "mshome" has the blank icon... then after a few void click it becomes right and sometimes it works pretty good... but very very slowly! Using Dapper never had this problem, and samba worked pretty good and fast. I hope someone will find a solution. BYe

---

### Post by zgornel on 2006-10-29
I have a Icon of the Windows Server I wish to connect on desktop. This is not a fix but might help. Go to ~/Desktop and create a file with the name :smb-"workgroup_name"-"server name" (e.g. mine is smb-workgroup-mathlon). In the file write:
[Desktop Entry]
Encoding=UTF-8
Name=*server name*
Type=Link
URL=smb://*IP or server name*/
Icon=gnome-fs-server
I'll try to get a fix for the Places Menu and Windows Network

---

### Post by navlelo on 2006-10-29
I have the same problem as you guys.

I'm glad I found this thread, because I have spent several hours in vain trying to figure this out. It never occured to me to click on the refresh button. I'm a Lunux newbie trying for the first time to install Lunux and Samba, and I've run into all these problems because I installed Edgy instead og Dapper. It's somehow good to know that my problems aren't entirely caused by ignorance and stupidity... :rolleyes: 

There are other problems with Samba and WINS. Here is a thread that also helped me:
[http://www.ubuntuforums.org/showthread.php?t=288022](http://www.ubuntuforums.org/showthread.php?t=288022)

I obviously have no clue as to what causes all these problems.

---

### Post by stanna on 2006-10-30
im also having the same problem, my cheap way around it was to refresh a few times or sometimes wait for the icon to magicaly appear (but that never happened). so i refreshed until it worked then just bookmarked them in nautilus. should work for awhile, but is still a minor annoyance.

---

### Post by zgornel on 2006-10-30
Problem solved: I changed the name of the workgroup so that both Linux and Windows machines share the same workgroup name. In dapper this was not the case.

---

### Post by DimitrisC on 2006-10-30
I have the same problem. At first i thought that this was due to the fact that i was accessing the network via wifi but this was not the case.  So i tried the dapper live cd and it worked fine. I then uninstalled edgy and tried the edgy live cd and the problem came up again.  I had some more issues with edgy so is back to dapper for me.  I guess LTS next to dapper's name meant something afterall :-)

---

### Post by bigken on 2006-10-30
yep I also have the same problem have to click reload several time to show
 all the work stations :-k

---

### Post by dmizer on 2006-10-30
try mounting with cifs instead of nautilus.  i've found nautilus to be fairly unreliable when dealing with samba shares.

i just wrote up a very detailed howto which includes directions on how to mount with unicode support. here: [http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

---

### Post by wilberfan on 2006-10-30
[COLOR="Red"][Major Edit]   I'm full of penguin poo.   The post below was regarding my 32-bit box--NOT the 64bit box...    I installed Kubuntu on the AMD64 *and I still have the same problem.*

D'0h![/COLOR]


Just in case this adds anything for anyone who might be experienced enough to work on this problem (certainly not me at this point!), I just discovered something:

I loaded the KDE desktop (Kubuntu) onto my Gnome (Ubuntu) system, and I can connect almost instantly to my XP box!  (I also loaded the Xubuntu desktop, but haven't tried to do any network connecting from there yet.)

Would this suggest that this problem is more of a gnome or nautilus problem??

I'm just guessin' at this point, obviously.  Maybe I should shut up before I say sumthin' stoopid?  (It might already be too late!)

---

### Post by Robvdl on 2006-10-30
> **zgornel said:**
> Problem solved: I changed the name of the workgroup so that both Linux and Windows machines share the same workgroup name. In dapper this was not the case.

Changing the workgroup in both Win XP and Edgy doesn't fix it for me, still get blank icons, I usually change it in two places:

"System->Administration->Shared Folders", "General Properties" tab in Edgy, this reflects to the same setting found in /etc/samba/smb.conf

Another setting, this is most likely less known, because I found this by chance by browsing through gconf-editor, run the following program:

gconf-editor

collapse "system", then click on "smb", change the workgroup in here to your workgroup. This has the effect of when you open "Network Servers", showing the computers in your workgroup directly in the first window, without having to double click on your workgroup first. It also has the effect, of when you log into a computer on your workgroup, the login window has your workgroup in the workgroup edit box by default, instead of just the default "WORKGROUP", saves you having to type your own workgroup every time ;-)

However, it still doesn't fix the problem, this get the blank icons, just thought someone might be interested in that so called "hidden setting" I discovered - this works in Dapper too.

---

### Post by navlelo on 2006-10-30
> **zgornel said:**
> Problem solved: I changed the name of the workgroup so that both Linux and Windows machines share the same workgroup name. In dapper this was not the case.
Doesn't work for me. I've been very careful keeping every name identical all the way.

Has anybody reported this bug apart from complaining here?

---

### Post by stanna on 2006-10-30
i changed the workgroups to match and it didnt make any difference, but im happy enough with the bookmarks in nautilus. should do me fine until this can be worked out.

---

### Post by dmizer on 2006-10-30
nautilus is, at best, a poor choice to use for mounting samba shares.

your icons are not showing up because nautilus does not "mount" the shares.  nautilus has to download your share names and file names every time you open it.  this is why you have slow response times and why your icons don't appear correctly.  it simply doesn't work well.  seriously ... my advice here is to simply not use it.  use the link i gave above to mount your samba shares, and all your woes will disappear.

---

### Post by Robvdl on 2006-10-30
> **navlelo said:**
> Doesn't work for me. I've been very careful keeping every name identical all the way.

Has anybody reported this bug apart from complaining here?

No, not quite sure what to file it under and how I would word it just yet, is it a Nautilus bug or a Samba bug? I might file it when I get some time later, if nobody else has done so already that is.

I actually knew about this bug when I was running Edgy beta and release candidate, I should have filed it then, but wrongly assumed it may get fixed when Edgy was released, I should have filed it then.

Same goes with the small foot bug in Nautilus ([http://ubuntuforums.org/showthread.php?t=207592](http://ubuntuforums.org/showthread.php?t=207592)), I thought it was so obvious I assumed it was bound to get fixed for the final release, but somehow didn't, surely someone must have filed the small foot in nautilus bug by now though I assume?

There's also another bug that I had a bogus "Floppy 1" under computer, which points to "/" as well as the proper "Floppy Drive" icon which points to the correct place. I filed this bug ages ago, but no reply yet :-(

---

### Post by navlelo on 2006-10-30
> **Robvdl said:**
> No, not quite sure what to file it under and how I would word it just yet, is it a Nautilus bug or a Samba bug? I might file it when I get some time later, if nobody else has done so already that is.
Well, rather you than me as I have only three days of Linux experience. According to dmizer it's a Nautilus problem.

---

### Post by dmizer on 2006-10-31
had some problems with the howto i've just fixed.  it may look daunting, but really it's only a few lines of command line code which can very nearly all be simply copied and pasted into the terminal.

---

### Post by zgornel on 2006-10-31
> **dmizer said:**
> had some problems with the howto i've just fixed.  it may look daunting, but really it's only a few lines of command line code which can very nearly all be simply copied and pasted into the terminal. Or a little script :D

---

### Post by dmizer on 2006-10-31
> **zgornel said:**
> Or a little script :D
which would work fine except for the fact that i would have no way of determining server passwords and netbios names.  this particular fix needs a human touch.

edit: just for you, i took a look at it.  if i wrote it up as a script, it would be necessary for you to be even more involved.

---

### Post by sorrender on 2006-10-31
Here the very same problem. I hope it gets solved soon, because I find it very intuitive to mount shares using nautilus (and it worked like a charm in ubuntu 6.06):KS

---

### Post by dmizer on 2006-10-31
> **sorrender said:**
> Here the very same problem. I hope it gets solved soon, because I find it very intuitive to mount shares using nautilus (and it worked like a charm in ubuntu 6.06):KS

okay ... i'll try this one more time.

if you mount with fstab, you only have to do it ONCE.  then your settings stay the same with every upgrade and every update.

your reaction times with downloads will double, and you won't have to wait for the files to cashe.  you'll have previews of your images and files just like as if they were on your local hard drive.

you'll never have to type your user name and password in, and it will be mounted automatically and correctly every time you reboot.

and ... you'll also have a nice icon on your desktop for it ... just like nautilus makes.

why wait around for an unreliable nautilus when you can spend about 10 or 15 minutes and never have to worry about it again?

---

### Post by zgornel on 2006-10-31
> **dmizer said:**
> okay ... i'll try this one more time.

if you mount with fstab, you only have to do it ONCE.  then your settings stay the same with every upgrade and every update.

your reaction times with downloads will double, and you won't have to wait for the files to cashe.  you'll have previews of your images and files just like as if they were on your local hard drive.

you'll never have to type your user name and password in, and it will be mounted automatically and correctly every time you reboot.

and ... you'll also have a nice icon on your desktop for it ... just like nautilus makes.

why wait around for an unreliable nautilus when you can spend about 10 or 15 minutes and never have to worry about it again?
Actually, mounting the share it's the only right way to do it. The nautilus trick is a half-measure and it proves it's flaws. dmizer is right.

---

### Post by wilberfan on 2006-10-31
I definitely want to try this, but I'm curious about something:   I have two machines, and don't file share THAT often--if I do the "permanent" setup and the other machine is _not_ on, will it bring things to a crashing halt?

---

### Post by dmizer on 2006-10-31
> **wilberfan said:**
> I have two machines, and don't file share THAT often--if I do the "permanent" setup and the other machine is _not_ on, will it bring things to a crashing halt?

no, if the machine you are trying to connect to is not on, the mount will simply be ignored.  worst that will happen is that you'll find an error (couldn't mount /server/share) in your dmesg.  much the same thing as what happens when you boot and there is no cd in the cdrom drive.

---

### Post by dfad1469 on 2006-11-05
Well, I understand your method under fstab. My problem is that I have a laptop that moves between several networks. I would like Nautilus to work correctly so that I don't have to constantly correct my fstab and then reboot. 

I would like to see this filed as a bug so those of us that would like it fixed can follow it.

---

### Post by dmizer on 2006-11-06
you can add all the samba mounts you want into fstab.  if the network is not there, it will simply not mount.

then if you move, just:
```
sudo mount -a
```
and your changed network results in a changed icon on your desktop ... without rebooting.

nautilus never has been, and most likely never will be good at mounting samba no matter how many bugs are filed.  and if a bug is filed, it will not receive priority because there are other, better methods of achiving the same results.

nautilus is not the way to skin this cat.  even when it does mount, response is slow, packets are dropped, it floods the network.  nautilus is just sloppy with samba shares.  it's great for other network activity like ftp and scp, but samba ... nope.

---

### Post by bigken on 2006-11-11
Well just did a feisty distro upgrade and the problem has gone take warning I only did the upgrade because I was going to reformat my laptop but as it goes I have K U & X desktops purring along very nicely :cool:

---

### Post by mjezell on 2006-11-13
> **dmizer said:**
> nautilus is, at best, a poor choice to use for mounting samba shares.

your icons are not showing up because nautilus does not "mount" the shares.  nautilus has to download your share names and file names every time you open it.  this is why you have slow response times and why your icons don't appear correctly.  it simply doesn't work well.  seriously ... my advice here is to simply not use it.  use the link i gave above to mount your samba shares, and all your woes will disappear.

That still doesn't answer the question of why nautilus has worked in Dapper and Breezy without this problem.  I have been running samba for several years on Ubuntu and with edgy I have this problem.

---

### Post by mjezell on 2006-11-13
> **dmizer said:**
> you can add all the samba mounts you want into fstab.  if the network is not there, it will simply not mount.

then if you move, just:
```
sudo mount -a
```
and your changed network results in a changed icon on your desktop ... without rebooting.

nautilus never has been, and most likely never will be good at mounting samba no matter how many bugs are filed.  and if a bug is filed, it will not receive priority because there are other, better methods of achiving the same results.

nautilus is not the way to skin this cat.  even when it does mount, response is slow, packets are dropped, it floods the network.  nautilus is just sloppy with samba shares.  it's great for other network activity like ftp and scp, but samba ... nope.

Some of us that use Ubuntu, are not particularly coding gurus and have come to Ubuntu for it's simplicity.  We are from the GUI generation and like our systems to work from the window.  You may not like nautilus in this situation but for some of us it has worked well for years and we would like it to work the same in edgy.

---

### Post by dmizer on 2006-11-14
i am not a coding guru.  i came to linux less than a year ago.  before then, i'd been slurping gui from microsoft for about a decade.

i know nothing about scripting, and my sum total of programing experience ammounts to a semester of pascal some eons ago.

the only reason i found cifs to begin with is that i have been having these kind of problems since breezy.  i'm currently using dapper, and i've yet to upgrade to edgy.  this problem is not unique to edgy.

---

### Post by Norradj on 2006-11-14
Ther are even more problems with SMB in Edgy. In previous Dapper and Breezy (and maybe Hoary, I cant remember) you could easily play songs from the network share with the Nautilus solution, now you can't. I don't care if its slow (not too bad, not worse than windows), the Nautilus solution has been very intiutive.

---

### Post by dmizer on 2006-11-16
just because you weren't experiencing them in breezy and dapper doesn't mean they didn't exist.  just like i'm sure you'll argue with the 70 some odd percent of the people who've upgraded to edgy and are connecting to their shares with no problems.

linux may be more difficult to use in some situations when when compared to windows, but one of the great things about linux is that when there is a problem (unlike windows) you don't have to put up with it.  you can fix it or find an alternative solution.  if linux worked like windows, then it would have the more serious security and vulnerability issues as windows.

if you are dead set on completely avoiding the command line, my guess is that you're probably better of with a different distribution like mepis.  that or go back to the familiarity of windows if you like.

---

### Post by sabredog on 2006-11-17
> **zgornel said:**
> I have a Icon of the Windows Server I wish to connect on desktop. This is not a fix but might help. Go to ~/Desktop and create a file with the name :smb-"workgroup_name"-"server name" (e.g. mine is smb-workgroup-mathlon). In the file write:
[Desktop Entry]
Encoding=UTF-8
Name=*server name*
Type=Link
URL=smb://*IP or server name*/
Icon=gnome-fs-server
I'll try to get a fix for the Places Menu and Windows Network
How is the best method to navigate to ~/Desktop?

All the problems in this thread I have as well and frankly I am considering reinstalling Dapper or going back to my Duron with Dapper installed.

Love to get help on creating an icon on the desktop as this will assist greatly.

cheers and thanks

---

### Post by ryan on 2006-11-17
> **sabredog said:**
> How is the best method to navigate to ~/Desktop?

All the problems in this thread I have as well and frankly I am considering reinstalling Dapper or going back to my Duron with Dapper installed.

Love to get help on creating an icon on the desktop as this will assist greatly.

cheers and thanks

I had something similar happen witha Dapper > Edgy upgrade. On a windows network I could get the normal computer icon on around 10% of the machines only. I also had some icons for certain files types not work on my desktop and I think it might be a "mime" issue in part. IDK for sure still looking into it.

---

### Post by nathanhill on 2006-11-24
Just found mention of this bug on LaunchPad.

[https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277](https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277)

Looks like a patch has been made upstream to Feisty.
Pretty soon, then, this should be backported to Edgy...

Too bad it has taken such a looooooong time though...

-N

---

### Post by vanshark on 2006-12-11
I used the fix from here [http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons](http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons) and all is back to normal

Jim

---

### Post by wilberfan on 2006-12-12
> **vanshark said:**
> I used the fix from here [http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons](http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons) and all is back to normal

Hmmm....  Didn't work for me.  Konqueror still works really nicely (even in gnome)--but Nautilus?   Not yet!

---

### Post by NZ-Wanderer on 2006-12-12
Well I fixed it in a round about way...

I installed Kubuntu Dapper, then used the upgrade manager to upgrade to Kubuntu Edgy...
Everything works perfectly, no sign of the icon bug that I experienced in Ubuntu Edgy..

Probably not important, but thought I would mention it anyway :)

---

### Post by victorbrca on 2006-12-19
Does anyone knows when they are going to implement the patch and how we are gonna be able to install it  ??? (noob here)

Will it fix executing files over the network as well?

[Launch Pad]("https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277")

> 
Re: Windows Network entries use a text icon instead of a computer one from Sebastien Bacher at 2006-12-18 11:30:40 UTC

fixed package uploaded to edgy-proposed



Vic.

---

### Post by celem on 2006-12-21
I have the same problem. With Dapper I had no problem accessing my Wondows shares but on my two Ububtu Edgy systems they both exhibit the same problem, much as you describe.

---

### Post by Raphaff on 2008-01-14
So about the icon i don't know the problem ... 
But u should check ur samba config file ! 

Wich is @ /etc/samba/smb.conf  i think   

sudo nano /etc/samba/smb.conf

make your changes 
Workgroup = rafahome 
Server string = %h  ubuntuserver

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

Example :

[share1]
comment = share1
path = /home/raphaff/share1
browseable = yes
public = yes 
read only = no
writable = yes
path = /home/raphaff/share1

ctrl + x
save modified buffer? yes
testparm /etc/samba/smb.conf

just to check for syntax errors
u now probably  have a public share with write permissions @ ~/raphaff/share1

after testparming or saving the file  sudo /etc/init.d/samba restart 
i hope this helps
I ended up here trying to find how to make a safe share if anyone of you can help i will appreciate !
:)

---

