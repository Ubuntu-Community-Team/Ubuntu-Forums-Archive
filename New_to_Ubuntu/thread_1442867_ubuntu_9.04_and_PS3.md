---
title: "ubuntu 9.04 and PS3"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by alan_18 on 2010-03-30
Sorry if this is in the wrong place, but I wasn't sure where else to post it.

I have one of the older 60gb ps3's, and I put a 500gb hdd in it a while back.  Recently, I decided to get on the bandwagon and install linux on my ps3.

That all went well, got the video configured and installed VLC player, where the issue is though is I can't figure out how to play the videos I have saved on the ps3 partition.  I have a few hundred gb's of movies and tv shows on my ps3 that I'd like to play through ubuntu.  Is it possible to make ubuntu 9.04 read or recognize the data on the ps3 partition?

---

### Post by J V on 2010-03-30
Yes, if you are on 9.04 it gets a bit more complex though :)

Could you post the output of "fdisk -l" please

You'll also want to install ubuntu-restricted-extras

---

### Post by alan_18 on 2010-03-30
> **J V said:**
> Yes, if you are on 9.04 it gets a bit more complex though :)

Could you post the output of "fdisk -l" please

You'll also want to install ubuntu-restricted-extras

I installed the extras like you said, and fdisk -l returns "Cannot open /dev/sda"

---

### Post by kokkus on 2010-03-30
A ps3 has 250mb of RAM and since you don't have a gfx card you will never get it to work. And no, you can't install a nvida driver for the vuilt in gfx card the ps3 uses.
You can only solve this problem by using an external fgx card with built in memory greater then 1gb.

---

### Post by J V on 2010-03-30
That was completely and utterly random...

Its got 500 megs, a very nice video card, which works... And he is trying to access his files not install drivers... You've spent too much time in the absolute beginners forum :P

Could you try "sudo fdisk -l", then input your password (It will look like nothing is typing but it is, just keep going)

---

### Post by hansdown on 2010-03-30
Please keep in mind, that sony's planned April 1st. update will bork ubuntu installs.

[http://news.cnet.com/8301-13506_3-10471356-17.html](http://news.cnet.com/8301-13506_3-10471356-17.html)

[http://arstechnica.com/gaming/news/2010/03/hacker-vows-to-fight-sony-ps3-update-restore-linux-support.ars](http://arstechnica.com/gaming/news/2010/03/hacker-vows-to-fight-sony-ps3-update-restore-linux-support.ars)

[http://news.yahoo.com/s/nf/20100329/bs_nf/72456](http://news.yahoo.com/s/nf/20100329/bs_nf/72456)

---

### Post by J V on 2010-03-30
Well that sucks... I'll be on psn strike until geo gets a patch out for sure, sony just created THE gate to ps3 piracy...

---

### Post by hansdown on 2010-03-30
> **J V said:**
> Well that sucks... I'll be on psn strike until geo gets a patch out for sure, sony just created THE gate to ps3 piracy...

I agree.

Sony's plan appears to be somewhat short sighted.

---

### Post by kokkus on 2010-03-30
> **J V said:**
> That was completely and utterly random...

Its got 500 megs, a very nice video card, which works... And he is trying to access his files not install drivers... You've spent too much time in the absolute beginners forum :P

Could you try "sudo fdisk -l", then input your password (It will look like nothing is typing but it is, just keep going)

You don't understand. we are talking about a PS3 (playstation 3).
When u install ubuntu on a ps3 the os will not be able to use the ps3 gfx card nor built in RAM. that's why he can't play video files.

---

### Post by J V on 2010-03-30
Just read that, It can use 256megs though, and the video isn't too choppy with SD... If OP still wishes to go linux, suggest gentoo, nice and speedy, less easy to use but with 256 megs you need the speed ;)

Edit: Or you could use mplayer from a terminal keeping load even lower with no X...

---

### Post by Ocxic on 2010-03-30
not to mention you cannot access the PS3 side of the HD as it is encrypted

---

### Post by alan_18 on 2010-03-30
> **J V said:**
> Just read that, It can use 256megs though, and the video isn't too choppy with SD... If OP still wishes to go linux, suggest gentoo, nice and speedy, less easy to use but with 256 megs you need the speed ;)

Edit: Or you could use mplayer from a terminal keeping load even lower with no X...

I found a guide that instructed me on how to [use the GPU as a swap]("http://psubuntu.com/wiki/PSUbuntuGPU").  Runs much faster now, and it's not that I can't play video files, it's that ubuntu can only see the 10gb partition that the PS3 gives it.

Also, sudo fdisk -l didn't return anything, at all.

---

