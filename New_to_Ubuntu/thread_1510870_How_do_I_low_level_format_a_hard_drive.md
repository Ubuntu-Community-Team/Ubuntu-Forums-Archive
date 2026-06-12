---
title: "How do I low level format a hard drive?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by bwallum on 2010-06-16
Hi

I set up Lucid on a brand new 500GB harddrive. All went well. I was showing Ubuntu to a neighbour, using his workstation and simply swapping over boxes. Just as Ubuntu was booting up I turned away and when I looked back the neighbour was wet wiping his keyboard to clean it. I have no idea what command he managed to give to the computer but the Ubuntu splash had hung.

I decided to re-install after a couple of attempts to get it going.

The install process gets to the point where it is formatting the partition to ext4 at indicated 5% of the installation process complete. The red led showing hard drive activity flickers away...and away...and away. It has been chuntering on for a couple of hours now.

Is there any way to give the hard drive a low level format prior to partitioning?

---

### Post by migs73 on 2010-06-16
You can get Gparted Live, which will allow you to run from a CD and format the drive from there. Don't know how easy it is and I don't know what interface it uses though. The other option is to remove the hard drive and put it in an external caddy, and use Gparted (from the Software Centre) on the other machine to format it (that is the route I used).

---

### Post by bumanie on 2010-06-16
Assuming you mean zeroing the hard drive as being the same as a low level format - from a live cd > sudo dd if=/dev/zero of=/dev/sdx replacing the x with the drive letter of your drive (likely /dev/sda if you only have one hard drive) - be warned, on a 500gb hard drive, this could take some time. You could also use dcfldd which uses the same basic syntax as dd commands, but is about twice as quick. If you want to use dcfldd, > sudo apt-get install dcflddafter you have enabled repositories. In which case the syntax would be > sudo dcfldd if=/dev/zero of=/dev/sdx again replacing the x with the appropriate drive letter.
You could also use darik's 'boot and nuke' live cd and it will essentially do the same thing.

---

### Post by anewguy on 2010-06-16
A low-level format is when you completely rescan the physical drive - not just the data areas in the sectors, but the entire surface.  It will normally flag bad tracks and add them to the drives bad track table.  Sometimes that wipes out the factory bad track table and you have to redeclare the factory bad tracks.  Special programs are needed for this (as far as I know they are normally *not* part of an OS delivery.  These normally come from the drive manufacturer and most modern drives no longer need this due to their own error detection/flagging bad tracks on the fly.

So.......I have to assume you don't REALLY mean a low-level format but are using that term to represent what you want to do.

What I WOULD try:  boot the livecd with the "try ubuntu without changing your computer" option.  Fire up the partition manager (or run parted) and delete all of your existing partitions on the drive, THEN try reinstalling.

Dave ;)

---

### Post by srs5694 on 2010-06-16
You might also try using a SMART checking utility. This will query the drive's self-diagnostics, which might turn up details on any hardware failures, if indeed such problems are causing the filesystem creation step to fail. There are various Linux utilities to do this, like gsmartcontrol; or you can check with the drive manufacturer to see if they've got a bootable diagnostic disc.

---

### Post by jmore9 on 2010-06-16
I always use Gparted Live cd and boot from it to do my formatting.  so far it has been able to do everything i needed it to do.  

Easy , you just download the iso then burn it to cd.  Then use it.

Hope that helps.  I have not low level formated a hard drive since around 1982 or there abouts.  New ones do not give us users the software to do that anymore.

---

### Post by lukeiamyourfather on 2010-06-16
> **bumanie said:**
> Assuming you mean zeroing the hard drive as being the same as a low level format - from a live cd  replacing the x with the drive letter of your drive (likely /dev/sda if you only have one hard drive) - be warned, on a 500gb hard drive, this could take some time. You could also use dcfldd which uses the same basic syntax as dd commands, but is about twice as quick. If you want to use dcfldd, after you have enabled repositories. In which case the syntax would be  again replacing the x with the appropriate drive letter.
You could also use darik's 'boot and nuke' live cd and it will essentially do the same thing.

This is the way for sure (using dd), but be ***extremely*** careful because it won't ask you twice before it blows everything away.

Also the disk itself might be defective. Low level formatting the disk likely won't resolve any problems. Cheers!

---

### Post by bwallum on 2010-06-17
bumanie said it, you confirmed it, so I did it. Hours afterwards (overnight) I had a completely neutered brand new 500GB hard drive.

I fired up Lucid live cd and...hey presto, it installed as though nothing had happened.

Worked for me and thank you all very much for the help. Hope flaming June is happening for you too. Here in Scotland I have to say, it's perfect.

There's a thought, anybody interested in setting up a global drop in for fellow travelling Ubuntu guys? Guess it would work like people volunteer to meet with and put up a fellow Ubuntu crusader for a specified date(s). That info is held on a server (canonical?) and 'pilgrims' can plan a trip accordingly. Work in the detail but count me in.

---

### Post by mörgæs on 2010-06-17
> **bwallum said:**
> There's a thought, anybody interested in setting up a global drop in for fellow travelling Ubuntu guys? Guess it would work like people volunteer to meet with and put up a fellow Ubuntu crusader for a specified date(s). That info is held on a server (canonical?) and 'pilgrims' can plan a trip accordingly. Work in the detail but count me in.

Well, that is the Ubuntu spirit! Good idea.

---

### Post by tom.swartz07 on 2010-06-17
> **bwallum said:**
> 
There's a thought, anybody interested in setting up a global drop in for fellow travelling Ubuntu guys? Guess it would work like people volunteer to meet with and put up a fellow Ubuntu crusader for a specified date(s). That info is held on a server (canonical?) and 'pilgrims' can plan a trip accordingly. Work in the detail but count me in.

Sounds awesome! 

Maybe you could start a new thread about it in the Community Cafe, see if we could scrounge up some support for it. Im sure if we could get enough support, it should be a breeze!

---

### Post by bwallum on 2010-06-18
> **tom.swartz07 said:**
> Maybe you could start a new thread about it in the Community Cafe, see if we could scrounge up some support for it. Im sure if we could get enough support, it should be a breeze!

[http://ubuntuforums.org/showthread.php?p=9477971](http://ubuntuforums.org/showthread.php?p=9477971)

---

### Post by migs73 on 2010-06-18
Got a funny feeling a lot of Hawaiian Ubuntuers would get a rise in friend requests!!
Although not from us Scots bwallum, I think we could give them a run for their money this week in the weather stakes(but probably only this week I would think!).:lolflag:

---

### Post by tom.swartz07 on 2010-06-18
> **migs73 said:**
> Got a funny feeling a lot of Hawaiian Ubuntuers would get a rise in friend requests!!
Although not from us Scots bwallum, I think we could give them a run for their money this week in the weather stakes(but probably only this week I would think!).:lolflag:

pah, i dont care what the weather is like, I would love to visit Scotland.

---

### Post by xpod on 2010-06-19
> **tom.swartz07 said:**
> pah, i dont care what the weather is like, I would love to visit Scotland.

You and me both.
10 years living down here in London is more than enough me thinks. It`s time i went home. :p

---

### Post by bwallum on 2010-06-20
Ay, laddie, lang may ye lum reek!

EDIT
Yes indeed, long may your chimney smoke. 
(An old greeting wishing you prosperity and a long life)

---

### Post by migs73 on 2010-06-24
Go here for a translation; [http://www.dsl.ac.uk/](http://www.dsl.ac.uk/)

(by the way dsl in this case is not Damn Small Linux.)

---

