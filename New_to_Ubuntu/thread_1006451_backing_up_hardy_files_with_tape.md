---
title: "backing up hardy files with tape"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by squrl on 2008-12-09
Is there a way to .....

1.  Back up files as files to a tape unit 

2.  A simple tape backup program with a gui. The keyword is "simple".

I have searched and googled. So far all the tape programs are way to comlicated and so far I haven't found anything for file by foile backups.

Thanks.

---

### Post by mapes12 on 2008-12-09
tar (tape archive record) is the default tape backup utility. This is mainly command line configured. Terminal ```
man tar
``` will give you more info. 

Tapes are somewhat steam age these days. Any reason why you need tape instead of another partition somewhere else on your system/network?

tar will also work with HDD partitions.

If you could give some more detail about what you are trying to backup there are other solutions people could suggest.

---

### Post by Tomatz on 2008-12-09
> **mapes12 said:**
> tar (tape archive record) is the default tape backup utility. This is mainly command line configured. Terminal ```
man tar
``` will give you more info. 

Tapes are somewhat steam age these days. Any reason why you need tape instead of another partition somewhere else on your system/network?

tar will also work with HDD partitions.

If you could give some more detail about what you are trying to backup there are other solutions people could suggest.

I'm intrigued! Why tapes?

---

### Post by squrl on 2008-12-09
Why?  Mainly because I have a nice Sony tape unit and a big box of tapes.

---

### Post by Tomatz on 2008-12-09
> **squrl said:**
> Why?  Mainly because I have a nice Sony tape unit and a big box of tapes.

Nice! Bet it takes you back doing it. How long do you reckon it will take you?

---

### Post by karlr42 on 2008-12-09
You don't mean audio cassettes, do you?

---

### Post by scorp123 on 2008-12-09
> **mapes12 said:**
> Tapes are somewhat steam age these days. Says who??

> **mapes12 said:**
>  Any reason why you need tape instead of another partition somewhere else on your system/network?  Current DLT or LTO drives are not that expensive anymore. And when it comes to reliability nothing beats a tape. A tape has a way higher chance of surviving things that would kill a harddisk ;)

[http://en.wikipedia.org/wiki/Linear_Tape-Open](http://en.wikipedia.org/wiki/Linear_Tape-Open)

At work I use LTO-4 tapes .... that's 800 GB per tape, with a transfer rate of about 120 MB per second. ;)

[http://h18006.www1.hp.com/storage/tapestorage/index.html](http://h18006.www1.hp.com/storage/tapestorage/index.html)

---

### Post by scorp123 on 2008-12-09
> **squrl said:**
> 2.  A simple tape backup program with a gui. The keyword is "simple". Forget GUI's. If you use tapes you want reliability. Getting your entire stuff onto those tapes and back from the tapes again if needed is easy .... with the right commands. GUI? Forget it.

Read this:
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

All those commands there are identical for you with one exception: Instead of specifying a filename to write to or to read from you have to specify the name of the tape .... Chances are it's something like **/dev/nst0** (**_N_**on-rewinding **_S_**CSI **_T_**ape _**0**_) ... or /dev/rst0  (rewinding tape). The difference between them is that writing to /dev/rst0 will cause the tape to be automatically be rewinded after each operation. I personally don't like that and prefer to use the non-rewinding one. Both device names should point to the same physical device though.

BTW, could you tell us more about your tape drive? What is it? I hope it's **DDS-4** or something newer? Below that you should not bother ... any modern USB-disk would beat old DDS (DDS-3 and older) tapes speed- and size-wise.

---

### Post by squrl on 2008-12-09
It is a Sony DDS4 autoloader TSL-S11000. Holds 8 tapes. I did CAD work for years and did a full backup once a week plus inc every night. Made life a lot easier. With an extra magazine it went a long time between reloads and made keeping track of things a lot easier too. I must have fifty tapes.

Since I retired and use ubuntu now a backup is even more important but not near as simple.

---

### Post by handydan918 on 2008-12-09
I admire your recalcitrant orneriness. Check man mt. It MIGHT help....

):P

---

### Post by scorp123 on 2008-12-10
> **handydan918 said:**
> Check man mt Yes, I second that. You will have to use the "mt" tool to operate the tape drive properly. e.g. to rewind you would issue commands like e.g.  ```
sudo mt -f /dev/nst0 rewind
```

... or to take the tape drive offline and eject the tape:
```
sudo mt -f /dev/nst0 offline
```

You can combine those commands with the backup scripts I linked to above, e.g. have a script take a complete backup and then have the tape automatically ejected when everything is done.

Keep in mind that with DDS-4 you're limited to 20 GB per tape. So you should plan your backup strategy accordingly, e.g. it won't be possible to backup a directory containing 300 GB of graphics in one single go; you'd need to change tapes in between. Safest thing would be to divide the stuff up, e.g. directories A, B, C, and D go onto tape #1; directories from E to J go to tape #2; directories from K to Z will be on tape #3, etc.

I personally don't like to stretch backups over several tapes (it can be done though) ... if you lose one tape or if one tape gets damaged then your entire backup is probably gone too. It's much safer if you avoid that if possible ... or get a tape format that can handle more GB per tape ;)

And to all those who questioned tapes ... 20 GB on a DDS-4 tape isn't bad. It's far more space than you'd have on a DVD and a tape is far far more robust than either a HD or a DVD ;)

---

