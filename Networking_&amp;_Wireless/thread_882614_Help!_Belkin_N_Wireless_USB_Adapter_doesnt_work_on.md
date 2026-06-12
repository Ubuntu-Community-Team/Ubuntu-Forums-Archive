---
title: "Help! Belkin N Wireless USB Adapter doesnt work on Hardy Heron"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by UnBr34KaBl3 on 2008-08-07
Hi, im using Ubuntu 8.04 Hardy Heron 64 bit and I'm trying to get the Belkin N Wireless USB Adapter to work (F5D8053 v3). I've been trying to use some guides but they never work.

Links to guides: [http://ph.ubuntuforums.com/showthread.php?p=5413090](http://ph.ubuntuforums.com/showthread.php?p=5413090)
                 [http://ubuntuforums.org/archive/index.php/t-638864.html](http://ubuntuforums.org/archive/index.php/t-638864.html)
                 [http://blog.vaxius.net/?p=45](http://blog.vaxius.net/?p=45)

They simply doesn't work!.
I got the files i need, rt2870.inf, rt2870.sys, rt2870.cat. I've tried to just go into System -> Administration -> ndiswrapper and then click install locate the rt2870.inf file and installed it. ndiswrapper shows that the device is present and that it is installed. But when I restart the computer it simply doesn't work. At all!

I have also been copying and pasting commands to the terminal but it doesn't work. Mainly because whenever I'm using a "cd" command to go to a folder it says it cant find it. Any ideas?

---

### Post by sonicb00m on 2008-08-07
I've also followed the guides and have no success. Despite no errors the green light never comes on and no networks are ever found. I've given up with it.

I know that doesn't help but i think it's just better and less time wasting to go and get a netgear usb adapter and be done with it.

---

### Post by UnBr34KaBl3 on 2008-08-07
The problem is that i have Windows Vista x64 aswell and the older belkin wireless g usb adapter doesnt work on my vista cuz its x64. I actually have one of them and they work like a charm on Ubuntu but not on Vista.

Found this: [http://blog.delgurth.com/2008/05/26/trying-to-get-the-belkin-f5d8053-v3-to-work-on-ubuntu-hardy-without-ndiswrapper/](http://blog.delgurth.com/2008/05/26/trying-to-get-the-belkin-f5d8053-v3-to-work-on-ubuntu-hardy-without-ndiswrapper/)

Problem is he didn't get it to work and i don't understand.

---

### Post by UnBr34KaBl3 on 2008-08-08
Please help!

---

### Post by treymok on 2008-08-08
The F5D8053 uses a rt2870 chipset. When I installed using ndiswrapper I noticed the cards performance was lacking and it would occasionally lock up requiring a reboot. I went here
 
[http://ubuntuforums.org/showpost.php?p=4808839&postcount=6]("http://ubuntuforums.org/showpost.php?p=4808839&postcount=6")

and followed these directions and now the adapter works like a charm. Only thing I noted was I had to go into Hardware Drivers and enable the adapter but after that was fine.

---

### Post by UnBr34KaBl3 on 2008-08-09
I tried it. I managed with the patch thing but i when i wrote "make && sudo make install" it says error and warning before every line. It can't make the install. And it doesnt show up in hardware drivers yet.

---

### Post by ChrisEdwards on 2008-08-11
I just bought one today and got it up and running pretty quickly on Hardy. There was no need to do a ton of command line crap, just a few lines did it. However, after re-reading I realized you're on 64 bit Hardy.

I followed the directions from [URL="http://blog.vaxius.net/?p=45"]http://blog.vaxius.net/?p=45
[/URL]too.

Note: I do need to go into terminal and "sudo modprobe ndiswrapper" every time I start up, as I haven't put it into my auto-startup. But hopefully it helps someone else Googling for help.

---

### Post by UnBr34KaBl3 on 2008-08-11
Can i reinstall the normal 32 bit hardy over the 64?

---

### Post by altonbr on 2008-10-05
It is because you need to run
```
sudo modprobe ndiswrapper
```
after every reboot, unfortunately.

---

### Post by guarnibl on 2008-11-02
You definitely have to do this after each reboot?

Is there a way to automate this? That's really, *really* annoying.

---

### Post by altonbr on 2008-11-03
No, you're right, you can set it up automatically.

Edit <tt>/etc/modules</tt> and append 'modprobe'. This will start modprobe on every boot.

You can also do this by entering the command ```
echo 'modprobe' | sudo tee -a /etc/modules
```

Hope that helps!

---

