---
title: "r8169 connection drop"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by fwh on 2014-04-30
Hi people,

I have a problem with my home server running ubuntu 14.04. It is an acer laptop of a few years old containing a Realtek RTL8169 card. When I get home later tonight I can post more details. I had recently upgraded from ubuntu 13.10 to 14.04 after which the wired network connection dropped after a random amount of time and the laptop becomes unreachable. It seems to have internet connection anymore although ethtool and ifconfig say otherwise. Pinging 8.8.8.8 or my router all give the error Destination host unreachable. The annoying part is that it is seemingly random. Sometimes the connection disappears after 2 minutes after booting and sometimes it can stay up for about an hour. The only temporary solution I have found so far is rebooting the laptop, after which the behavior repeats.
When I run dmesg the output is very similar to [this]("http://lists.debian.org/debian-kernel/2013/08/msg00595.html") kernel log. As said before, when I get home I will post the exact output. 

What I have done to resolve the problem:
[LIST]
[*]Use an older kernel
[LIST]
[*]I am now running the latest kernel in the repos which is 3.13.0-24, and this behaviour did not happen with the 3.11 kernel. Booting that kernel did not solve the problem 
[/LIST]
  
[*]Use the r8168 module
[LIST]
[*]On the internet I have found that most people fixed this by not using the r8169 module, but the r8168 module. This was useless for my case because they all had the r8111/8168 card which I don't have. Tried it anyway and it dit not work 
[/LIST]
  
[*]Use the latest r8169 module downloaded from realtek
[LIST]
[*]This also did not solve problem as the behaviour did not change. 
[/LIST]
  
[*]Tried a different operating system
[LIST]
[*]I have booted the latest arch linux, under which the same behaviour occured. Therefore I think configuration issues on ubuntu are ruled out. 
[/LIST]
      
[/LIST]

So my question is this: Do you know anything else I can try to fix my problem? Or is it hardware failure?

Thanks for reading

---

