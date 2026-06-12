---
title: "Bouts of high latency over wifi with Steam in-home streaming"
date: 2019-05-25
forum: Networking &amp; Wireless
---

### Post by OpenTangent on 2019-05-25
I haven't been able to play games for months because I rely on Steam in-home streaming for various reasons. It's been working fine for years and suddenly (possibly since upgrading to Ubuntu 19.04) I get debilitating bouts of lag when streaming to my Ubuntu machine. My post on Ask Ubuntu explain it all: [Bouts of high latency over wifi with Steam in-home streaming]("https://askubuntu.com/questions/1144521/bouts-of-high-latency-over-wifi-with-steam-in-home-streaming")

---

### Post by TheFu on 2019-05-25
Wifi is very difficult to troubleshoot because the RF environment changes from msec to msec. Your other devices, neighbors, weather can all impact performance.

If it worked before, check the driver version you have installed.
Also, check the driver options.  A common issue is power management. Disable that in the driver options.

If you want more detailed help, we need more details here.  
**sudo lshw -c network** is a start. Please post the command AND output using [code tags]("https://blog.jdpfu.com/code_tags") so it looks the same here as in a terminal and everything lines up.

---

### Post by OpenTangent on 2019-06-23
I've tinkered and tested extensively, it's definitely a bug or an unwanted feature or a combination of the two, somewhere in the Ubuntu stack, could be upstream I really don't know. Streaming games is one of my primary requirements, I've waited months for this to be addressed or even acknowledged. The complete lack of interest in this problem has pushed me  to switch back to Windows after 12 years of using Ubuntu. TheFU you are the only person that has responded with anything at all. Open Source desktop operating systems are clearly dead, I'm just clinging to false hope at this point.

---

### Post by Autodave on 2019-06-23
Upgrading often causes problems like you are having.  If you can easily do it, backup everything and do a clean install of 18.04.

---

### Post by TheFu on 2019-06-23
Seems the OP didn't actually want any help.

---

### Post by OpenTangent on 2019-06-24
I already did a complete reformat and re-install of 19.04. Using 18.04 might or might not work depending on what the bug is but then I'd be stuck with an older version of Ubuntu. And to be clear what I'm really asking for is for the bug to be fixed and in order to fix the bug whoever is responsible for wifi throughput on Linux operating systems needs to acknowledge it. I'm almost certain everyone in my position is experiencing these bursts of wifi strangulation, but I am clearly in a very small minority that is live streaming with Ubuntu. As more people need to stream in real-time this bug will become more apparent and will have to be fixed. Until then, I've switched to Windows, I wish I didn't have to.

---

