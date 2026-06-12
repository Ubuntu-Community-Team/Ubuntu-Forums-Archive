---
title: "How to boot with GRUB after installing NBR next to windows XP? still get xp bootload"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by nyponsoppa on 2010-10-12
Hello

I just installed ubuntu netbook on my netbook from a live usb that I made with the tools here. 

I did search on google and found some things related but not exactly  describing this problem, so I`ll make a post and hope for some help.

Install went fine but after reboot, the windows bootloader appears like it used to and it does not `see` ubuntu at all, so I cannot boot into ubuntu.

I did this about a year ago and then it worked.

Now I rebooted into the live usb and running from the usb (non install option) which works fine.

I`m trying to make a dual install with winxp which was already installed and chose the side by side option.


Anyway, my idea on why this doesn`t work is that I installed it as a side/by/side but on a different partition.

My hard drive before installing looked like this, not used to linux terminology im writing as Im used to seeing it in windows. 

120gb total
3 partitions
c:   20 Gb   Windows xp installed here
e:   50 Gb   cleared
f:    50 Gb    file storage

During the ubuntu install I let it clear the e: partition and then installed it there, giving 50% to ubuntu and leaving the rest as it was before.

I belive that the computer boots normally reading from c:  (I don`t understand the details) and this is why it never gets to the ubuntu things which are on part of what was previously e:


WIndows xp can boot normally and in there I can see as expected
c:  just as before
e:  now about 25Gb  
f:  as before

so half of e: is no longer visible in windows, this is obviously what I did during ubuntu install.

So my question is now: how to do either

1 from windows  install GRUB so it can boot either windows xp or ubuntu from respective partition
2 from the ubuntu live boot (which Im running right now) do the above
3 something else leading to a solution which I havent seen ocming

I`d greatly appreciate any help.


By the way, I suppose a standard thing to do would be to install ubuntu again but on c: and side by side sharing that drive with windows xp. I think that would make it possible and it is probably how it is supposed to be done.  
However, space is limited and I don`t have a reinstall disc for XP so I prefer not to mess with that one, and leave it as it is. That`s the main reason why I want to install ubuntu on a different partition.

---

### Post by Quackers on 2010-10-12
Welcome to ubuntu forums :-)
As you used a usb I suspect that grub has been loaded to the usb device and not to your hard drive.
You should be able to install grub to where it should be with the help of drs305's guide below.
Please bear in mind that if this is successful you may have to repair the windows bootloader afterwards with the windows repair cd.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

