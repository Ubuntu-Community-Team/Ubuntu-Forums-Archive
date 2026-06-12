---
title: "[SOLVED] Network performance - ISP filtering?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by cgitz on 2008-04-03
I have a laptop running 8.04, a laptop running 7.10 / XP dual boot and a server running 7.10.  All three computers can connect to the Internet but have very slow connections.  Updates, for example, average about 1 Kbps.  If I boot the 7.10 laptop into Windows XP, and try to download the same file from the Ubuntu update servers using Firefox, I get normal speeds (30-60 Kbps for me).  If I try to download the file while running Ubuntu on any of the computers I only get about 1 Kbps.  My CentOS servers seem unaffected - they can retrieve updates at normal speeds.

I have searched for solutions to this problem for well over a month and I'm at a loss.

Things I've tried:
[LIST]
[*]Disabled IPv6.
[*]Set the MTU to 1450 (though XP uses an MTU of 1500).
[*]Tried wired and wireless connections.
[*]Switched access points.
[*]Switched my gateway router.
[*]Tested my laptop at another location (works fine).
[/LIST]

Speedtest.net showed that my upload speeds on Ubuntu and Windows XP are virtually identical.  It is only the download speed that is affected on Ubuntu.

My best guess is that it is filtering at my ISP.  What could they filter that would target Ubuntu traffic, not XP traffic?

Thanks.

---

### Post by The Cog on 2008-04-03
Interesting. Can you take about 30 seconds of packet capture and post the file here as an attachment? The command I'm thiking of is:
**sudo tcpdump -i eht0 -w capture1**
That file will open in wireshark which might reveal the problem.

---

### Post by cgitz on 2008-04-03
Thanks for the reply.

I ran the tcpdump on my 8.04 laptop.  Unfortunately, I don't have wireshark installed.  10MB of downloads will take all night at 1Kbps  :)

I attached a tcpdump capture (approx. 30 sec).  I started Update Manager and began downloading updates.  After a few seconds I started the tcpdump:

**sudo tcpdump -i wlan0 -w capture1**

wlan0 is my wireless adapter - an ipw3945 using the iwl3945 kernel driver (2.6.24-12).  Like I said before, though, there is no difference between wired and wireless and my laptop runs at full speed within my network.

Thanks again.

---

### Post by The Cog on 2008-04-04
That's wacky. Looking at the trace, your laptop is only offering a window size of 46 bytes. It is saying to the server "Only send me 46 more bytes" every time it acknowleges a packet. The server is sending a little more than this (92 bytes) but normal packet sizes for this kind of transfer are over 1400 bytes. It looks to me as though your laptop is causing the problem. 

I can't believe this is normal. The fact that the same PC on a different site is fine seems very strange. It sounds as though something at that site is provoking the Ubuntu TCP stack into behaving oddly, but I can't imagine what.
It would be very interesting to get traces of the start of the download both with the misbehaving laptop and either that lappy elsewhere or the centos box, to compare the difference in their behaviours (getting the same file from the same server). Maybe we can see something triggering the reduced window. The fact that the wireless is the same kind of rules out ethernet problems like a duplex mismatch.

---

### Post by cgitz on 2008-04-04
I went to my other site and downloaded wireshark - very nice program - thanks for the suggestion.  I also did a capture while installing updates.  I was using a wired connection, though (no wireless here).

**sudo tcpdump -i eth0 -w capture-eth0-1**

At this site my window got as high as 5790 (during the segment I captured) with data rates averaging about 350 Kbps.

When I get home, later, I will run some more captures - try to catch the beginning when the window size is being set.

---

### Post by cgitz on 2008-04-04
Cog,

Your last reply put me on the right track - the small window was the problem.  Using that, my search turned up several other threads in these forums with users having similar trouble.  The problem has to do with routers that do not handle window scaling properly.

There were a couple threads with the solution.  I found this one to contain the clearest explanation:
[http://ubuntuforums.org/showthread.php?t=443209&page=2]("http://ubuntuforums.org/showthread.php?t=443209&page=2")

The thread above also contained the following link to an excellent explanation of the problem:
[http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/")

I will post the fix I used in case someone hits this thread, first.

**Option 1:**

Modify /etc/sysctl.conf and add the following line:
```
net.ipv4.tcp_window_scaling = 0
```

Then reload the kernel parameters from sysctl.conf:
```

sudo sysctl -p

```

**Option 2:**

Modify /etc/sysctl.conf and add the following lines:
```

# Uncomment the following line if switching from option 1 to enable window scaling again
#net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

```

Then reload the kernel parameters from sysctl.conf:
```

sudo sysctl -p

```


I've flipped briefly between the two settings and option 2 seems to be a bit quicker for me.  Either option fixes the problem and switching between the two is easy enough - I may do further testing.

Thanks, again, for your help, Cog.

---

### Post by The Cog on 2008-04-05
Thanks for the explanation. I have learned something too - I didn't know about window scaling. There was no such thing when I learned about TCP.

---

