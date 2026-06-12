---
title: "Killed Rescue and Recovery on a ThinkPad?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by bitrocker on 2008-12-11
Hi,

this is especially meant for those, who want to install (K)UBUNTU on an ThinkPad with Rescue and Recovery Partition.
Well, I did, I nearly crashed everything, I could restore almost everything, I want to warn you. As well as I have got a questions.

The  installer does not ask you when it writes to the MBR! Well, I know that Windows does that, but expected more from a Linux installer ;(
 Since the MBR of a ThinkPad contains information on how to boot Rescue and Recovery it should not be overwritten!!!
If you want a dual-boot system I strongly recommend to do the "install inside Windows" installation!
If you already crashed you PC or still want to try to install not inside Windows, here are helpful hints: [http://www.thinkwiki.org/wiki/Rescue_and_Recovery]("http://www.thinkwiki.org/wiki/Rescue_and_Recovery").

If you crashed your ThinkPad, and can`t get it running, just ask... I`ll try to help.

Strange thing now, is after the whole procedure, I`ve got my Rescue and Recovery back, I`ve got my Windows again (better don`t ask what happed to it) and I`ve got an KUBUNTU (installed 'inside' Windows).
But strange wise, my Rescue and Recovery Partition isn`t hidden anymore into Windows!? But it is hidden in KUBUNTU. So the partition type must have changed. Anyone knows who to check the partition type and maybe change it?

---

### Post by yakyuwarrior on 2008-12-30
OK, I am having what sounds like a similar problem, want to get some advice:

Note: I have a T61 with windows vista, 160 GB HDD.  Have dual-booted with ubuntu/openSUSE (see below)

Here is how I messed everything up:

1: I installed ubuntu normally (8.04, updated to 8.10).  Used it for 4 months, never worried about the rescue and recovery functionality at all (probably didn't work; never tried it).  Everything worked great

2. Got curious; decided to try openSUSE 11.1.  During install, I repartitioned the linux extended partition.

3. Decided I didn't like openSUSE (too many issues getting Plasma to work smoothly).  I used the option in YaST to reset the MBR to it's original setting (mistake!).  Upon reboot, discovered that this functionally deleted the MBR; windows won't boot (although it's there), R&R won't boot (although the recovery partition is there), and, surprisingly, ubuntu live CD's (8.04 and 8.10) won't boot.  However, the openSUSE install DVD still runs fine (NOT a live DVD/CD).

4. I then used the recovery tools on the openSUSE DVD to delete/reformat the linux ext. partition.  No effect on ubuntu live cd.

5. After a lot of research, it appears I have a couple of options:

[INDENT]A. Use a windows recovery cd to restore default vista MBR, then use BMGR to restore the default Thinkpad MBR (see [http://www.thinkwiki.org/wiki/Rescue_and_Recovery]("http://www.thinkwiki.org/wiki/Rescue_and_Recovery")).[/INDENT]

[INDENT]B. Use the openSUSE dvd recovery tool to create a bootloader that will allow me to boot windows, Then restore the original thinkpad MBR using BMGR. [/INDENT]

[INDENT]C. Find (where?) a bootable recovery disk that will restore the original MBR configuration.[/INDENT]

6. I will then follow instructions on how to install ubuntu without removing the thinkpad R&R functionality.

Is there anything I am missing?  I am I on the right track?  Please let me know if anyone has any better suggestions...

---

### Post by yakyuwarrior on 2008-12-30
Update: Options A and B (see prev. post) both failed.

A. When the windows recovery CD was used, the recovery software failed to find any vista operating system or partition.  This halted any progress.

B. The openSUSE MBR tool cannot function unless a linux OS is actually installed on the hard disk; I may need to reinstall openSUSE in order to create a bootloader, then move forward from there.

Does anybody know of a better recovery tool that I could use?

---

### Post by bitrocker on 2008-12-31
Hi,

well, your problem is a MBR prob, but somehow different from mine, so I am not shure if I can help.

So here is what I did:
1. Applied the hints from [http://www.thinkwiki.org/wiki/Rescue_and_Recovery]("http://www.thinkwiki.org/wiki/Rescue_and_Recovery") to make GRUB access the R&R partition. I did the Recovery.
But since I still could not boot Windows (XP) (to complete the installation)...
2. I used a XP-CD, entered the setup, used the repair option, did
```
fixmbr
fixboot
```
3. Completed Windows Installation.
4. Installed Kubuntu inside Windows.

I am not sure if the Ultimate-Boot-CD can help you, but a look wont`t hurt: [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

Another thing that might be useful is SperGRUB (I did try it...)

Good luck...

---

