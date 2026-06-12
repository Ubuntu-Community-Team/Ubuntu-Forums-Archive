---
title: "64bit questions?????"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by 9000cse on 2011-03-01
Hi all, a few questions, I could do with answering.

1.  In XP, or anything MS. using the black box as it where. you can change drives, & folders by - c:\>CD Windows and or C:\> D:\ return
So, how do you do this within Linex/UBUNTU ?  under UBUNTU, Mounting the drvs is not a problem.  Opening folders is not a problem.  But in UBUNTU, black box, it is.

2, I managed to get a windows program working by coping the folder 'racer30' from a NTFS drive to a Linex drive, then getting into the folder racer30 and changing the permissions on the reacer30.exe file then running Wine.  Works OK, as far as I have tested.  But, within the program there is an area where it shows a gif, jpg photo, under XP that is. In Linex, it does not.  Photos are where they should be and the path proves this, but no photo shows up. Why?

3.  The Mail system within UBUNTU, I have it set-up as per, and no errors.  But no mail comes in. Any ideas why?

4. My system is setup as std.  ./swap  ./home  ./root  How do I add more space by using part of a large NTFS partition?  I did try Gpart, booting from the CD, but that just throw up errors for some reason and then stopped with the _ flashing away at me.

What I'm trying to do here, is move across to UBUNTU for most of the HDD space I have, 3 drvs. 160 for UBUNTU - 300 & 500 for NTFS.  Not having enough free space to move files/folder around.  I just want a very basic XP system, to be able to run one or three XP programs, games, ebay turbo, rFactor. and a few others.  So will be un-installing a far bit of stuff that I will no longer need or UBUNTU can work with it. The 300 HDD is the main boot drv for XP. So I happy leaving that as is. The 500 drv is the one that I would like to use under UBUNTU.  So my thinking was, turn the free space over to UBUNTU, but in what format and name?  Moving what is on the NTFS partition across to the linex one and then doing what's left.  What is the best way to do this?

Cheers for your time and help on my question.
Andy

---

### Post by bryncoles on 2011-03-01
Good questions.  I think forum etiquette is usually to start a separate thread for each problem though. That way you can attract more posters by giving each thread a descriptive title.  

Now, I can only help with question one, assuming question 1 is asking how to change directories from the command line.  It's done with the 'cd' command (cd = change directory).  Just type cd FILEPATH, thus:

```
cd ~/Desktop
```to get to the desktop of the home folder. 

```
cd /tmp
``` to get to the temporary internet folder, and so forth.  Do a google search for something like 'terminal commands linux' for further info. 

I hope somebody else with knowledge of your other problems comes along soon!

---

### Post by oldos2er on 2011-03-01
If by "black box" you mean a command prompt, the Linux equivalent is terminal, you can access it via menus Applications, Accessories, Terminal. [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

For resizing your partitions, you were on the right track booting from CD to run gparted. Please post the errors you saw so we can determine what went wrong.

---

### Post by Kirboosy on 2011-03-01
> **9000cse said:**
> Hi all, a few questions, I could do with answering.

3.  The Mail system within UBUNTU, I have it set-up as per, and no errors.  But no mail comes in. Any ideas why?



This is probably because your other email client (in windows) has downloaded all the previous emails. Therefore unless you get new ones, your Evolution client won't recieve any emails.

> What I'm trying to do here, is move across to UBUNTU for most of the HDD space I have, 3 drvs. 160 for UBUNTU - 300 & 500 for NTFS. Not having enough free space to move files/folder around. I just want a very basic XP system, to be able to run one or three XP programs, games, ebay turbo, rFactor. and a few others. So will be un-installing a far bit of stuff that I will no longer need or UBUNTU can work with it. The 300 HDD is the main boot drv for XP. So I happy leaving that as is. The 500 drv is the one that I would like to use under UBUNTU. So my thinking was, turn the free space over to UBUNTU, but in what format and name? Moving what is on the NTFS partition across to the linex one and then doing what's left. What is the best way to do this?

You really don't need to format the drive unless you want to. You can use it as is. Just Navigate under Places-->Computer--> and double click your 500 Gb drive. If you want you can Format the drive and rename it, but keep in mind that you will most likely want to keep it NTFS or FAT that way Windows can read it. IF you format it ext4 or ext3 then your drive will only be accessible under Ubuntu. It would be a pain for you to have to reboot into Ubuntu if you needed the files in Windows at the moment.

---

