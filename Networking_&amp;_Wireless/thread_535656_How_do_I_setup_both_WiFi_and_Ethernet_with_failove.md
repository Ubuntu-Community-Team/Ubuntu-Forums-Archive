---
title: "How do I setup both WiFi and Ethernet with failover?"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by hyperq on 2007-08-26
I've already figured out how to setup my WiFi and crossover ether network and they are working fine.  Now I want to setup a failover ip of the same hostname.  So when I ping the desktop from laptop, the laptop will be looking for 192.168.100.10 when the corssover cable is connected.  If I disconnect the crossover cable, when I ping the desktop, the laptop should be looking for 192.168.1.10.  Do you know how to set this up?

Here are the details:

I have a desktop and a laptop, and both of them are running Ubuntu 6.06.1 LTS.  Both are configured to use WiFi to surf the web.  Desktop wlan0's static ip is 192.168.1.10, and the static ip on laptop's wlan0 is 192.168.1.20.

I then connected the ethernet port on each computer with a crossover cable to transfer large files.  The software configuration was simple.  All I did was installing Firestarter on each computer, run its setup wizard, and then turned on internet connection sharing when prompted.  Desktop eth0's static ip is 192.168.100.10, and the static ip on laptop's eth0 is 192.168.100.20.

I added the following two lines in /etc/hosts on desktop
192.168.1.10  desktop
192.168.100.20 laptop

I added the following two lines in /etc/hosts on laptop
192.168.100.10  desktop
192.168.1.20 laptop

Everything works great.  I can transfer large files in between two PCs and both can access internet.  Here comes the problem.  When I disconnect the crossover cable and move the laptop to another room, I can no longer access desktop from it.  I can manunally change the hosts files and firewall settings on each computer, but that is a pain if I have to do that everytime.  

What should I do so the laptop will be searching for 192.168.100.10 and 192.168.1.10 when I ping the desktop?

---

### Post by ankorie on 2007-08-26
I am not sure if this will help much but here it goes...
In your /etc/hosts file you can change it to:

192.168.1.10 desktop
192.168.100.10 xoverdesktop
192.168.1.20 laptop
192.168.100.20 xoverlaptop

This way when you ping desktop it uses wlan0 and when you ping xoverdesktop it will use eth0
This should work but I think there might be another way.
Hope it helps.

---

### Post by hyperq on 2007-08-26
I have thought about that, but it still doesn't solve the problem.

Because I am using NFS to transfer large files, the hostnames of desktop and laptop are saved in the /etc/fstab files on both computers.  So when each computer is rebooted, it will auto-mount the NFS shared folders from the other computer.  Then I can easily drag and drop files using the file manager.

I want to be able to keep draging and dropping files between two computers whether they are using crossover or wifi.  So it should use ethernet if the crossover cable is present, wifi if the cable is not there, while using the same hostname specified in the /etc/fstab file.

---

### Post by ankorie on 2007-08-27
a quick Google search yielded these results [http://groups.google.com.au/group/comp.unix.questions/browse_thread/thread/323528cfbc899190/45667f0a1ae31120%2345667f0a1ae31120?hide_quotes=no]("http://groups.google.com.au/group/comp.unix.questions/browse_thread/thread/323528cfbc899190/45667f0a1ae31120%2345667f0a1ae31120?hide_quotes=no")

in summary you can have multiple ip addresses tied to one host name so your /etc/hosts will look like....

```
192.168.1.10 desktop
192.168.100.10 desktop
192.168.1.20 laptop
192.168.100.20 laptop
```

let me know if this works for you
Cheers
Ank

---

