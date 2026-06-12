---
title: "Question on Running from Live CD &amp; Start-Up?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-08
I have a strange start-up whereby before the splash screen, ubuntu decides to run a sort of health check, scanning various programs. Examples of what I see are, for example, "Setting kernal variables, mounting local filesystems..." It says OK to all of them and then goes to the Splash Screen.

[I was helpfully advised to do the following:]("http://ubuntuforums.org/showthread.php?t=1061304")

"....I suggest you boot to the ubuntu live CD and run
Code:

sudo fsck /dev/sda,1..."

**My question: when I start-up the laptop with the live cd in it, do i tap F12? - basically, how do I run from the live cd?**

Thanks, Lister

---

### Post by hyper_ch on 2009-02-08
when you start up the live cd tehn you run it from it. Just make sure the bios is set to boot first from cd.

and once you're in the live cd open a terminal and run
```

sudo fdisk -l

```
Then you get the list of partitions and you you will then run

```

sudo fsck /dev/sdXY

```
on each of them, if they are EXT3.

---

### Post by jerrrys on 2009-02-08
"My question: when I start-up the laptop with the live cd in it, do i tap F12? - basically, how do I run from the live cd?"

ok, just to make sure i knew what im talking about i dug out my live cd. f12 will give you boot options, but since you can already boot from cd its not needed, so just run with it and have fun.

---

