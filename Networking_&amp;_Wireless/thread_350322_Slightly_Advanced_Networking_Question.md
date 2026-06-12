---
title: "Slightly Advanced Networking Question"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by crackotter on 2007-01-31
Hi all,
 I have a slightly advanced Ubuntu networking question. I need to create a virtual interface within ubuntu. the problem is I do not want this interface to have the MAC address of any other interface in my box. I am hoping I can do some magic in /etc/networking/interfaces to make this happen. I am looking for either (or both) of these two solutions

1) True virtual/loopback interfaces - looking to create a loopback interface other than 'lo'. How would I go about doing that

2) Creating alias interfaces (i.e. eth0:0) which have a different mac address than the physical (i.e. eth0) interface.

Hopefully some one has a answering or can atleast point me in the right direction.

-Otter

---

### Post by Paerez on 2007-01-31
[http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm)

Search for the text "virtual interface". The section you want is about 2/3 of the way down the page.

---

### Post by crackotter on 2007-01-31
Thanks for the post, but unfortunately the link doesn't help. The virtual interfaces they describe are "aliases" which use the same MAC address as the interface they are linked to. I wonder if I could assign a mac address to the 'lo' interface. Then the MAC would be differnt than the cards.

-Otter

---

