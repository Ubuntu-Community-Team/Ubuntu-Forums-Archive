---
title: "system gone wackers 8.0"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by misswham on 2010-01-26
a few weeks back my system started running sluggishly. I started getting an update cirlce in my toolbar at the bottom that I had never seen before in the years I have had ubuntu.  I would update as it said but it always said sytem was already updated and it would go away but come back 30 mins later.  I have been having problems since then.  

So today I walked away from the computer and came back 1 hr later and my screen resolution went out of wack and it was wayyy bigger than my screen, so i did control-alt-backspace to restart and it ran through the check when it has a bad shutdown and when it got to 92% this is what came up



An automatic file system check (fsck) of the root filesystem failed.  A manual fsck must be performed, then the system restarted.  The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.  

bash:  no job control in this shell
Bash:  groups: command not found
bash:  lesspipe: command not found
bash:  Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash:  Command:  command not found
bash:  The:  command not found
root@aretha-desktop:  #

I tried to type it exactly.

I pressed CONTROL-D and it restarted and went through the check again and got all the way to 92% and gave me the same message.

I dont know what has happened.

Can someone please help me?  Does it sound like i have some sort of bug?

---

### Post by sailthesea on 2010-01-26
```

An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.

```
 Did you do this ?
What was the output if you did?

---

### Post by misswham on 2010-01-26
i dont know how to run a manual check.  can u tell me how please?

---

### Post by sailthesea on 2010-01-27
OK 
1.What version of Ubuntu are using? 
2.Is that an upgraded installation? 
3.Are you dual booting? 
3.How much Hard disc space does it all use? Use Gparted to get the info

---

### Post by misswham on 2010-01-27
i rebooted in xp and it also went haywire.  I messed around with the resolution and the screen went blank but popped back in correctly.  so i rebooted in ubuntu and he resolution was fine and it went through the same motions at startup and got the same error message.  i hope someone can tell me how to run the maintenance check

---

### Post by misswham on 2010-01-27
i am using hardy heron.  it is the same version that i have had for 2 yrs.  yes i am dualbooting with xp but i havent logged on to it in a year but just did to see if i could and i could. as far as disc space that it uses i havent a clue.  i cant get back on and i dont know how to get or use gparted or what it is.  oh my god i have some valuable things on my ubuntu part of my harddrive.

---

### Post by sailthesea on 2010-01-27
Don't panic! 
Gone wackers 8.0 might be right (must add that to my sig ;))
I have to go now I hope you get helps
A look at your fsck and some CLI stuff should get you going though
Good luck and Good Night from the UK:D

---

### Post by misswham on 2010-01-27
thank you for trying.  i am so frustrated.  i love this operating system soo much and sing its praises but this is scaring me.  i have sooo much important stuff on there and i dont know how to run the manual  check.  

oh god send me someone who knows.

---

### Post by sailthesea on 2010-01-27
I'ts just a system error Some one will help you out soon Or I will get back to when I can Gotta Sleep Zzz

---

### Post by Ji Ruo on 2010-01-27
I'm a bit disappointed no one's spelled out what you need to do yet.

When you get the prompt, just type in: fsck and press enter. That's how you run a manual check. The fsck program will start and do all the work for you, but will come up with a few prompts, you just have to enter 'y' to all of them. This will fix any corruption on the filesystem. Then press Ctrl+D like it says and restart your system. Simple... once someone's pointed it out to you.

As for why you're hard drive is getting corrupted, that's where posting sailthesea's requested information will come in handy. Once you can get back in, go to system>administration>partition editor in the top menu to start gparted, which will show you the space left on your disk. 

Don't actually do anything in gparted though besides looking at how much free space you have.

---

### Post by 3rdalbum on 2010-01-27
When you get to that command-line, run:

```
fdisk -l
```

You should be able to identify the device file name for your Linux partition. The device file name begins with "/dev/" - it'll probably be something like /dev/sda2 or /dev/hda2.

Once you have this device file name, you can run fsck:

```
fsck /dev/sda2
```

EDIT: Just noticed that you're already at a root shell, so you don't need 'sudo'.

---

### Post by Raijin8 on 2010-01-27
You should boot from a live CD and back up you files if possible. Try doing
```
sudo fsck /dev/[your filesystem here]
```
from a live CD as well. You can find out what to fill in there (it should be sda0 or sda1 or something) as well as the other info about your drive from GParted, which should be on the live CD if it's not on your install of Ubuntu.

---

### Post by misswham on 2010-01-27
thank you so much ji ruo.  it worked perfectly and i went to systems>administration and i didnt see the other u told me to click on but i clicked on system monitor and it says i havce 157.6 GIB TOTAL  63.1 FREE  55.0 AVAILABLE  95.5 USED.

does this tell u anything?

---

### Post by Ji Ruo on 2010-01-27
> **misswham said:**
> thank you so much ji ruo.  it worked perfectly and i went to systems>administration and i didnt see the other u told me to click on but i clicked on system monitor and it says i havce 157.6 GIB TOTAL  63.1 FREE  55.0 AVAILABLE  95.5 USED.

does this tell u anything?

Yes, it means that it's not due to a lack of space on your hard drive. With Linux you don't need to defragment your hard drive like you're always told to do with Windows, but the tradeoff is that once you have less than something like 10% of free space you can get problems. You've got 1/3 free so that's not the issue.

I was getting file corruption on an old laptop I had with every second boot or so, and after a few weeks of that the hard drive died. So if it keeps on happening more frequently, that's your problem. Anyway it's fixed for now and if it happens again you know what to do... in the meantime you should back up your data just in case it's not just a one-off problem. You could put all your important documents, pictures etc. onto DVDs or CDs so that if anything bad happens you haven't lost anything important. If you've got a lot of stuff you could consider putting in another hard drive or using an external one. Backups are very important! HTH

---

### Post by misswham on 2010-01-28
thanks soo much.

---

