---
title: "Marvell Yukon Ethernet not working"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by botagrox on 2005-08-15
I recently installed Ubuntu on a partition and have been unable to get the ethernet working.  The card is the Marvell Yukon ethernet adapter on the Asus P5GD2 board.  I have installed Ubuntu on my laptop (which I'm on now) with success but the hardware is older.

I installed the sk98lin driver from the website and I was able to install it (eventually).  I then tried opening a web page and that didn't work.  So I played around with the networking menu and that didn't do any good either.  I think I have installed the driver properly but I'm not sure what I need to do next to get it working or what commands I can issue to check to see if it is working.  (I've run some ifconfig commands but the response doesn't make a whole lot of sense.)  Any help or suggestions to guide me would be wonderful.

Thanks.

---

### Post by kleeman on 2005-08-15
I wrote a howto on this which might be useful for future reference:

[http://www.ubuntuforums.org/showthread.php?t=47615](http://www.ubuntuforums.org/showthread.php?t=47615)

In the meantime what do the following commands give you

sudo lsmod | grep sk98

sudo ifconfig 

(these are checking whether the module loaded and whether the interface is up)

---

### Post by botagrox on 2005-08-15
Thanks a lot for your speedy response.  I did spend a lot of time looking over your guide but I was still unable to have success using it . . . until now.  I used the sudo pppoeconf command and that didn't appear to work (or do anything) but when I restarted my computer, the internet was up and running.  I am not sure if that was the key or something else along the way.  But it works now, and I'm happy.  Thanks.

---

