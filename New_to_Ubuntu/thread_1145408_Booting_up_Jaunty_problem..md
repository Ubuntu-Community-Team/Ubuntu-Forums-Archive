---
title: "Booting up Jaunty problem."
date: 2009-05-01
forum: New to Ubuntu
---

### Post by dan1973 on 2009-05-01
Hello all,

Have just updated my wubi installed version of intrepid to jaunty and as a consequence am experiencing a few problems.

The most pressing one is that every time it boots up, it gets about a third of the way through the 'graphical bar' on the loading screen, then stops a while, then reverts to text display. There is an error present here along the lines of the following:

```
/etc/rcS.d/s25brltty: 21: md5sum not found
```

The start-up then stops at this point. The keyboard works to type but there is no command prompt available.

I then ctrl-alt-del which gives the message:

```
rc5 killed
rc6 killed
```

and then jaunty gives the log-in screen and all goes well from there on.

When I had completed upgrading there was the following problem given:


```
E: /var/cache/apt/archives/memtest86+_2.11-3ubuntu1_i386.deb: unable to make backup link of `./boot/memtest86+.bin' before installing new version
```

Not sure how relevant this is but thought i'd mention it.

Please can anyone help?

---

### Post by lavinog on 2009-05-01
How did you update?

in the terminal, what is the output of 
```
ls /usr/bin/md5sum

```

---

### Post by lavinog on 2009-05-01
/etc/rcS.d/S25brltty is for the Braille terminal driver
if you don't need it, you can disable it by changing the S to K
```
sudo mv /etc/rcS.d/S25brltty /etc/rcS.d/K25brltty
```
and see if that fixes anything.

I don't have any md5sum commands in my S25brltty (but this particular machine is intrepid, so maybe there was a change in jaunty?)

---

### Post by dan1973 on 2009-05-01
Placed the K in front of the s25brltty file and the error message has gone - good.

However, this has had no impact on the boot-up problem. It still hangs on the start-up and still need to ctrl-alt-del following which it syas:

init rc5 killed
init rc6 killed

and then goes to sign in screen.

There must be some way around this as so far, i seem to have full function once inside jaunty.

Must get some sleep now but please try to figure it out,

Many thanks all,

---

### Post by lavinog on 2009-05-02
try this:
when you boot, go to the grub menu (press esc if it asks)
with your default boot selection highlighted press 'e'
then highlight the kernel line and press 'e' again
at the end of the line you should replace 'quite splash' to 'verbose' press enter
then press 'b' to boot.
What that should do is boot your system with all messages being displayed.
see if it gives you any more information.


I am on my jaunty machine, and sure enough there the brltty has a bug that checks the md5sum of the config file before it checks the existance of the config file...(This is a wasted operation that can slow down the boot a small amount if it doesn't exist...funny that the goal of jaunty was to speed it up.) EDIT: Filed bug report [https://bugs.launchpad.net/ubuntu/+source/brltty/+bug/370728](https://bugs.launchpad.net/ubuntu/+source/brltty/+bug/370728)

Did you happen to check if md5sum exists on your system?

---

### Post by dan1973 on 2009-05-02
Morning,

Ok, changed the boot up to verbose, has provided us with a clue:

The hanging point appears to be:

```
* Activating swapfile swap...
```

After stating this, it just hangs. Ctrl-Alt-Del shows following - managed to get some more detail.

```
init rc5  (786) main process killed by Term signal
init rc6  (1953) main process killed by Term signal
```

above message is not exact but numbers and codes are.

Hope this helps,

---

### Post by lavinog on 2009-05-02
Try adding noswap to the boot line (just like you did with verbose)
Note: editing the boot line in this manner is only temporary
To make these changes permenant, you will have to modify the /boot/grub/menu.lst

---

### Post by lavinog on 2009-05-02
just found a post about your issue:
[http://ubuntuforums.org/showthread.php?t=501953](http://ubuntuforums.org/showthread.php?t=501953)
launchpad question: [https://answers.launchpad.net/wubi/+question/65689](https://answers.launchpad.net/wubi/+question/65689)

---

### Post by dan1973 on 2009-05-02
Many thanks for the thread link,

Found my swapdisk file at following location:

```
/host/ubuntu/disks/swap.disk
```

changed it to:-

```
/host/ubuntu/disks/noswap.disk
```

and what do you know, we have clean boot-up.

Not sure how this will affect performance, shouldn't be too serious as I don't use too many 'power intensive apps.'

I think I'm going to call this problem solved for the meantime, thanks for your patience,:KS

---

### Post by lavinog on 2009-05-02
If you have plenty of ram, you can go without a swap.
I think the only time my computer uses swap is when I messup something.

---

