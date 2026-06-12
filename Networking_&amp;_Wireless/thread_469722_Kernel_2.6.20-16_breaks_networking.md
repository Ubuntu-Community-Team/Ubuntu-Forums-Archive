---
title: "Kernel 2.6.20-16 breaks networking"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Unchien on 2007-06-10
When using the new kernel update, 2.6.20-16, the connection to the internet will randomly stop working for some web pages.
There is no error, but when using Firefox it just says "connecting..." at the bottom of the window and nothing happens. 
It doesn't matter if I switch browser, I've tried swiftfox also.
I've tried some solutions recommended for similar problems such as disabling ipv6 and setting "window scaling" to zero but nothing works.
The problem seems to be random. One minute you can surf e.g ubuntuforums.org just fine and then suddenly it will stop responding when you click on another topic, but you can still connect to other websites so the whole connection doesn't die.
It starts working again after some minutes of if you do a ifdown/up.

However if while in GRUB at startup I choose the previous kernel, 2.60.20-15, this problem doesn't seem to occur.
I was just wondering if anyone knows what this is and if there's a fix one the way?


UPDATE: It might have something to do with network-manager. 
I recently had to remove it(using "sudo apt-get remove network-manager") because it refused to work with my Netgear wireless USB stick. So I had to install wicd and remove network-manager.
I then tested if the normal wired network had stopped having problems when using the new kernel and it work fine now.
There have of course been some updates to Ubuntu since the new kernel, so maybe they also had something to do with it.

---

