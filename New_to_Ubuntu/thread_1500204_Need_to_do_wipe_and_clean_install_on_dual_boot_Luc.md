---
title: "Need to do wipe and clean install on dual boot Lucid/Win7"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Doublehelix22 on 2010-06-02
How do I do a full wipe of Lucid without affecting my Windows setup? I'd like to do a full wipe and a clean install so I don't make more mistakes

I used the alternate installer CD to set up a dual boot with Win 7, and encrypted Lucid using instructions from the following webpage

[http://blog.nyxyn.com/2010/05/encrypted-ubuntu-104-on-dual-boot.html](http://blog.nyxyn.com/2010/05/encrypted-ubuntu-104-on-dual-boot.html)

Lucid initially installed and worked fine- except that I'd done something dumb and encrypted the home directory as well during the installation and for some reason couldn't access free space

Trying to fix it I made so many more mistakes I broke everything from grub onwards and I figure a clean install is the only way to fly, but I can't find anything too easily which will tell me how to remove Ubuntu from my system altogether ( pref without hurting Windows ). Possibly I have too much information and my head is going to explode :)

Was using Jaunty a mate set up for me-very happily too- for a year when my laptop broke. I decided to try a similar install on my new machine with Win pre-loaded, I figure if I understand what I'm doing it will help me to get more involved in the community

Hoping this isn't the dumbest question ever

Thanks for your time

---

### Post by Ozymandias_117 on 2010-06-02
Just boot to your CD and when you get to the Partitioning, do a manual partition and set your EXT4 partition as / and your Swap as Swap :P if you made more than one partition for Ubuntu, post back all your partitions.

---

### Post by Doublehelix22 on 2010-06-02
Thanks, they'd reverted back to something odd.

Am re-installing, will let you know how it goes :)

---

### Post by Doublehelix22 on 2010-06-02
Re-install works well, but I still can't mount my free space- error message shows up as [B]

Unable to mount 219GB LVM2 Physical Volume[/B]

I'll have a look around for fixes

thanks

---

### Post by Ozymandias_117 on 2010-06-03
Er... Is it partitioned as anything?

---

### Post by Doublehelix22 on 2010-07-19
Sorry for the delay in replying there, I thought I'd already replied before

I ended up giving up on this and just installed encrypted Ubuntu, wiping out Win in the process

Full install from CD worked straight out of the box and runs like a top

One day when I have more time I'll try this again but atm am massively enjoying functionality

cheers and thanks!

---

