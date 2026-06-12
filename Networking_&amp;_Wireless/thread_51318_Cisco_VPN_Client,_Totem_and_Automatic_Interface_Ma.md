---
title: "Cisco VPN Client, Totem and Automatic Interface Mapping"
date: 2005-07-23
forum: Networking &amp; Wireless
---

### Post by jonspinks on 2005-07-23
Hi,
This is more of an observation than anything.  I was just wondering if anyone else had seen similar behaviour.  Basically I was helping a friend get the Cisco vpnclient application running as it worked fine on my laptop.  Basically what would happen was as soon as we had dialled in we would fire up the vpnclient application (obviously with the kernel modules loaded).

However on his system the application would just sit there and not do anything.  It reacted the same way even if the Cisco VPN module was loaded into the kernel or not.  This is strange as it's first port of call is to check whether the module is loaded.  So it was actually hanging somewhere before that.

During our investingations my friend noticed that when he was at home the application didn't hang.  When we were using his laptop at work it would hang but at home on the same dialup connection it wouldn't.

We then noticed another application going a bit funny when we were at work.  Totem would start up and then quit.  Starting it from the command line we could see it was complaining about a missing network connection.  This is strange as it shouldn't quit if the box isn't online.

Anyway we eventually narrowed the problem down to the fact that on the startup when I was using the laptop I was pressing CTRL+C during the boot process whilst the system was trying to bring up a non-existant interface.  My friend wasn't doing this he was just waiting for it to time out.  Therefore the Cisco VPN client and Totem were working at his home but not at work (where I was using it).

My laptop doesn't sit trying to configure interfaces which don't exist because I have commented out the 'auto' options.  However even with them gone his laptop still paused trying to bring up eth0 becuase of the automatic mapping functions which are present in the interfaces file.

So I guess my question would be (if there is one here) why does the automatic mapping in the /etc/network/interfaces file try and bring up eth0 everytime.  This is just a pain in the bum as it increases load times.

Thanks (sorry for the novel)
Jon

---

