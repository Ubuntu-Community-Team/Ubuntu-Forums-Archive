---
title: "Another iPod problem"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Zepar on 2009-07-29
I've been using Ubuntu for a couple weeks, and I just recently tried to add songs from my music library to both my iPod and my mom's(mine is a 2nd gen nano, her's a 3rd gen nano). Everything I did with mine worked more or less flawlessly, however when my mom's was plugged in, and music erased(using Banshee) the "other" portion of the file space immediately took up whatever space was free, and when it was unplugged, both the iPod and Banshee(when it was plugged back in) said that there was no  free space, and no music(in actuality, only two or three albums were erased of about 4 gbs of music), and now it won't mount, and still reads 0mb free space, and No songs.

I've tried looking at several of the other threads that people have posted to no avail.
When I plug it in, and look in the Computer folder it is given a name like "USB Device" or "Mass Storage"(it changes); when I try to open it, I get the message "Unable to mount location: Can't mount file"
I have tried mouning it through a terminal, to which I receive:

```
brandt@brandt-laptop:~$ sudo mount -t vfat /dev/sdf1/media/JENNIFER'S
> 


```And nothing happens. I know that sometimes it takes a bit and then goes through, as if loading, but it seems that this time it isn't doing anything.

Please, help!

(BTW, I am using Jaunty, and I have installed Listen because some said that it worked much better with the 3rd gen nanos; I'm sure that's true, and that it would be so... if it would mount.)

P.S. if you have any questions, i'll do the best I can to answer them

---

### Post by Volt9000 on 2009-07-29
See that > on the second line? That means bash is still waiting for input, because it saw the single quote on the first line, which it interprets as a delimeter.

It's better to avoid using the single quote, but if you really want it, you have to escape it with a backslash. So your revised command is:

```

sudo mount -t vfat /dev/sdf1/media/JENNIFER\'S

```

Note the backslash betweeen "JENNIFER" and the single quote.

---

