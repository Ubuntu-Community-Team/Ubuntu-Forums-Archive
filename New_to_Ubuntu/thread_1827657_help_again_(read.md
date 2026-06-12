---
title: "help again (read"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by edwardpatch1 on 2011-08-18
I downloaded ubuntu.iso i burnt the image i opened the wubi.exe and i choosed second link on installer then i choosed 10 gb then i put username in and that then i installed it and restarted it and i choose the ubuntu operating system not windows 7 then it came up as
[COLOR="Red"][U][B]Try (hd0,0):NTFS5:No Wubildr
Try (hd0,1) invalid or null
Try (hd0,2) invalid or null
Try (hd0,3) invalid or null
Error while reading mbr of drive (hd01)
Try (fd0): invalid or null
Error:cannot find GRLDR in all devices. Press CTRL+Alt+Del[/B][/U][/COLOR]

---

### Post by edwardpatch1 on 2011-08-18
plz help :)

---

### Post by overdrank on 2011-08-18
Hi and welcome, please be patient and do not bump so quickly. Once a day (24 hr) is polite.
:)

---

### Post by edwardpatch1 on 2011-08-18
ok sorry

---

### Post by androssofer on 2011-08-18
> **edwardpatch1 said:**
> I downloaded ubuntu.iso i burnt the image i opened the wubi.exe and i choosed second link on installer then i choosed 10 gb then i put username in and that then i installed it and restarted it and i choose the ubuntu operating system not windows 7 then it came up as
[COLOR="Red"][U][B]Try (hd0,0):NTFS5:No Wubildr
Try (hd0,1) invalid or null
Try (hd0,2) invalid or null
Try (hd0,3) invalid or null
Error while reading mbr of drive (hd01)
Try (fd0): invalid or null
Error:cannot find GRLDR in all devices. Press CTRL+Alt+Del[/B][/U][/COLOR]

looked into it and is a few ways to fix it... some look complex (some might say too complex for those using wubi (as then tend to be newbies trying out linux for the first time)) anyway. in [this]("http://ubuntuforums.org/showthread.php?t=798283") thread. i found this info to fix it via windows: 

***note: i dont use windows anymore(and haven't for a while), nor is it my solution, so if u get stuck etc, i wont b much help. so try at ur own risk... :-)

> 
Here's how I did it (in WIndows 7 though).
I went to control panel and searched the word "partition". A result "Create and format hard disk partition" under Administrative tools will show up.
Click on the "Create and format hard disk partition". The disk management dialogue box will open.
Look below.
You will see "System Reserved", ( C, ( D and/or any other partition that you might have with their respective letters.
Right click on the "System Reserved", select "Change Drive letters and paths". In the new dialogue box, click "add" and then "OK" on the new dialogue box that appears. You should receive a notification similar to the one when you plug in a pendrive.
Now, go to the directory where you installed Ubuntu/Kubuntu, search for and copy the file wubildr and then paste it in the new partition that should have appeared in My Computer. (Do not do anything else to the new partition as it contains system files and might damage your Windows.)
After that, open disk management again and then remove the drive letter from "System Reserved". (You will get a warning about removing the drive letter bu do it, nothing will happen - at least nothing happened on my computer).
Then restart the computer. Ubuntu/Kubuntu should load normally without the "ntfs no wubildr" message.
P.S do it at your own risk, I am not responsible for any damage that might occur.

---

### Post by westie457 on 2011-08-18
> **edwardpatch1 said:**
> I downloaded ubuntu.iso i burnt the image i opened the wubi.exe and i choosed second link on installer then i choosed 10 gb then i put username in and that then i installed it and restarted it and i choose the ubuntu operating system not windows 7 then it came up as
Try (hd0,0):NTFS5:No Wubildr
Try (hd0,1) invalid or null
Try (hd0,2) invalid or null
Try (hd0,3) invalid or null
Error while reading mbr of drive (hd01)
Try (fd0): invalid or null
Error:cannot find GRLDR in all devices. Press CTRL+Alt+Del

Hello.

It has been a while since I installed Ubuntu as a Wubi install.

Try these steps:- 

1 Boot into Windows

2 Go to Control-Panel > Add/Remove programs. Here you are looking for Ubuntu, click on uninstall and okay. Wait for this to finish, it will take a while.

3 When the uninstall completes reboot into Windows to remove any remaining files that were in use.

4 Defrag Windows twice to free up space for the Ubuntu directory.

5 Open a Command Prompt window and type in ```
chkdsk /f
```
A warning that you 'cannot run chkdsk while the file-system is mounted' will show and ask if you want to run it at the next boot. type 'Y' exit the command prompt and reboot.

6 Let the 'chkdsk' run fixing any errors on the hard drive.

7 Put your LiveCD in the tray and click on the install icon.

8 At the 'where to install' screen select 'Inside Windows', click on next/forward.

9 In the next screen DO NOT ACCEPT the defaults as Windows will be left with no space. Adjust the space for the install to 15GB - 20GB. This will be plenty. Again click 'forward'. The install goes ahead.

10 If you get a prompt for where to install Grub accept the defaults. Wait for everything to finish. You cannot hurry this.

11 Reboot your computer. You should be given a choice to start Windows or Ubuntu.

Now this is the bit where my memory is struggling. I cannot remember that if choosing Ubuntu will bring up a Grub menu asking you to choose which Operating System to start. If it does this default is Ubuntu and Windows will be at the bottom of the list.

Hope this helpful to you and also hope that my memory of the steps is correct.

My last Wubi install was 3 years ago using the above instructions. All went well for me.

---

### Post by edwardpatch1 on 2011-08-18
> **westie457 said:**
> Hello.

It has been a while since I installed Ubuntu as a Wubi install.

Try these steps:- 

1 Boot into Windows

2 Go to Control-Panel > Add/Remove programs. Here you are looking for Ubuntu, click on uninstall and okay. Wait for this to finish, it will take a while.

3 When the uninstall completes reboot into Windows to remove any remaining files that were in use.

4 Defrag Windows twice to free up space for the Ubuntu directory.

5 Open a Command Prompt window and type in ```
chkdsk /f
```
A warning that you 'cannot run chkdsk while the file-system is mounted' will show and ask if you want to run it at the next boot. type 'Y' exit the command prompt and reboot.

6 Let the 'chkdsk' run fixing any errors on the hard drive.

7 Put your LiveCD in the tray and click on the install icon.

8 At the 'where to install' screen select 'Inside Windows', click on next/forward.

9 In the next screen DO NOT ACCEPT the defaults as Windows will be left with no space. Adjust the space for the install to 15GB - 20GB. This will be plenty. Again click 'forward'. The install goes ahead.

10 If you get a prompt for where to install Grub accept the defaults. Wait for everything to finish. You cannot hurry this.

11 Reboot your computer. You should be given a choice to start Windows or Ubuntu.

Now this is the bit where my memory is struggling. I cannot remember that if choosing Ubuntu will bring up a Grub menu asking you to choose which Operating System to start. If it does this default is Ubuntu and Windows will be at the bottom of the list.

Hope this helpful to you and also hope that my memory of the steps is correct.

My last Wubi install was 3 years ago using the above instructions. All went well for me.
Yea but how do i do that can u help me with a program called team veiwer to do that bit ??

---

### Post by Idefix82 on 2011-08-18
> **edwardpatch1 said:**
> Yea but how do i do that can u help me with a program called team veiwer to do that bit ??

You know, one of the tricky things about asking for help is that you actually have to read the answers.

---

### Post by edwardpatch1 on 2011-08-18
yea im only 12 and i dont want to mess my windows up

---

### Post by androssofer on 2011-08-18
> **edwardpatch1 said:**
> yea im only 12 and i dont want to mess my windows up

if u put the CD in when windows running, and select "install inside windows" then you can uninstall it from windows using the "Programs" program in control panel as you would any other windows program. its highly unlikely to mess your windows up... its only if u boot from the ubuntu CD and install outside windows that it cud do that.

so just hav ur browser up and swtich between it and the install wizard, and u can follow the instructions as you go... :-)

---

### Post by edwardpatch1 on 2011-08-18
ok i will try to follow i already have more than 15gb

---

### Post by edwardpatch1 on 2011-08-18
I am doing it now

---

### Post by edwardpatch1 on 2011-08-18
Try (hd0,0):NTFS5:No Wubildr
Try (hd0,1) invalid or null
Try (hd0,2) invalid or null
Try (hd0,3) invalid or null
Error while reading mbr of drive (hd01)
Try (fd0): invalid or null
Error:cannot find GRLDR in all devices. Press CTRL+Alt+Del
Its doing it again i done what u said and its not working so what do i do now

---

### Post by androssofer on 2011-08-18
> **edwardpatch1 said:**
> Try (hd0,0):NTFS5:No Wubildr
Try (hd0,1) invalid or null
Try (hd0,2) invalid or null
Try (hd0,3) invalid or null
Error while reading mbr of drive (hd01)
Try (fd0): invalid or null
Error:cannot find GRLDR in all devices. Press CTRL+Alt+Del
Its doing it again i done what u said and its not working so what do i do now

have you done this at all? :


> Here's how I did it (in WIndows 7 though).
I went to control panel and searched the word "partition". A result "Create and format hard disk partition" under Administrative tools will show up.
Click on the "Create and format hard disk partition". The disk management dialogue box will open.
Look below.
You will see "System Reserved", ( C, ( D and/or any other partition that you might have with their respective letters.
Right click on the "System Reserved", select "Change Drive letters and paths". In the new dialogue box, click "add" and then "OK" on the new dialogue box that appears. You should receive a notification similar to the one when you plug in a pendrive.
Now, go to the directory where you installed Ubuntu/Kubuntu, search for and copy the file wubildr and then paste it in the new partition that should have appeared in My Computer. (Do not do anything else to the new partition as it contains system files and might damage your Windows.)
After that, open disk management again and then remove the drive letter from "System Reserved". (You will get a warning about removing the drive letter bu do it, nothing will happen - at least nothing happened on my computer).
Then restart the computer. Ubuntu/Kubuntu should load normally without the "ntfs no wubildr" message.
P.S do it at your own risk, I am not responsible for any damage that might occur. 

---

### Post by edwardpatch1 on 2011-08-18
> **androssofer said:**
> have you done this at all? :
nopeb i will try now

---

### Post by gr8ansh4u on 2011-08-18
one way to fix it is that by installing it in system drive itself...then it'll work fine...same problem was happening with me too...i installed it in system drive and it worked fine..


and wenever u face problems just uninstall it from control panel...


no damage happens to windows...

---

### Post by bcbc on 2011-08-18
It appears there is only one valid partition (hd0,0) that grub4dos can read (old partition numbering used by grub4dos that is used to boot Wubi installs) and this partition corresponds to /dev/sda1 or (hd0,1) under grub2.

The others are invalid or null. The (hd01) MBR invalid is either a typo (should be (hd1) which would mean grub4dos cannot read this drive - GPT?) or something new I've never seen before.

So start off by explaining what type of computer you have, brand model, what sort of drives you have etc. 

The usual cause of the problem you are seeing is:
1 No C:\wubildr file (easy to check)
2 A drive > 137GB with an older bios and the wubildr file is physically placed over the 137GB BIOS read limit.
3 Perhaps some excessive fragmentation

---

### Post by edwardpatch1 on 2011-08-18
> **bcbc said:**
> It appears there is only one valid partition (hd0,0) that grub4dos can read (old partition numbering used by grub4dos that is used to boot Wubi installs) and this partition corresponds to /dev/sda1 or (hd0,1) under grub2.

The others are invalid or null. The (hd01) MBR invalid is either a typo (should be (hd1) which would mean grub4dos cannot read this drive - GPT?) or something new I've never seen before.

So start off by explaining what type of computer you have, brand model, what sort of drives you have etc. 

The usual cause of the problem you are seeing is:
1 No C:\wubildr file (easy to check)
2 A drive > 137GB with an older bios and the wubildr file is physically placed over the 137GB BIOS read limit.
3 Perhaps some excessive fragmentation
its a custom built one processer AMD
graphics card navida
windows 7
and thats it really

---

### Post by bcbc on 2011-08-18
> **edwardpatch1 said:**
> its a custom built one processer AMD
graphics card navida
windows 7
and thats it really

What about the drives? How many physical drives? How many 'drives' (partitions) does Windows see? How big?

Maybe a snapshot from the windows disk management console (click Start, enter "disk management" )

---

### Post by scruffyeagle on 2011-08-18
> **edwardpatch1 said:**
> its a custom built one processer AMD
graphics card navida
windows 7
and thats it really

Unfortunately, that's not all there is to it. At 12 years old, you're trying to do something that stumps a large portion of the adults. (That's why MS Windows is still dominant in the market.) But, knowledge is the key. You've made a good choice by coming here seeking assistance and guidance, but you need to accept that it's YOUR level of knowledge that is the key. It will take work on your part, to gain that knowledge. It might not happen quickly. But, if you set your goal and pester it relentlessly, indefinitely, for however long it takes (a year? 3 years?) it CAN happen. And then, you'll have something you can be quite proud of.

The first thing you need to do, toward achieving your goal is to get focused. When one of the people who are kind enough to assist a stranger (you, for example) asks a specific question, focus down on being able to answer that one question. At the current moment, bcbc is asking you for details about your hard drive - how big it is (number of GB), and what kind (IDE or SATA?). You can find this information by using Windows. There's a system information utility, a device manager, and a disk management utility. These are available through the "Control Panel", and each other. Successfully answering this request for information will be a step toward your goal.

---

