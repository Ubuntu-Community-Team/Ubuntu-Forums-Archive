---
title: "XP Booting from after installing Ubuntu on external drive"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Ayersrock on 2009-10-20
Hey guys :-)
I've installed Ubuntu (9.xx, most recent release afaik) as my first Linux OS ever and it actually worked out ok, apart from one problem...I installed Ubuntu on an external disk and I now have the problem, that Windows XP doesn't boot, when the external drive isn't connected to my PC. 
It says Grub loading error (or something very similar).
When the external drive is connected, I can choose between Ubuntu and Windows without problems...

So, my questions are:
Do I have to fix the MBR of my windows installation?
How do I get my system to boot Windows automatically when the external drive isn't connected, with the least risky changes?


if there any other information is needed, I'll try to provide it as fast as possible.
thanks already!

Georg

---

### Post by martrn on 2009-10-20
> **Ayersrock said:**
> Do I have to fix the MBR of my windows installation?
Yes!
1.Enter Windowze Recovery Console. 2.When you reach the command prompt, type the following and then press Enter. [COLOR="Black"]fixmbr[/COLOR] 3. The fixmbr utility will write a master boot record to the hard drive that you're currently using to boot into Windowze. This will repair any corruption or damage that the master boot record may have. 4. Take out the Windowze CD, type exit and then press Enter to restart your PC. 5. Windowze should now start normally. 

> **Ayersrock said:**
> How do I get my system to boot Windows automatically when the external drive isn't connected, with the least risky changes?

See above.

Ensure that your external (ubuntu disc) is not connected so it writes to the master boot record to the windows disc, and everything should be fine.

---

### Post by rs_man on 2009-10-20
Congratulations on installing Ubuntu. It sounds to me like the Ubuntu installation wrote a new boot sector, if you leave the external drive connected you should be prompted with a menu in which to select the OS you want to start. My suggestion is to boot to the windows startup disk and repair your MBR. You will then be able to get into windows at least. 

Im assuming the reason for installing on an external drive is so you can boot from any PC, correct me if Im wrong. If that is your goal, then I would suggest using Usbuntu. Its a great windows based tool that does exactly what it sounds like you are trying to do. Its fairly straight-forward and works. I've tested it on several HDDs to let my family tinker with the OS before I force them to convert.

---

### Post by Ayersrock on 2009-10-24
Hey, it's me again!
Thanks for the answers, had no time to write due to university word...
I've come up with a few more questions on the issue, which I'm sure you can help me with ;-)
First of all, I'm wondering about the risks of resetting the MBR. Any main issues I have to consider (apart from saving the data on my hard drive)?
Last time I messed around with the boot sector (even though I thought I knew what I was doing) it went so wrong, even a computer specialist had problems fixing my hard drive^^
So I'm wondering about leaving everything the way it is, as long as Windows is booting while the external drive is connected. 

Furthermore I'm thinking about using VirtualBox...I mainly need Linux for University reasons: Programming and a few mathematical programs that only exist as Open Source projects for Linux. 
Is Ubuntu okay for me? I do want to learn a few things about the OS for personal reasons, but mainly it has to fullfill "university requirements" so I have to be able to work with it as quickly as possible. 
What do you think about VirtualBox? Is it worth considering for me? Can I install all Linux Software in VirtualBox?
I guess the disadvantage will be, that without VirtualBox installed on the Host, it's no use even if I've got it with me on my hard drive?

thanks already
:)

---

### Post by Mark Phelps on 2009-10-24
It's a bad idea to start taking a thread into different directions.  Folks respond to posts based primarily on the thread  title.  No one's going to read through pages of posts to find your that NOW, you want information on Virtualbox, not on fixing boot problems.

Best to (1) search the forums for posts on Virtualbox to see if there's anything answer your questions and (2) if nothing is there, start a new thread about Virtualbox.

---

### Post by NCLI on 2009-10-24
> **Ayersrock said:**
> Hey, it's me again!
Thanks for the answers, had no time to write due to university word...
I've come up with a few more questions on the issue, which I'm sure you can help me with ;-)
First of all, I'm wondering about the risks of resetting the MBR. Any main issues I have to consider (apart from saving the data on my hard drive)?
Last time I messed around with the boot sector (even though I thought I knew what I was doing) it went so wrong, even a computer specialist had problems fixing my hard drive^^
So I'm wondering about leaving everything the way it is, as long as Windows is booting while the external drive is connected.
Windows should fix the MBR without any problems, and it is, AFAIK, an automated process, so you just have to type in the command, and Windows will do the rest.

Hard to mess that up :)

---

### Post by Bartender on 2009-10-24
If you spend some time looking into it, you'll find that MBR problems have been addressed about a million times on this forum.  If you don't have a genuine Windows disc you might not be able to fix the MBR.
The Windows MBR is just a little scrap of data at the beginning of the HDD that tells Windows where to go to find the OS.  So fix that first.

Then reinstall Ubuntu to the external but at the last step of the installation process click on the "Advanced" button and tell GRUB to install to the external HDD.

Or fix GRUB, but I think it's easier for newbs to just reinstall.

Either way, you need to look into how the Linux bootloader interfaces with Windows.  Until you get a handle on this you're likely to have trouble.

---

### Post by ranch hand on 2009-10-25
Read the link in the sig.  The links are advanced information.

If you need help use the;
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)
where people use grub2.

---

