---
title: "backing up files from live usb, over network to windows"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by REMIX8604 on 2011-03-29
so heres the deal. my friend gave me his laptop that his girlfriend broke in half. thats right, in half :P screen separated from the base.

I could use the ram and hard drive but first i need to back up his music collection that is around 130 gigs. so i took his hard drive out and dropped it in my netbook. i started it with a live usb but i am having trouble transferring the music files to a windows laptop.

what is a simple way to do this?

would just making a crossover cable work? is it possible to directly connect the to laptops with a regular ethernet cable? or should i just hook both up to a router?

---

### Post by rosencrantz on 2011-03-29
Do you have a proper crossover cable or just the standard ethernet (different wiring)? In the latter case, you need a router.
You also need samba on the linux machine and you'll have to figure out the IP adresses. Try this link [http://ubuntuforums.org/showthread.php?t=794799](http://ubuntuforums.org/showthread.php?t=794799)
On the other hand, couldn't you just connect the drive directly to the Windows machine? (provided you have an external enclosure; with SATA laptop drives, both the 2.5'' and 3.5'' work)
If the file system is ext, you could try the ext2read or ext2fsd drivers - they should work even with external hard drives.

---

### Post by Immolatus on 2011-03-29
Wow, this sounds like fun.....I think I'd just yank the hd out and plug it in to a desktop and transfer the files directly via router (convenient but slow). Do you know anything about ssh? Or maybe just plug an external monitor into the busted machine (proly faster than the netbook), most nowadays have VGA outs; just to see what your doing(unless it wont boot). If it wont boot then strait across the router I'd think best on acount of the more you transfer a file the more chance of corruption.

---

### Post by REMIX8604 on 2011-03-29
i dont have a cross over. but if its easy that way i will rewire one of my short cables. i was having a bit of trouble installing samba on the live usb. not sure why. there were a few different options when i searched for samba in the software center also. maybe i chose the wrong one? 

with the VGA cable, i thought i would have to change a setting in the OS. or does the computer auto detect the VGA on start up?

the samba and router idea... i connect both laptops to a router. load samba and open a folder on the windows laptop then drag n drop?

i think my main problem is in using samba. either im trying to install the wrong one or i am just confused after viewing to many tutorials. maybe sombody can direct me to one that will suit my needs. thanks guys/girls

---

### Post by rosencrantz on 2011-03-29
For the VGA cable, just try it. On some laptops, autodetect on startup works - although I'm not quite sure how this is going to help with your transfer problem (or does the broken machine run on Windows as well?)
Right now, I can't test networking, as I have neither a router nor a Windows machine available, but I'm pretty sure you need the samba client (package smbclient). I see no reason why it should not work from a USB drive. 
If that doesn't work, you can always try it the other way round with ssh, like Immolatus suggested. The most common Windows ssh client is PuTTY. However, this is probably less intuitive.

If you feel comfortable rewiring network cables - I wouldn't know how to do it without breaking the plug ;-) - do it, but using a router should be pretty easy, too.

---

### Post by collisionystm on 2011-03-29
What are your resources? Do you have a router, or a switch? Just plug both computers into it. Static assign the IP's if you are not getting dhcp. Make a music folder on windows, right click, share, set to everybody

on the netbook, browse to the windows computer and just copy and paste one folder to the other.

Even if you crossover, you need to make sure you statically assign an ip address to each computer.

---

### Post by REMIX8604 on 2011-03-30
yes router. ok i got it. finally. i installed samba. enabled sharing on the windows PC. connected both to a router. from the windows laptop i could see the ubuntu and the shared folder but got an error every time i tryed to open it. so from my linux usb/netbook combo, i opened the windows network and was able to transfer files that way.

  although i was able to complete my task. i dont understand why i could not connect from the windows.

---

### Post by rosencrantz on 2011-03-30
Aaah, don't delve too far into the mysteries of Windows networking - hic sunt dracones...

---

