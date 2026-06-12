---
title: "HOWTO: DWL-G120 b1 external wireless card under Fiesty"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by mraudiofreak on 2007-06-01
It sounds like a lot of people are having trouble getting the DWL-G120 revision b1 usb wireless card to work. I was able to get it working fairly easily with the help of these two guides:
[ http://www.linuxforums.org/forum/361063-post1.html]("http://www.linuxforums.org/forum/361063-post1.html")
[ http://www.linuxquestions.org/questions/showthread.php?p=1170631#post1170631]("http://www.linuxquestions.org/questions/showthread.php?p=1170631#post1170631")

If you have a windows parition, that's great. Otherwise, this guide should still work. I installed the card using my windows partition, but I put the files I used on a website for those of you that don't have xp installed. These will probably work, but no guarantees. I believe you can get to the same files by clicking on the first link.
[U][B]
Step 1
[/B][/U] If possible, install the card on a Windows XP partition.

_**Step 2**_
Install ndiswrapper via synaptic. The two packages I had installed were ndiswrapper-common and ndiswrapper-utils-1.9.

_**Step 3**_
Now look in your windows partition for prisma02.inf. I did a file search for this, mine was located in /../windows/inf/prisma02.inf. Enter the directory that the file is in and run the command
```
 ndiswrapper  -i  prisma02.inf
```For me, this created the directory /etc/ndiswrapper/prisma02 which had 4 files in it: 045E:00C2.F.conf, 2001:3701.F.conf, 09AA:1000.F.conf, prisma02.inf. Some people may only have 2 files: 2001:3701.F.conf, prisma02.inf.

Note: If you don't have a windows partition, try using the files from the first link or the files I used [here]("http://mraudiofreak.googlepages.com/home"). No guarantees on these though. I suspect it would only work for the B1 revision of the card. If your not sure of your revision, check the back of your card for where it says H/W Ver.  Any feedback on if these work would be appreciated, they may even make a few other steps unnecessary.

_**Step 4**_
When you run the ndiswrapper command, it does not find 2 of the files. Add 2 copies of each of these files to the directory /etc/ndiswrapper/prisma02; one copy with all lowercase and one copy with all uppercase letters (except for the extension).  The first file is prisma02.sys (mine was in /../windows/system32/drivers/) and the second is prismapi.dll (mine was in /..windows/system32/).

The directory /etc/ndiswrapper/prisma02/ should now have the following files in it
```
dan@dan-deskbook:/etc/ndiswrapper/prisma02$ ls
045E:00C2.F.conf  2001:3701.F.conf  prisma02.sys  prismapi.dll
09AA:1000.F.conf  prisma02.inf      PRISMA02.sys  PRISMAPI.dll
```Note: Again, if you don't have a windows partition try the files I uploaded or the ones from the first link.

[U][B]Step 5
[/B][/U]Now, we need to disable the original ubuntu drivers that didn't work. To do this, open up the blacklist in gedit
```
sudo gedit /etc/modprobe.d/blacklist
```Add the following lines to the file
```

blacklist islsmusb
blacklist islsm
blacklist islsm-usb
blacklist prism54usb

```[U][B]Step 6
[/B][/U]Plug in, reboot, and you should be good to go.

---

### Post by Idura on 2007-06-03
I have a DWL-G120 b1 and when I type  ndiswrapper  -i  prisma02.inf into terminal I get an error something like "couldn't copy /etc/ndiswrapper/prisma02.inf at line 182" I can confirm I am in the right directory and I typed everything in correctly, I tried lots of times, but got the same error. I would post screenshots, but I cannot connect to the internet  on my linux partition, I tried saving the screenshots into my windows partition, but I can't find them.

When I type ndiswrapper -l to list the currently installed drivers, I get something like this "cannot find /etc/ndiswrapper/drivers"

I had trouble installing ndiswrapper because whenever I would try to install it using add/remove it would make me connect to the internet to download it, I had the CD, but it would still try to make me connect to the internet. I had to install it using terminal. It should be working because if I type ndiswrapper into terminal it does show me a list of commands for it.

I am using ubuntu AMD64-bit, I am guessing my drivers are 32-bit since my windows partition is 32bit. I looked at the d-link website and couldn't find 64-bit drivers for the DWL-G120. Do I need to get a 32-bit ubuntu in order to get my WLAN working?

---

### Post by Idura on 2007-06-04
Update, I got past my previous problems.

Here is the new problem.** I am on step 4 and when I try to paste the files into /etc/ndiswrapper/prisma02 folder it says access is denied even though I am the computer admin**, what can I do? I tried finishing the steps without the 2 files you need to rename and add to the folder, but it doesnt work :( Please someone help me!

---

### Post by mraudiofreak on 2007-06-04
You must use the command line to copy the files and us the "cp" command as the superuser.  so if you wanted to copy prisma02.sys from your current directory to /etc/ndiswrapper/prisma02 you would do this
```
sudo cp prisma02.sys /etc/ndiswrapper/prisma02/prisma02.sys
sudo cp prisma02.sys /etc/ndiswrapper/prisma02/PRISMA02.sys
```

Let me know if this works

---

### Post by Idura on 2007-06-04
Ok I copied the files you listed, but it still didnt work :(

 I didn't get 045E:00C2.F.conf and  09AA:1000.F.conf .  Can you email me these files or put them on your website so I can try it with these files, I don't know why it wouldn't create them :( if I am using the same wireless card and OS as you :(

I have the following files in the /etc/ndiswrapper/prisma02 directory: 2001:3701.F.conf , prisma02.inf , prisma02.sys , PRISMA02.sys , primsapi.dll , PRISMAPI.dll .

---

### Post by Idura on 2007-06-04
I'd like to add that on step 3 it adds 3 files instead of 2. The extra file it adds is prisma02.sys

---

### Post by mraudiofreak on 2007-06-05
what does
```
ndiswrapper -l
```
output?

also, try having the card unplugged, rebooting, starting gnome, and after everything is loaded plug the card in. If the power light comes on on the modem, you should be ok. Click on the network manager icon to view available networks.

---

### Post by Idura on 2007-06-05
"prisma02 driver installed
2001:3701 present (alternate driver prism54)"

thats what i get with ndiswrapper -l

I tried that, but no lights ever come on :(, it works just great on my windows xp partition so the adapter does work.

---

### Post by Idura on 2007-06-05
MrAudio are you using 64-bit FF ubuntu? That may be why it is not working for me?

---

### Post by mraudiofreak on 2007-06-08
I'm not great at this kind of stuff, but it sounds like ubuntu is still trying to run the prism54 driver. Make sure you did step 5 (check the file to make sure you saved the changes), and maybe even add an extra line in the blacklist named prism54. I am not running 64-bit ubuntu, but I don't think that this would be the cause of the problem.
There should be other items in the blacklist too, otherwise you edited the wrong file.
good luck

---

