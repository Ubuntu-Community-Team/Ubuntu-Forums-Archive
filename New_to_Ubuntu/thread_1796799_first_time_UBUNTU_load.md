---
title: "first time UBUNTU load"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by yyuryyubicuryy on 2011-07-04
I have a desktop PC with 2G ram and a Pentium (R) D processor. I am trying to load UBUNTU for the first time. I have created a CD with version 11.4 of UBUNTU and have tried several times to load from the CD. What I get is "UBUNTU ......" that stays for a long time and eventually a black screen. When I hit Esc partway through the installation I can see the following error lines:
cannot execute mktemp /input/output error
sed /root/etc/debconf: input/output error
chroot:can't execute debconf-communicate
/scripts/casper-bottom/10adduser:line 20 cannot open /root/usr/share/debconf/confmodule


and more. I cannot get this to load from the windows side either. I put in my cd and the window comes up with three options. I select install in windows and it appears to be loading, then stops and says "invalid argument" and shows a log file location. Looking at the log file, the end looks like this (complete file attached)
"

07-04 07:04 DEBUG  TaskList: ## Finished copy_installation_files
07-04 07:04 DEBUG  TaskList: ## Running get_iso...
07-04 07:04 DEBUG  TaskList: New task copy_file
07-04 07:04 DEBUG  TaskList: ### Running copy_file...
07-04 07:06 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
07-04 07:06 DEBUG  TaskList: # Cancelling tasklist
07-04 07:06 DEBUG  TaskList: New task check_iso
07-04 07:06 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
07-04 07:06 DEBUG  CommonBackend: Searching for local ISO
07-04 07:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-04 07:06 DEBUG  TaskList: New task get_metalink
07-04 07:06 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-04 07:06 DEBUG  TaskList: # Cancelling tasklist
07-04 07:06 DEBUG  TaskList: # Finished tasklist"

I have also tried to load this on other older PCs and have had the same luck even with reformated (no os) disk. Is this a bad version to load from to start with? Or am I missing something?

---

### Post by Bucky Ball on 2011-07-04
Welcome. Go for 10.04 LTS. Stabler and you will get a smoother ride as a newcomer and can upgrade when you are more familiar (although 10.04 LTS is long-term support release until 2013). 11.04 has some issues with some systems.

See if you get the same issues. You need to boot from the CD, *not* Windows unless you have downloaded the Wubi installer. Windows will not have any idea about a regular install ISO CD. 

What version of 11.04 did you download? Desktop, Alternate, Wubi???

---

### Post by bcbc on 2011-07-05
> **yyuryyubicuryy said:**
> ... Is this a bad version to load from to start with? Or am I missing something?

This is most likely a bad burn. (That wubi "[errno 22]", combined with the problems booting from cd, make it very likely). See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) for instructions on how to burn and check a CD.

---

### Post by 3rdalbum on 2011-07-05
The "Input/Output" errors reported when booting Ubuntu suggest that the CD you created is faulty, or your CD-ROM drive is starting to die.

It might also point to bad RAM.

The first thing to try is to stop burning Ubuntu onto the cheapest CDs you can find. Buy a somewhat more expensive disc. CD-RWs tend to work quite well. And when burning, use a lower speed like 8x to ensure a high standard of burn. After burning the disc, take it out of the drive and allow it to cool naturally before trying to boot off it.

Try that, and see how you go.

---

