---
title: "Dual Boot"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by MichaelIan on 2010-03-31
I have had to Re-install Windows XP (surprise!)
In doing so I lost my ability to get access to Ubuntu.
In trying to follow instructions on manually creating a Grub loader from a Cd version of Ubuntu I lost all ability to start up my computer.
In desperation I then used the CD to install Ubuntu.
I am obviously not competent to make decisions on partitioning so I let the installation proceed without altering the proposed partitions, which created further partitions in the Linux part of my hard drive.  This re-installed Grub giving me access to two versions of Ubuntu and Windows.

I would very much appreciate a detailed description (obviously I am fairly incompetent in following instructions given for more experienced users) as to how I may get rid of the second version of Ubuntu while correcting the partitions on my drive and readjusting the Grub loader.

---

### Post by yetiman64 on 2010-03-31
If you have 2 installs of ubuntu (which version ?), and xp and you want to repair the system to have only one install of ubuntu. 1st check you can successfully boot all 3 systems to their desktops (sounds like you might be able to but don't use any linux boots marked recovery or single user though- at this stage). 

Important: Backup all your data from XP 1st off the machine if you can, as you'll be dealing with repartitioning and repairs using gparted from ubuntu or a live cd , and its possible to lose everything if anything goes wrong. [COLOR=Blue]Partition work is dangerous to installed systems, but usually not to the underlying hardware itself.[/COLOR]

This sounds like it can be repaired if done carefully. Do the above checks and backing up, then post back .

---

### Post by MichaelIan on 2010-03-31
Thank you for your very prompt reply.
Both editions of UBUNTU are 9.1
The second installed from a magazine DVD is slightly younger than my normal updated version.
I can access either UBUNTU systems or Windows from Grub at start-up.
Due to my problems I have been backing up all my important documents to a second hard drive.
I would not mind reformatting the Linux Partition and then reinstalling UBUNTU.  I fear loosing access to the windows partition in the process.  
Last time trying to regain access by using fixmbr (to get into Windows) did not work.

---

### Post by yetiman64 on 2010-03-31
OK this sounds good so far.

I assume you're woking from either Ubuntu. If you're not in Ubuntu (either 1) let me know 1st up -ok. You'll need gparted installed so put in terminal.

> sudo apt-get install gpartedWhen installed open from system > partition editor.

When you can see your drive partitions take a screenshot using the Printscreen key on the keyboard. Dont have anything open you don't want seen publicly though. Attach the screenshot to your next post so we can work from there. [COLOR=Blue]Edit: see post #9 re filesize limits.[/COLOR]

You'll be removing 1 or more Linux partitions, so now backup any data you may want to keep from Ubuntu (best to do both installs).

You won't be needing to do anymore reinstalls if this works ok. and both OSes should still work. However if the wrong ubuntu is removed you may loose grub again, but thats OK as it can be fixed from a live cd without reinstalling.

IF this works Windows won't be affected.

---

### Post by MichaelIan on 2010-04-01
Thank you again for your trouble.
At the moment I am using windows but when dealing with Ubuntu I will be logged in to the latest installation.
I have had some difficulty in reducing the size of the screenshot to 100kb and retaining a clear picture.
I will attach it to this post and then send another post including the GRUB screen on startup.

---

### Post by MichaelIan on 2010-04-01
I hope I have managed to attach the screenshot to my last reply and that you will be able to see it.  I cropped it to make the most of the 100k.
I now intend to attach a photo of the GRUB screen.
When making alterations, following your suggestions, I will be using the UBUNTU version at the top of the list.  This is the latest installation to my computer and the version which created the GRUB loader currently in use.
I would point out that my problems arose while trying to use a live version of UBUNTU from a DVD to create a GRUB loader.  :(

---

### Post by yetiman64 on 2010-04-01
Thanks  Yes I got the earlier screenshot and and now the grub boot screen. I'm currently tied up in another thread and will get onto working through this soon. I actually saw the first post of yours @ 1 minute old :), but was in the middle of some researching.  Nev

Edit: FYI the picture quality is perfect for this task.

---

### Post by MichaelIan on 2010-04-01
I am very concious and appreciative of your attention to my problem.  I am sure you realise that although it is in the background it is not preventing me from using my computer.  Please do not feel pressured into devoting time to this if you have more pressing problems. (how to relax over a holiday week end? :D)

---

### Post by yetiman64 on 2010-04-01
Thats OK Michael, 

 I'm currently considering wiping the whole backend out and rebuilding with the cd if you agree. I realize that its a bit intimidating for you after whats happened, but trust me in the long run it will make life much easier and quicker to do. It is very messed up at the moment and difficult to even save 1 of the Ubuntu installs without leaving an equally strange layout at the end.


Edit: Theres actually a very easy fix: 

1. Boot on live cd.

2. Open gparted   (Remember if at any time you think you've done wrong here -- use the undo button.)

3. Right click on all backend partitions and delete (including the extended one. Note:-[COLOR=DarkGreen][COLOR=Black]gparted won't let you delete the extended partition till all logical partitions within are 1st deleted.[/COLOR][/COLOR]) When this is completed nothing but XP and unallocated space should show ,with XP at the start of the drive in /dev/sda1.[COLOR=DarkGreen][COLOR=Black] (To others viewing this check comments at post #13  [http://ubuntuforums.org/showpost.php?p=9065861&postcount=13](http://ubuntuforums.org/showpost.php?p=9065861&postcount=13))

4. Click on apply and let gparted clean out the backend totally. When its finished close gparted.

4a.  <WARNING> DO NOT shut the machine down at this stage go straight to step 5. as all of grubs files required for the bootloader are now gone. 

5. On the live cds desktop is the install icon, use it to do an automatic install as you did before.


When the install is done you should have both XP and a new Ubuntu accessible from a newly installed grub boot menu.

Nev.

Please remember IF this is a fix for you, to use the thread tools and mark as solved. Otherwise just repost and continue.  :)

[/COLOR][/COLOR][COLOR=Blue]Please disregard my previous comments re filesize. The filesizes are listed for various filetypes with the upload tool. My previous info from another thread may have only been a suggestion for the consideration of dial up users. [COLOR=Black]
[/COLOR][/COLOR]

---

### Post by yetiman64 on 2010-04-02
[COLOR=Blue]<useless post content removed>[COLOR=Black]
[/COLOR] [/COLOR]

---

### Post by MichaelIan on 2010-04-02
Many thanks for input.
Have printed off the instructions and will try them.
Sounds "SIMPLE".
Will get back when succeeded!!   :D  <- I hope
New post may not be for some time due to commitments.

---

### Post by yetiman64 on 2010-04-02
I just re-editted in a waning , maybe after you posted, check the instructions again Hope all goes well.

---

### Post by MichaelIan on 2010-04-02
:D
Managed to delete the various partitions and have now got a clean Two Operating system computer.
It was a bit experimental with the deleting.  I did not realise until I started to get rid of the various partitions that they had to be deleted in order highest number first and also that the Swap partitions had to be marked as "Swap Off" before they could be got rid of. 
Very many thanks for the continued close support it was greatly appreciated.
Michael
PS: was looking for the link to close this thread but can not recognise it.t.

---

### Post by yetiman64 on 2010-04-02
Good to hear its worked, =D>
cheers,   Nev

> PS: was looking for the link to close this thread but can not recognise it.t.At the top of the page use Thread tools drop down menu and choose thread solved.

---

