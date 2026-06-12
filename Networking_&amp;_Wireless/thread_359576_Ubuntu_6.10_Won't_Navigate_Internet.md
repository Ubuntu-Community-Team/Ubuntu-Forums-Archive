---
title: "Ubuntu 6.10 Won't Navigate Internet"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by glenndrayton on 2007-02-12
I see a number of unanswered posts along these lines, but this problem is BIG and deserves a new post.

We are having problems with 6.10 (Edgy Eft) - although I see posts about most releases. We have tried four computers, complete install, some inside vmware, others just full install of Unbuntu only. Some with DVD ISO image some with CD ISO image.

In all cases the ethernet (wired) appears configured fine, and we can ping anywhere (inside and out - and I mean anywhere), but firefox won't navigate to any pages (connection times out) and Synapics will not download any information. In other words the install is completely useless as it won't do anything related to the iNet except ping.

What is going on here? Why is no one coming to the party with a fix? I've talked to two other users online and they are stuck with no inet browsing as well.

We're a pretty serious software company looking to support Linux, but this is SHOWSTOPPER. This problem needs immediate resolution, its a bl**dy joke!

---

### Post by mips on 2007-02-12
Two possibilities, DNS & IPv6

I'll leave the searching up to you ;)

---

### Post by glenndrayton on 2007-02-12
Thanks, I will do some searching.

Even more interesting is that we just tried Fedora Core 6 and got exactly the same issue, so this is a generic issue with the networking in Linux that does not appear on Windows (note we have tried two locations with different network setups and got the same result).

Must admit its very discouraging. I expected iNet to work out of the box.

---

### Post by sumgi on 2007-02-12
> **mips said:**
> Two possibilities, DNS & IPv6

I'll leave the searching up to you ;)

Wow that is a really lame answer.

Here are some network [resources]("https://help.ubuntu.com/community/NetworkDevices").

Also tail your system logs

tail -f /var/log/messages

Here is a good list of general purpose [URL="http://www.ubuntuforums.org/showthread.php?t=232059"]links
[/URL].

---

### Post by glenndrayton on 2007-02-12
Good news!  This problem is resolved.

I discovered that if I tell firefox to navigate directly to the google IP of [http://66.102.7.147](http://66.102.7.147) then it worked fine. So this suggested that the timeout problem I was having was DNS related.

All I had to do was change the DNS listing to put my ISPs DNS server (in this case 61.9.226.33 which is BigPond Australia) in instead of my router's IP (10.1.1.1 which is the default - and what normally works under Windows).

i.e. step-by-step:

1. Open System/Administration/Networking
2. On the DNS tab
3. Delete the IP of the router
4. Add the IP of the ISP (which I got my logging into the router and looking up the DNS server it was using).

This solution is dead-simple but it has taken nearly a week to find it. Maybe this can be put in a FAQ somewhere for easier resolution. I guess it relates to current Linux releases running through a router to a broadband connection.

---

### Post by mips on 2007-02-13
> **sumgi said:**
> Wow that is a really lame answer.[URL="http://www.ubuntuforums.org/showthread.php?t=232059"]
[/URL].

Why ? It pointed him in the right direction after all. 

Some individuals have initiative and will follow up on those key words. Others expect to be spoon fed and won't even follow up on that. I tend to try and help those that want to help themselves.

I'll keep you in mind....

---

### Post by mips on 2007-02-13
> **glenndrayton said:**
> 
This solution is dead-simple but it has taken nearly a week to find it. Maybe this can be put in a FAQ somewhere for easier resolution. I guess it relates to current Linux releases running through a router to a broadband connection.

Did you search for the right thing as there are many posts on this issue and I myself have posted responses to this on numerous occasions. One just gets tired of repeating the same thing over & over again.

---

