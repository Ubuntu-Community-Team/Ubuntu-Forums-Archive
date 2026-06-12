---
title: "[SOLVED] Remote connection (ssh) - Keep jobs running even when you log out"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by tekkenlord on 2008-02-14
Hello! Can someone help me with this:

I have 2 computers (A and B), both running Ubuntu. Computer B is much more powerful than computer A but computer B is far away from home(where me and computer A is). So, I connect remotely (with ssh) to computer B from computer A and I get a terminal (of comp B on the screen of comp A) where I can run jobs and programs. The problem is that if I close the terminal the jobs will be terminated. (I hope what I've written makes sense...)

Is there a way to avoid this? So that when I close the terminal I do not loose the jobs? Will I be able to log into computer B again and check on the jobs?

Thanks in advance!

---

### Post by tekkenlord on 2008-02-15
Just a friendly bump...

---

### Post by Shubo on 2008-02-29
Look at: [http://www.howtogeek.com/howto/ubuntu/keep-your-ssh-session-running-when-you-disconnect/](http://www.howtogeek.com/howto/ubuntu/keep-your-ssh-session-running-when-you-disconnect/)

---

### Post by Mr. C. on 2008-02-29
[deleted - misread]

---

### Post by NetFreeDiver on 2008-06-24
Hello,

I just learned "nohup" command which works great.

example:

nohup [command that you normally run with all flags and everything] & (this last & is for job to run at background)


now job is running even you logout from ssh!

you can check screen outputs from nohup.out file with "cat" or any other editor when you ssh back to your remote computer.

---

### Post by leandromartinez98 on 2008-06-25
You can redirect the output of your program to any file:

nohup program > file.log &

The nohup.out file will only contain non-standard output (crashes, etc..., if any).

The "screen" program works as well, but it is a little more complicated to get used to. However you can leave the terminal and continue to have a "screen" for each program when you go back, like if you never had left.

---

### Post by Archmage on 2008-06-25
I use the program "screen" for this.

---

