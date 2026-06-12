---
title: "Fastest Way To Completely Wipe Drive?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by yamfox on 2010-06-01
I have a drive fried to the point where GParted can't make a partition table for it. Boot and Nuke works, but it will take forever. Any other options?

---

### Post by inameiname on 2010-06-01
If it's an entire drive, I just use Killdisk. You can get the free version of it no problem, and it'll 'Wipe' it out entirely fairly fast. Of course, it depends on the size of your drive, and the speed of your computer. I'm not sure about Nuke, but if it works anything like Killdisk, then the time it'll take won't be much different. 

FYI, for a few years old laptop, I can erase 150GB hard drive in an hour using random pass.

Also, if you know of 'shred', it's another option within Ubuntu if you want.

I use this for flash drives and portable hard drives all the time:

sudo shred -v -z -n 1 /dev/sdb

...where 'sdb' is whatever your drive is...

shred (insert one of the below commands) FILE (insert name of file, or drive, or whatever) 

-f, --force
    change permissions to allow writing if necessary 
-n, --iterations=N
    Overwrite N times instead of the default (25) 
-s, --size=N
    shred this many bytes (suffixes like K, M, G accepted) 
-u, --remove
    truncate and remove file after overwriting 
-v, --verbose
    show progress 
-x, --exact
    do not round file sizes up to the next full block 
-z, --zero
    add a final overwrite with zeros to hide shredding 
-
    shred standard output 
--help
    display this help and exit 
--version
    output version information and exit

And then after it is done, you simply open up Gparted and format it as usual, and voila. Of course, as I said, the time it takes will be pretty much the same as Killdisk, or Nuke if it works the same way. So as far as a quicker way, there isn't one aside from keeping the erasing method down to the minimum, which I do in the above options.

---

### Post by Shpongle on 2010-06-01
you could try format it from command line using a live cd , [COLOR="Red"]use with caution[/COLOR] ,say if you wanted to remove the root dir "/" for example you would type sudo rm -rf / 

rm is remove , -r is recursively and -f is force.

again [COLOR="Red"]use with caution[/COLOR]

Edit Beaten to it :-p

---

### Post by mkvnmtr on 2010-06-01
The time it takes is related to the speed of your computer not the program. I use secure-delete quite often and set it to just make one pass. That is all that is really required. Still takes a very long time. Taking the 35 or so passes that used to be recommended would take a week.

---

### Post by yamfox on 2010-06-01
inameiname, that sounds fantastic! I can wait an hour :)

---

### Post by inameiname on 2010-06-01
Well an hour on my machine. It varies of course. 

Because it's the hardware that determines the speed, and the size of the drive of course, Killdisk or that shred command I mentioned would take the same amount of time for a particular device.

Shred would probably be the easiest since it requires the least to do. Just copy and past in the terminal and good enough.

---

