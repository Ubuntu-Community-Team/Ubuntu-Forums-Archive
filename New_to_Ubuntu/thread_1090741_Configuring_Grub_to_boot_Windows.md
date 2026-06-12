---
title: "Configuring Grub to boot Windows"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Dj Melik on 2009-03-08
[img]http://i43.tinypic.com/34oejv6.png[/img]

Here is how my partition table looks.. Windows is currently installed on /dev/sda5, how can I set up grub to boot that :/

---

### Post by Panzor on 2009-03-08
```
$sudo gedit /boot/grub/menu.lst
```
add
```
title     Windows
root     (hd0,4)
makeactive
chainloader    +1
```to the bottom. Hmmm, it's on the extended...well, this is definitely the first thing I would try. Not sure if the extendedness is going to mess it up.

---

### Post by Dj Melik on 2009-03-08
> **Panzor said:**
> ```
$sudo gedit /boot/grub/menu.lst
```
add
```
title     Windows
root     (hd0,4)
makeactive
chainloader    +1
```to the bottom. Hmmm, it's on the extended...well, this is definitely the first thing I would try. Not sure if the extendedness is going to mess it up.

I tried that won't work :(

---

### Post by meierfra. on 2009-03-08
It looks like you deleted the partition containing the boot files for Windows XP.   

This HowTo  shows  you how to solve your problem:

[http://ubuntuforums.org/showthread.php?t=813628]("http://ubuntuforums.org/showthread.php?t=813628")
[B]
If you need additional help:[/B]


Download the Boot Info Script to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by mlentink on 2009-03-08
you might want to read this: [http://forums.cnet.com/5208-6142_102-0.html?forumID=5&threadID=332520&messageID=2991782](http://forums.cnet.com/5208-6142_102-0.html?forumID=5&threadID=332520&messageID=2991782)
and this:
[http://www.goodells.net/multiboot/](http://www.goodells.net/multiboot/)

---

### Post by kansasnoob on 2009-03-08
> **meierfra. said:**
> It looks like you deleted the partition containing the boot files for Windows XP.   

This HowTo  shows  you how to solve your problem:

[http://ubuntuforums.org/showthread.php?t=813628]("http://ubuntuforums.org/showthread.php?t=813628")
[B]
If you need additional help:[/B]


Download the Boot Info Script to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

Always glad to see you pop in! I was just prepared to say, "oh no, it's on an extended partition"!

As many times as I've seen you and caljohnsmith do this I still don't get it!

---

### Post by presence1960 on 2009-03-08
> **Dj Melik said:**
> [img]http://i43.tinypic.com/34oejv6.png[/img]

Here is how my partition table looks.. Windows is currently installed on /dev/sda5, how can I set up grub to boot that :/

I may be incorrect, but I seem to recall that Windows does not like booting from an extended or logical partition.

---

### Post by kansasnoob on 2009-03-08
Presence,

I've yet to figure it out, but I've seen three people here on the forums lead people through the process successfully. They are meierfra, caljohnsmith, and unutbu.

I plan on studying the guide just posted by meierfra! It's something I'd like to learn.

Personally, I prefer partitioning properly to begin with! That and I find it very easy to use Partimage to copy a partition to an external drive and then copy it back to a properly partitioned drive.

But it's always good to know the alternatives.

---

### Post by presence1960 on 2009-03-08
> **kansasnoob said:**
> Presence,

I've yet to figure it out, but I've seen three people here on the forums lead people through the process successfully. They are meierfra, caljohnsmith, and unutbu.

I plan on studying the guide just posted by meierfra! It's something I'd like to learn.

Personally, I prefer partitioning properly to begin with! That and I find it very easy to use Partimage to copy a partition to an external drive and then copy it back to a properly partitioned drive.

But it's always good to know the alternatives.

I hear you Kansasnoob. I didn't say it wasn't possible, but it is much more uncomplicated and straightforward to put Windows on a primary partition. You know how Windows can be!

---

### Post by Dj Melik on 2009-03-09
Thanks a lot everyone, sorry for the late reply. But I got it to work. 

I followed meierfra.'s guide and got it :)

---

### Post by meierfra. on 2009-03-09
> I followed meierfra.'s guide and got it 

Glad to here that my tutorial worked for you.
Have fun with XP and Ubuntu.

---

### Post by meierfra. on 2009-03-09
> Not sure if the extendedness is going to mess it up. 

> "oh no, it's on an extended partition"!


> Windows does not like booting from an extended or logical partition. 

I just would like to point out that  **grub does not have a problem with booting Windows from a logical partition.**

Only the Windows boot code  in the MBR is not able to boot logical partitions. So Windows always puts the boot files onto a primary partition. Often this primary partition seems to have nothing to do with the Windows OS and gets deleted. 

So Dj Melik's problem was not caused by the fact that Windows is on a logical partition, but by the missing boot files.

---

