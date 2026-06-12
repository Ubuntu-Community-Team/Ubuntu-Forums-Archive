---
title: "Dual booted Ubuntu problems"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by zdubun on 2009-10-14
Dear All,

Need advice.

I recently installed Ubuntu 9.04 on my dell latitude d630, core 2 duo along with windows. I used the slider in the installer to free up some space on the hard drive for ubuntu.  Ubuntu is working fine but:-

1.  My kaspersky antivirus in windows has stopped working.
2. the windows is behaving strangely.

Thanks in advance

---

### Post by vipulkelkar on 2009-10-14
can u a bit elaborate on what is it doing strange ...

---

### Post by Mark Phelps on 2009-10-14
> **zdubun said:**
>  1.  My kaspersky antivirus in windows has stopped working.
2. the windows is behaving strangely.

Did your Dell have Vista preinstalled? If so, don't be surprised if the shrinking using Ubunbtu damaged the Vista OS in some way.  There have been reports of Vista being rendered unbootable after such an operation.

If you have a Vista DVD, you should boot from it and run Startup Repair a few times -- and see if that fixes the problems.

If it doesn't (and that's my guess), open an elevated command window in Vista and run "sfc /scannow" to attempt to locate and repair corrupted/missing system files.

---

### Post by dunkar70 on 2009-10-14
I learned the hard way to use the Windows Vista tools to shrink the Windows partition before adding Ubuntu. Windows is picky about sharing. 

Assuming you have (and want to keep) Vista, you may need to backup your data, execute a restore of your Vista environment, then start over. Before shrinking your Vista partition, you may need to defrag the partition. Unfortunately, the defrag tool focuses on optimized performance rather than consolidating the files so you can reduce the partition. The GUI has very little flexibility, but you might be able to find some command line options on a Windows forum.

---

### Post by zdubun on 2009-10-15
Dear All ,
Thank you in advance. Mine is windows XP. It came "preinstalled" with the laptop when I bought it. Howver I have the Kaspersky CD still with me. Would reinstalling it solve the problem.

Thank ing you in advance

---

### Post by Niko Johnson on 2009-10-15
if you have a windows recovery partition on your disk you should try booting off that and attempt to reinstall Vista. but it is picky when it comes to shrinking and you should always defrag before installing ubuntu... you should get a trial version of perfect disk, its a great defraging program that i used with amazing results

---

### Post by DGortze380 on 2009-10-15
You really need to give us more information before we can help.

What do you mean by 'your anti-virus stopped working', what exactly does it no longer do that it is supposed to be doing?

What do you mean by 'windows is acting strangely', what is doing that is 'strange'?

---

### Post by zdubun on 2009-10-15
The Anti Virus is not active anymore. It posts up an error.

---

### Post by DGortze380 on 2009-10-15
> **zdubun said:**
> The Anti Virus is not active anymore. It posts up an error.

Ok, last try here.

You need to give us MORE INFORMATION if we are going to help you.

What is the error?
You should likely uninstall and reinstall the antivirus .. but you've told us nothing about these mysterious Windows issues...

---

### Post by Pelsia on 2009-10-15
I was in a similar situation to you as I just recently setup my laptop to dual boot XP and Ubuntu.  Using the Dell OS cd is really nice as it will install most drivers needed to get things running and start installing current ones.  

So far I've had 0 problems with XP or Ubuntu; though the *only* thing I use XP for is running games that either aren't ported to Linux, or can't run with Wine.  Long as your data is backed up, reinstall would probably solve the problem.

Just be sure to install XP first, and then when you get to the fdisk portion of the install (partition mananger), delete all existing partitions, then create 1 that Windows will use.  *Leave the rest of the disk as free space, don't partition it.*  When you go to install Ubuntu choose the option of install in all existing free space and you should be good to go.

---

### Post by zdubun on 2009-10-22
Hi all,

When I try to shut it sown I get a message that avp.exe cannot be shut down.

During booting windows up I get a message saying that a certain memory place cannot be read.

The windows hangs if i tru to shut it down.

Thank you all .

---

