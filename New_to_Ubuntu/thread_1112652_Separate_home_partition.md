---
title: "Separate /home partition"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by outhouse on 2009-03-31
Bear with an old man trying to learn. I tried psychocats tutorial and everything worked till the end. After reboot I got dmrc and ICE errors. BUT when I boot into Recovery and drop down to root shell and hit enter I get a prompt at the bottom saying "enter password or type Control-D". Nothing I try works. The blinking cursor never moves. I've got home backed up to another drive, but after 3 days of searching I still can't figure out how to get back into Ubuntu to copy it back. If I have to re-install can I just  copy my /home backup or will I have to also install all my programs?
Thanks in advance for any help.

---

### Post by pbpersson on 2009-03-31
What were you attempting to accomplish to begin with?

What instructions did you follow?

When you boot from a Live CD and run Partition Editor, how does it look now?

When you boot from a Live CD and view your /etc/fstab file, how does it appear now?

Let us know if you need details on how to accomplish any of this, I know it all might be new to you.

---

### Post by D1ZZ4ZZT3R on 2009-03-31
ha! i just re-installed ubuntu on this comp and am in the process of installing it on my new (used) laptop. i'm stuck on how i should go about partitioning it. i'm searching the forums right now and will check psychocats (sp?) tutorial. if anyone can suggest any threads, please let me know. 

may the force be with you, outhouse. and, may we both figure out what we require.

---

### Post by pbpersson on 2009-03-31
How you should partition?  How many drives?  What size drives?  What do you want to accomplish?

I generally like three partitions:

/
/home
swap

However some people have said they like many more.

It is really up to you.

Oh....sorry.....those are mount points but hopefully you get my drift.

---

### Post by sgosnell on 2009-03-31
There is no password echo, for a reason.  Just type the password and then press enter, and you should get results.  You won't see anything at the prompt as you type, though.

I have no idea who psychocat is, or what his tutorial says.  We really have no idea what you've done, so more information is necessary.

---

### Post by JT9161 on 2009-03-31
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by lostbuthappy on 2009-04-01
Hello outhouse,

when you log in in a terminal (tty) the caret (courser) does not move when you type in your password (for security reasons). But since Ctrl+D does not work there seems to be some sort of problem (that is impossible to determine without more information).

You can boot from the ubuntu live-cd/usb-medium for maintenance. From here you should mount your root and home partitions. Type sudo fdisk -l for a list of available partitions or use gparted. Next check out /YourMountedRootPartition/etc/fstab for errors. You should also make sure that you copied/moved all data to the new partition, including hidden files and subdirectories (use rsync instead of cp to copy the files, it's much more secure).

In general, moving home to another partition is an easy procedure once you understand how mounting works and you double check what you're doing. In fact all this can be done while the system is running, without rebooting once (except for resizing your root partition, if neccessary).

Doing system critical stuff without understanding what you are doing is like playing russian roulette. One typo and you are screwed.

*Waiting for detailed information*
Dominik

---

