---
title: "IS there a way to set the boot order??"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-09
folks, I have a pc with windows 7, 64 bit, as well as the latest Ubuntu 11.04. Is there a way to set Windows 7 as a default instead of Ubuntu as the default? I would like to boot into Windows, then reboot into Linux afterwords. Maybe there is a utility to do this?
 
Please let me know,
 
Thanks

---

### Post by jtarin on 2011-05-09
Yes there is.
[A good Grub read from a community member.]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by TheNerdAL on 2011-05-09
Maybe this will help: [http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm](http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm)

---

### Post by TAspr on 2011-05-09
I think that is a BIOS setting and not necessarily the actual Grub Menu order.

---

### Post by Not unique on 2011-05-09
Won't  **- SYSTEM-PREFERENCES-LOGIN SCREEN SETTINGS-**  sort it?
At the bottom tab there is a choice of OS's.
Or in Ubuntu 11.04 -PREFERENCES-LOGIN SCREEN SETTINGS- ?

---

### Post by jtarin on 2011-05-09
> **TAspr said:**
> I think that is a BIOS setting and not necessarily the actual Grub Menu order.If the operating systems are on different physical disk that would be a consideration. I believe he is speaking of the Grub boot screen order.

---

### Post by Not unique on 2011-05-09
That's always worked for me or am I misunderstanding?
Are the OS's on two separate disks?

---

### Post by alphacrucis2 on 2011-05-09
If on Natty then grub submenus are used for old kernels, so you can't use a simple count to select the default boot item. Another fine post by drs205 explains how to account for submenus when setting your grub default:

[URL="http://ubuntuforums.org/showthread.php?p=10720316"]http://ubuntuforums.org/showthread.php?p=10720316
[/URL]

---

### Post by 73ckn797 on 2011-05-09
Start-Up-Manager will allow default boot order in Grub to be changed. It is available in Synaptic Package Manager.

---

### Post by TAspr on 2011-05-10
> **Not unique said:**
> Won't  **- SYSTEM-PREFERENCES-LOGIN SCREEN SETTINGS-**  sort it?
At the bottom tab there is a choice of OS's.
Or in Ubuntu 11.04 -PREFERENCES-LOGIN SCREEN SETTINGS- ?


ok, this is what I got...  I do not see preferences other than what I am looking at..

What am I supposed to be looking for?

---

### Post by TAspr on 2011-05-10
> **jtarin said:**
> If the operating systems are on different physical disk that would be a consideration. I believe he is speaking of the Grub boot screen order.


Correct!

---

### Post by TAspr on 2011-05-10
> **Not unique said:**
> That's always worked for me or am I misunderstanding?
Are the OS's on two separate disks?


No, it is all on one disk.

---

### Post by jtarin on 2011-05-10
[Take a look.]("http://kubuntuforums.net/forums/index.php?topic=3107328.0")

---

### Post by TAspr on 2011-05-10
> **jtarin said:**
> [Take a look.]("http://kubuntuforums.net/forums/index.php?topic=3107328.0")


Yes, my friend, but how do you even get to the Grub menu?

---

### Post by jtarin on 2011-05-10
> **TAspr said:**
> Yes, my friend, but how do you even get to the Grub menu?
What part of ```
"Opening /etc/default/grub as root
If your file manager supports it, open the file manager, navigate to /etc/default/grub, right-click on the file, Actions, Edit as Root."
```is not clear. There are more instructions but you will need to know how to open and close a file manager, file editor and terminal and you must know how to do these as "root". This is something that can mess up your system if you don't know what your doing. So insure this is something you want to do and then proceed with the given instructions.

---

### Post by TAspr on 2011-05-10
> **jtarin said:**
> What part of ```
"Opening /etc/default/grub as root
If your file manager supports it, open the file manager, navigate to /etc/default/grub, right-click on the file, Actions, Edit as Root."
```is not clear. There are more instructions but you will need to know how to open and close a file manager, file editor and terminal and you must know how to do these as "root". This is something that can mess up your system if you don't know what your doing. So insure this is something you want to do and then proceed with the given instructions.


I am a newbie, sorry about that.  Would it bother you to show me pictures... I am a bit older and can understand pictures much better.  When you said the words in between CODE, is it as easy as going through the directories?

---

### Post by alphacrucis2 on 2011-05-10
> **73ckn797 said:**
> Start-Up-Manager will allow default boot order in Grub to be changed. It is available in Synaptic Package Manager.


It doesn't work properly under Natty as it doesn't make allowance for the submenus Natty uses in grub.

---

### Post by jtarin on 2011-05-10
> **TAspr said:**
> I am a newbie, sorry about that.  Would it bother you to show me pictures... I am a bit older and can understand pictures much better.  When you said the words in between CODE, is it as easy as going through the directories?[Is this the screen your talking about?]("http://www.n00bsonubuntu.net/wp-content/uploads/ubuntu-grub2-boot-menu.jpg") List the entries you see there?

---

### Post by TAspr on 2011-05-11
> **jtarin said:**
> [Is this the screen your talking about?]("http://www.n00bsonubuntu.net/wp-content/uploads/ubuntu-grub2-boot-menu.jpg") List the entries you see there?


Yes, exactly, but I also have a Windows 7 option as well.  How do I move the Windows 7 to the top of the list (well, at least for now)

---

### Post by kurok on 2011-05-11
no idea weather it works for natty or not but it worked like a charm in 10.04 [http://ubuntuforums.org/showthread.php?t=1664134&highlight=change+boot+order]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=change+boot+order")

---

### Post by TAspr on 2011-05-11
> **kurok said:**
> no idea weather it works for natty or not but it worked like a charm in 10.04 [http://ubuntuforums.org/showthread.php?t=1664134&highlight=change+boot+order](http://ubuntuforums.org/showthread.php?t=1664134&highlight=change+boot+order)


Fantastic! I will check on it and let you know how it went...  (I hope I do not screw this up..lol)

I do have a question though, under the instructions for the previous version, when it mentiones;

**[COLOR=Navy][SIZE=3]1. Installation[/SIZE][/COLOR]** Synaptic:
[LIST]
[*]Start Synaptic
System > Administration > Synaptic Package Manager
[/LIST]
Where do you find this?  I do not have an option.

---

### Post by grahammechanical on 2011-05-11
You can download Grub Customizer through the Ubuntu Software Centre as well as through Synaptic Package Manager. Just search for grub-customizer. I recommend this utility. I should be a standard part of every Ubuntu install, in my opinion.

I am using 11.04 Ubuntu/Unity user interface. If you are then, click the shut down icon and select System Settings and look for either the software centre or synaptic. The Ubuntu Software Centre is on the Launcher (left side panel).

Regards.

---

### Post by TAspr on 2011-05-11
> **grahammechanical said:**
> You can download Grub Customizer through the Ubuntu Software Centre as well as through Synaptic Package Manager. Just search for grub-customizer. I recommend this utility. I should be a standard part of every Ubuntu install, in my opinion.

I am using 11.04 Ubuntu/Unity user interface. If you are then, click the shut down icon and select System Settings and look for either the software centre or synaptic. The Ubuntu Software Centre is on the Launcher (left side panel).

Regards.

Thank You, I will try that.  Thanks so much.

---

### Post by KL_72_TR on 2011-05-11
I think this is what you are looking for: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by TAspr on 2011-05-11
> **KL_72_TR said:**
> I think this is what you are looking for: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Mr KL, that may be the ticket.  I will try it and let you guys know.

Thanks a bunch, I really, really appreciate it.  As a newbie, all things, going from the windows era, things are quite different, but I do like the 11.04 version allot.  Now, if only I could add things from the applications or shortcuts bar to the launcher...

---

### Post by TAspr on 2011-05-11
Using the Start Up Manager, I was unable to get the boot order to change.  It looked exactly like I left it.  What gives?

---

### Post by jtarin on 2011-05-11
What gives? 11.04.....new version of Grub 1.99. Your going to have to learn it at the same time we do......or wait.All Grub tools are not up to date with this yet.

---

### Post by TAspr on 2011-05-12
I ran the "start up manager", and after rebooting, the pc defaulted to Windows 7, although it did keep the structure of the options in order.  It just now boots to windows 7, which is the way I wanted it to be.
 
I may get rid of Windows 7 eventually, but there are too many programs that I use that rely on it for now.
 
Thanks a bunch for all your help in this matter.

---

### Post by 73ckn797 on 2011-05-13
> **TAspr said:**
> I ran the "start up manager", and after rebooting, the pc defaulted to Windows 7, although it did keep the structure of the options in order.  It just now boots to windows 7, which is the way I wanted it to be.
 
I may get rid of Windows 7 eventually, but there are too many programs that I use that rely on it for now.
 
Thanks a bunch for all your help in this matter.

Glad to hear things worked out. I knew Startup Manager would accomplish your goal.

---

### Post by 73ckn797 on 2011-05-13
> **KL_72_TR said:**
> I think this is what you are looking for: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

This does not apply to Grub2.

---

### Post by jtarin on 2011-05-13
Learn something new everyday......never paid much attention to startup manager......as I thought it was only concerned with processes and not boot configuration. I'll have to take a look at that in more detail.
[Here's documentation]("https://help.ubuntu.com/community/StartUpManager") if anyone is curious.

---

