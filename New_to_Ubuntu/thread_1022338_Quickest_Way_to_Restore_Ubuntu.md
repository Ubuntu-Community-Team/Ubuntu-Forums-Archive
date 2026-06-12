---
title: "Quickest Way to Restore Ubuntu"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by jdpearson on 2008-12-26
Let's say I needed to blow away my PC and reinstall Ubuntu.  Maybe I need to install a larger HD.

In the Windoze world I'd look to something like Ghost to image my computer.

I just tried PING (Partimage is not Ghost) but it took over 4 hours to image my 100GB drive (w/ just 40 GB of data).  I could reinstall Ubuntu in just 20.

If I've used the Quickstart to backup my Home and config files would that work?  Just reinstall Ubuntu and then restore those files?  I'd assume though, that I'd have to reinstall all my appys.

Just looking for suggestions.

Thanks.

---

### Post by ercferret18 on 2008-12-26
The way I do it is just backup all my files and reinstall. that way you are getting rid of all the stuff you don't want and keeping the stuff you do want.

---

### Post by kansasnoob on 2008-12-26
Gosh I've used Partimage a lot and really find it simple and straight-forward:

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by jerome1232 on 2008-12-26
That's what I do too, I just backup my /home to an external drive using rsync in a small script. It auto runs when I attach my external drive.

---edit--- 4 hours seems like an awfully long time... partimage has options to ignore free space and such are your sure you selected those.

---

### Post by jdpearson on 2008-12-26
> **jerome1232 said:**
> That's what I do too, I just backup my /home to an external drive using rsync in a small script. It auto runs when I attach my external drive.

---edit--- 4 hours seems like an awfully long time... partimage has options to ignore free space and such are your sure you selected those.


Nope, I'm definitely not sure that I chose that option.  First time using it and all.

---

### Post by kansasnoob on 2008-12-26
> **jerome1232 said:**
> That's what I do too, I just backup my /home to an external drive using rsync in a small script. It auto runs when I attach my external drive.

---edit--- 4 hours seems like an awfully long time... partimage has options to ignore free space and such are your sure you selected those.

For that matter since I keep very little data on my internal drive anyway, I frequently just make a folder in another OS's Home and store what I want until I've reinstalled the OS I want to, but I like lots of options:

[ATTACH]97697[/ATTACH]

You see for instance sda10 is /home for Mint 6. I could create a folder named "Mint stuff" in Ubuntu 8.04 on sda5 and transfer the stuff I wanted to keep for Mint into that folder and fairly easily transfer it back to a new Mint 6 (or another OS) if I wanted to.

But if I'm replacing a hard drive I like to use Partimage to copy everything to an external drive, and then restore it all to the new drive. Of course if you're reinstalling to a larger drive some repartitioning will be necessary afterwards!

Then I prefer Gparted, and I do NOT like to stack up too many changes at once!

---

