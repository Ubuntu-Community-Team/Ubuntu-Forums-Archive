---
title: "Wubi and Ubuntu i386 installed on desktop but Wubi keeps downloading amd64. Why??"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by saresu on 2011-01-25
I installed ubuntu-10.10-desktop-i386 but Wubi keeps downloading the amd64.

I put both on desktop but it doesnt work. I tried open the ubuntu file with Wubi (Is this what people call Argument?), but it didnt work either.

PS> my Windows is Vista.

Please help me.

---

### Post by migs73 on 2011-01-25
Let me get this right;

On your computer you have... 

Windows Vista (32 or 64bit??)
Ubuntu 10.10 i386 (32bit)

and are trying to install Ubuntu using Wubi, and it keeps trying to install the 64bit (amd64) version?

If the Vista is 64bit that might explain why it downloads the 64bit Wubi.

---

### Post by [Snc] on 2011-01-25
> **saresu said:**
> I installed ubuntu-10.10-desktop-i386 but Wubi keeps downloading the amd64.

I put both on desktop but it doesnt work. I tried open the ubuntu file with Wubi (Is this what people call Argument?), but it didnt work either.

PS> my Windows is Vista.

Please help me.

In Vista, maybe you should *run* WUBI *as administrator*...

---

### Post by saresu on 2011-01-25
My vista is 32 bits and i always run as administrator

---

### Post by [Snc] on 2011-01-25
> **saresu said:**
> My vista is 32 bits and i always run as administrator

So you have the ISO downloaded from ubuntu.com and WUBI?

---

### Post by oldos2er on 2011-01-25
[https://wiki.ubuntu.com/WubiGuide#Why is the AMD64 version of Ubuntu getting downloaded and installed?](https://wiki.ubuntu.com/WubiGuide#Why is the AMD64 version of Ubuntu getting downloaded and installed?)

---

### Post by Frogs Hair on 2011-01-25
Wubi installs Ubuntu 64bit by default , but it is possible to the 32bit version . See the guide.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by saresu on 2011-01-25
There is nothing in the guide.

---

### Post by migs73 on 2011-01-25
If you already have 32bit Ubuntu installed, I take it you have a liveCD?

If so just pop the CD in during a windows session and install Wubi that way (I think it still works from the liveCD!!), I would hope it would use the ISO on the disk and not download the 64bit one.

BTW; If you are migrating from Windows to Ubuntu, why do you want a Wubi install? Wubi is really only an evaluation tool, and if you get rid of windows, your Wubi install goes with it!!.

---

### Post by oldos2er on 2011-01-25
From the guide: "Why is the AMD64 version of Ubuntu getting downloaded and installed?
The machine you are trying to install Ubuntu on may be 64 bit. The AMD64 installation is appropriate for all 64 bit architectures, no matter if they are AMD or Intel.

Can I force Wubi to download and install a 32 bit version of Ubuntu?
Yes: either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument."

---

### Post by migs73 on 2011-01-26
> **oldos2er said:**
> 

Can I force Wubi to download and install a 32 bit version of Ubuntu?
Yes: either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument."

I have installed Wubi once, and I don't recall any place where I could insert a --32bit argument. Having a look at the documentation, I don't see anywhere you could put it either.

I think the OP requires more explicit instructions on how to force the 32bit iso, the guide says to predownload the 32bit and place it in the same folder as Wubi.exe

> I put both on desktop but it doesnt work.

The OP says he has the 32bit file on his desktop along with Wubi (both therefore in the same folder) and when running Wubi he still got 64 bit.

Does he need to put both in another folder on his desktop to force the 32bit install? Can anyone explain to them (and me!!) where the --32bit argument should be placed?

---

### Post by Rubi1200 on 2011-01-26
As I understand it, there are 2 options.

Download the 32bit ISO and then place the wubi.exe and ISO in the same folder, then run.

Second option is to right-click on the wubi.exe and create a Shortcut.

Then, right-click on the shortcut > Properties

In the target field and comments field add --32bit so that it looks like this:

"C:\Documents and Settings\your_name\Desktop\wubi.exe" --32bit

Notice the space after the last quotation marks.

I believe this should work.

---

### Post by bcbc on 2011-01-26
You place both the .iso and wubi.exe in the same folder.  Then you create a shortcut to wubi.exe (in the same folder). Right click, properties on the shortcut and you can add --32bit to the command line.

However, I believe you don't need to force --32bit in this case (from my recollection, but I might be wrong). As long as the wubi.exe and the .iso are the exact same release it should use it. It's easy to mix up the releases: 10.04.1 wubi.exe cannot install 10.10 or even 10.04, it can only install 10.04.1.

When you run wubi.exe it shows you the version (top centre). Also if you look in the logfile (in the %temp% directory) it might explain further why it is rejecting the .iso.

EDIT: Rubi1200 beat me to it ;)

---

### Post by migs73 on 2011-01-26
> **Rubi1200 said:**
> As I understand it, there are 2 options.

Download the 32bit ISO and then place the wubi.exe and ISO in the same folder, then run.

Second option is to right-click on the wubi.exe and create a Shortcut.

Then, right-click on the shortcut > Properties

In the target field and comments field add --32bit so that it looks like this:

"C:\Documents and Settings\your_name\Desktop\wubi.exe" --32bit

Notice the space after the last quotation marks.

I believe this should work.

Now in defence of the OP (and me!) that is not what the guide tells you. That is helpful and concise, maybe the guide should be updated?

This does not explain why the Wubi on his desktop with a 32bit iso there still used the 64bit one? Do you need to create another folder and put them both in it? 
Desktop not really a folder?????????

---

### Post by saresu on 2011-01-26
> **migs73 said:**
> If you already have 32bit Ubuntu installed, I take it you have a liveCD?

If so just pop the CD in during a windows session and install Wubi that way (I think it still works from the liveCD!!), I would hope it would use the ISO on the disk and not download the 64bit one.

BTW; If you are migrating from Windows to Ubuntu, why do you want a Wubi install? Wubi is really only an evaluation tool, and if you get rid of windows, your Wubi install goes with it!!.
Hum... this is what ive been thinking... I wasnt sure whether use Wubi or install Linux from livecd.

If I install from livecd, there is no way that it gonna be installed amd64? right? Can I be sure of it? Because if yes, I think I will install from livecd instead of using Wubi.

Im too unexperienced in both ways, Vista or Linux. sorry

---

### Post by saresu on 2011-01-26
> **migs73 said:**
> I have installed Wubi once, and I don't recall any place where I could insert a --32bit argument. Having a look at the documentation, I don't see anywhere you could put it either.

I think the OP requires more explicit instructions on how to force the 32bit iso, the guide says to predownload the 32bit and place it in the same folder as Wubi.exe



The OP says he has the 32bit file on his desktop along with Wubi (both therefore in the same folder) and when running Wubi he still got 64 bit.

Does he need to put both in another folder on his desktop to force the 32bit install? Can anyone explain to them (and me!!) where the --32bit argument should be placed?
Man! Thank you! Finally somebody understood why I made this post, understood what exactly is going on... Im too novice in Linux stuff even to make a good post.

People keep replying my post with link to Wubi Guide, and Ive been trying to tell people that all this stuff I know. All this stuff Ive alredy checked on Wubi Documentation. 

If there was information enough on Wubi Guide, it wouldnt make any sense to make this post.

But for some reason its seems that people are ignoring the fact that THERE IS NO FURTHER INFORMATION ABOUT THIS ISSUE (FORCING WUBI INSTALL I386). THE INSTRUCTIONS ON WUBI GUIDE IS NOT WORKING!!!.

Thank you again MIGS73 . U've helped a lot!

---

### Post by saresu on 2011-01-26
> **Rubi1200 said:**
> As I understand it, there are 2 options.

Download the 32bit ISO and then place the wubi.exe and ISO in the same folder, then run.

Second option is to right-click on the wubi.exe and create a Shortcut.

Then, right-click on the shortcut > Properties

In the target field and comments field add --32bit so that it looks like this:

"C:\Documents and Settings\your_name\Desktop\wubi.exe" --32bit

Notice the space after the last quotation marks.

I believe this should work.
[COLOR=Blue][B]Rubi1200

Thats is a brand new information for me.

U got it my brother!!

It works!!!!!! (I MEAN, UR SECOND OPTION WORKED!!!!!!!! *making shortcut and stuff...*)

Im so happy now with you reply but Im so **** (not with anyone of you folks) wondering why this is not written on Wubi Guide!

Please, let people know about this stuff to update Wubi Guide with ur new information.[/B][/COLOR]

[COLOR=Blue][B]
ITS WORKING!!!!!!!!!!!!!!!!!!


*(Interesting thing. What is happening here is: Wubi is downloading ubuntu-10.04.1-desktop-i386.iso.torrent... So, in the end, I didnt need to install any i386.iso... its just install wubi and follow ur instruction, no 32bit ubuntu installation required)*

U got it man!!

[/B][/COLOR]
**[COLOR=Blue]Thank you very very much!![/COLOR]**

---

### Post by Rubi1200 on 2011-01-26
You are more than welcome saresu :-)

I am really please this finally worked for you, despite the frustrations along the way.

I will try and find out if there is a way to add this information to the Wubi Guide for you (and others).

Please mark this thread Solved using the Thread Tools near the top of the page so that other users can also find a working solution.

Thanks.

---

### Post by saresu on 2011-01-26
> **Rubi1200 said:**
> You are more than welcome saresu :-)

I am really please this finally worked for you, despite the frustrations along the way.

I will try and find out if there is a way to add this information to the Wubi Guide for you (and others).

Please mark this thread Solved using the Thread Tools near the top of the page so that other users can also find a working solution.

Thanks.
Sure man!

Thank you again!

---

### Post by bcbc on 2011-01-26
> **saresu said:**
> [COLOR=Blue]*(Interesting thing. What is happening here is: Wubi is downloading ubuntu-10.04.1-desktop-i386.iso.torrent... So, in the end, I didnt need to install any i386.iso... its just install wubi and follow ur instruction, no 32bit ubuntu installation required)*[/COLOR]
If that's the case then you probably had a mismatching .iso (it just rejected the one on the desktop) and it had nothing to do with the --32bit option.

You said in the first post that you downloaded 10.10 on to the desktop, so it seems you are running the 10.04.1 wubi.exe with the 10.10 .iso.

You can check this by looking in (or posting) the logfile: %temp%/wubi-10.04.1-rev190.log

EDIT: however this doesn't change the fact that the wubi guide is missing this important detail on how to supply the --32bit option.

---

### Post by bcbc on 2011-01-26
PS Saresu, it's important to avoid updating packages grub-pc and grub-common with 10.04.1. See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for details.

---

### Post by saresu on 2011-01-27
> **bcbc said:**
> If that's the case then you probably had a mismatching .iso (it just rejected the one on the desktop) and it had nothing to do with the --32bit option.

You said in the first post that you downloaded 10.10 on to the desktop, so it seems you are running the 10.04.1 wubi.exe with the 10.10 .iso.

You can check this by looking in (or posting) the logfile: %temp%/wubi-10.04.1-rev190.log

EDIT: however this doesn't change the fact that the wubi guide is missing this important detail on how to supply the --32bit option.
so why there is this mismatch? Ive just downloaded the latest wubi available and the latest ubuntu 32 bits available... (I thought... )since wubi is suppose to work only with ubuntu i thought that the way I downloaded both would be enough... but surely in linux world, things can't be that easy, right? something must be complicated..hahaha
[COLOR=Red]

[/COLOR]sorry, I didnt understand this?: [COLOR=Red]*"You can check this by looking in (or posting) the logfile: %temp%/wubi-10.04.1-rev190.log"*[/COLOR]

---

### Post by bcbc on 2011-01-27
> **saresu said:**
> so why there is this mismatch? Ive just downloaded the latest wubi available and the latest ubuntu 32 bits available... (I thought... )since wubi is suppose to work only with ubuntu i thought that the way I downloaded both would be enough... but surely in linux world, things can't be that easy, right? something must be complicated..hahaha
[COLOR=Red]

[/COLOR]sorry, I didnt understand this?: [COLOR=Red]*"You can check this by looking in (or posting) the logfile: %temp%/wubi-10.04.1-rev190.log"*[/COLOR]

When you go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) you can choose either 10.10 (default) or 10.04.1. If you then click the [Windows installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") tab there is no choice - it doesn't tell you what version it is - but it downloads 10.04.1.

If you wanted 10.10 wubi.exe you have to get it here: [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

There are some significant differences in the wubi implementation of different releases, so I guess that's why they've made it version specific.

The logfile is in the %temp% folder (temp is a session variable that contains the path of the folder). So you can click START, Run, %temp% - or open an explorer window and enter %temp% in the address bar. Or just open notepad, click open and enter "%temp%\wubi-10.04.1-rev190.log"

---

### Post by saresu on 2011-01-27
> **bcbc said:**
> PS Saresu, it's important to avoid updating packages grub-pc and grub-common with 10.04.1. See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for details.
Ive bookmarked ur wubi Megathread.

Ive been seeing lots of "Advanced" information about this problem, but so far, I still didnt understand how to avoid doing this *"updating packages grub-pc and grub-common with 10.04.1"*. 
[COLOR=Red]
**How can I know if im about to do this, or not?**[/COLOR]

When I finished all the process to install ubuntu, the OS started and appeared a screen showing a list of several programs asking for upgrade (or st like that) and I just click "yes" and updated all.

Im so lost now that I even dont know what exactly I suppose to ask about this... haha!!

But everything is cool, Ive changed Ubuntu to Dream Studio to work with Ardour.

---

### Post by bcbc on 2011-01-27
> **saresu said:**
> Ive bookmarked ur wubi Megathread.

Ive been seeing lots of "Advanced" information about this problem, but so far, I still didnt understand how to avoid doing this *"updating packages grub-pc and grub-common with 10.04.1"*. 
[COLOR=Red]
**How can I know if im about to do this, or not?**[/COLOR]

When I finished all the process to install ubuntu, the OS started and appeared a screen showing a list of several programs asking for upgrade (or st like that) and I just click "yes" and updated all.

Im so lost now that I even dont know what exactly I suppose to ask about this... haha!!

But everything is cool, Ive changed Ubuntu to Dream Studio to work with Ardour.
If you ran all the available updates, then you've already updated grub-pc and grub-common. 
Two scenarios:
1. You installed Ubuntu to C:. This could result in a problem booting Ubuntu (immediately or in the future).
2. You installed to a 'drive' (partition) other than C:. You were prompted whether to continue without installing Grub. If you check the box and click Forward, you're ok. If you just click forward, and then select the checkboxes it offers, then you stop your computer from booting. (Plus you could end up with the problem from 1: later as well).

The 'screen that popped up' is the Update Manager. It lists all packages that have updates. Some are listed as Security updates, others as Recommended. You should review the updates before accepting them (especially the Recommended ones). If you see grub-pc and grub-common listed, uncheck them.

I admit that when I do a fresh install I don't bother reviewing 200+ updates... and grub updates are buried near the bottom of the list. But since the devs have refused to respond to the problem or pull the grub updates, we can only warn users such as yourself who have problems installing (doesn't always help ;) ) - otherwise we have to help users after the problem has occurred.

---

### Post by saresu on 2011-01-27
> **bcbc said:**
> If you ran all the available updates, then you've already updated grub-pc and grub-common. 
Two scenarios:
1. You installed Ubuntu to C:. This could result in a problem booting Ubuntu (immediately or in the future).
2. You installed to a 'drive' (partition) other than C:. You were prompted whether to continue without installing Grub. If you check the box and click Forward, you're ok. If you just click forward, and then select the checkboxes it offers, then you stop your computer from booting. (Plus you could end up with the problem from 1: later as well).

The 'screen that popped up' is the Update Manager. It lists all packages that have updates. Some are listed as Security updates, others as Recommended. You should review the updates before accepting them (especially the Recommended ones). If you see grub-pc and grub-common listed, uncheck them.

I admit that when I do a fresh install I don't bother reviewing 200+ updates... and grub updates are buried near the bottom of the list. But since the devs have refused to respond to the problem or pull the grub updates, we can only warn users such as yourself who have problems installing (doesn't always help ;) ) - otherwise we have to help users after the problem has occurred.
Wow! Keeping with Wubi isn't good anyway.

I changed my mind now... I dont need my Vista anyway, so If I install from live cd and let my laptop only Ubuntu, I dont need to take care of this kind of stuff?? Is that correct?

Im wondering If I let my laptop only with Ubuntu, will there be new kinds of problems and stuff?

Cause if yes, I will conclude that to use Linux I will need nerves to dont freak out.

But, really... thank you very much for ur time explaining all this stuffs.

---

### Post by bcbc on 2011-01-27
> **saresu said:**
> Wow! Keeping with Wubi isn't good anyway.

I changed my mind now... I dont need my Vista anyway, so If I install from live cd and let my laptop only Ubuntu, I dont need to take care of this kind of stuff?? Is that correct?

Im wondering If I let my laptop only with Ubuntu, will there be new kinds of problems and stuff?

Cause if yes, I will conclude that to use Linux I will need nerves to dont freak out.

But, really... thank you very much for ur time explaining all this stuffs.
Why rush to dump Windows? You can do a regular dual boot instead until you are sure everything works all right: split your windows partition using the Vista disk manager then install Ubuntu in the free space. I would be careful using 10.10 though ([the installer has some issues]("http://ubuntuforums.org/showthread.php?t=1622388")) - safer to stick with 10.04.1 instead.

---

### Post by saresu on 2011-01-27
> **bcbc said:**
> Why rush to dump Windows? You can do a regular dual boot instead until you are sure everything works all right: split your windows partition using the Vista disk manager then install Ubuntu in the free space. I would be careful using 10.10 though ([the installer has some issues]("http://ubuntuforums.org/showthread.php?t=1622388")) - safer to stick with 10.04.1 instead.
Its seems it will never end... 

First:
Before I chose Wubi, I was aiming to do this Dual Boot, Ive Studied all the Ubuntu documentation and even burn a Iso GParted Live CD cause... (this is hilarious) ... my Vista is Japanese, (Im brazilian, cant read kanji), even though, I tried the Vista disk manager but It was inacessible to make any changes, (for some reason that I coudnt and still cant understand, even after reading several Threads about this problem). Im using always as Administrator, I dont get whats Is happening. *[COLOR=Red]Thats why I chose Wubi cuz I thought this would be the best and easy way[/COLOR]*

Second:
I chose deliberately Ubuntu 32bit. The purpose of this is: to use Ardour. And Ardour coudnt be installed on a Ubuntu 64bit normally on my laptop. I tried to install Ardour but at Ubuntu Software Centre appeared this: ("sorry, 'Ardour GTK2' is not available for this type of computer (amd64)"). **[COLOR=Red](but I did with Wubi installer, not from the partitioning way)[/COLOR]**

[COLOR=Black]**Does it make difference if my Ubuntu 64bit is Wubi or DualBoot in this specific case?**** If the Ubuntu is 64bit DualBoot, Can Ardour be installed?**[/COLOR]

Since I have 2Gb Ram, from the recommendations I received from Ardour forum, I dont need a "64bit"
[B][COLOR=Red]
So, Do I have to make a post like this on Ardour forum:?[/COLOR][/B]
[I]
"How to force install Ardour in a Laptop Intel Core 2 Duo 2.00 Ghz with[COLOR=Red]** 2.00 Gb**[/COLOR] DualBootVista Ubuntu 64bit?"[/I]

I dont know what else to do.

---

### Post by bcbc on 2011-01-27
Well, you have an issue - partitioning vista. The solution isn't to completely wipe the computer and install Ubuntu. If Wubi is working for you then just keep it - when you have used Ubuntu enough and know that you don't want to use Windows, then you can wipe it. Take it slow.

You can always migrate your Wubi to a normal partition dual boot later without losing settings or data.

---

### Post by saresu on 2011-01-27
> **bcbc said:**
> Well, you have an issue - partitioning vista. The solution isn't to completely wipe the computer and install Ubuntu. If Wubi is working for you then just keep it - when you have used Ubuntu enough and know that you don't want to use Windows, then you can wipe it. Take it slow.

You can always migrate your Wubi to a normal partition dual boot later without losing settings or data.
Even If I say that Im sure that I dont want vista, do you think I might be wrong? Why the solution is not wipe the computer and put linux? Since Ive already updated packages grub-pc and grub-commom, this means that i will have trouble now or in the future, right? Having the chance to lose all my work files when this grup-cd trouble comes.

---

### Post by saresu on 2011-01-27
Wait a second!?

"PS Saresu, it's important to avoid updating packages grub-pc and grub-common with 10.04.1."

But the Ubuntu Im using is 10.10! it still affects? So U mentioned for both 10.10 and 10.04.1 Right?

---

### Post by bcbc on 2011-01-27
> **saresu said:**
> Wait a second!?

"PS Saresu, it's important to avoid updating packages grub-pc and grub-common with 10.04.1."

But the Ubuntu Im using is 10.10! it still affects? So U mentioned for both 10.10 and 10.04.1 Right?

> **saresu said:**
> [COLOR=Blue][B]
ITS WORKING!!!!!!!!!!!!!!!!!!


*(Interesting thing. What is happening here is: Wubi is downloading ubuntu-10.04.1-desktop-i386.iso.torrent... *

[/B][/COLOR]
That's 10.04.1

---

### Post by Rubi1200 on 2011-01-28
Some new information regarding the original purpose of this thread.

@ saresu and migs73; the Wubi Guide has now been updated with the --32bit argument explained more clearly. 
> **Can I force Wubi to download and install a 32 bit version of Ubuntu?**

 Yes: either [pre-download the appropriate 32 bit ISO manually]("https://wiki.ubuntu.com/WubiGuide#ManuallyDownloadISO") and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument. 
To  modify arguments, right-click Wubi.exe and select "Create Shortcut".  Then right-click the shortcut, select Properties, and modify the Target  line, for example: "C:\Documents and  Settings\<user>\Desktop\wubi.exe" --32bit 


---

### Post by saresu on 2011-01-29
> **Rubi1200 said:**
> Some new information regarding the original purpose of this thread.

@ saresu and migs73; the Wubi Guide has now been updated with the --32bit argument explained more clearly.
Thank you Rubi1200!

---

