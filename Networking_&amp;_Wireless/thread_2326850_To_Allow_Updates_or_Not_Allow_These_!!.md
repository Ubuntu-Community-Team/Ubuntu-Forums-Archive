---
title: "To Allow Updates or Not Allow These ?!?!"
date: 2016-06-05
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2016-06-05
If one looks under the thread "Networking", you will see abundant subject titles regarding their inability to connect via wired, wireless, and not able to connect at all since a recent update and backporting of Network Manager software.

So my question is in regards to an update received today! 
"Library for dealing with netlink sockets".
> 
Changes for libnl-route-3-200 versions:
Installed version: 3.2.21-1ubuntu1.1
Available version: 3.2.21-1ubuntu3

Version 3.2.21-1ubuntu3: 
  * Add a versioned Breaks on network-manager (<< 0.9.8.8-0ubuntu7.3~)

Version 3.2.21-1ubuntu1: 

  * Apply backported upstream patches (Closes: LP: #1511735)
    - lib-socket-use-proper-typed-constant-UINT32_MAX.patch
    - lib-socket-don-t-fail-if-no-more-local-ports-can-be.patch
    - lib-socket-retry-generate-local-port-in-nl_connect.patch
    - lib-socket-randomize-the-generated-local-port.patch
    - lib-nl-preserve-s_local-if-nl_connect-fails.patch
    - socket-clear-port-when-unable-to-generate-local-port.patch
    - socket-add-fallback-for-nl_connect-by-trying-to-bind.patch
    - socket-fix-assertion-in-nl_connect-when-all-ports-ar.patch
  * Updated symbol file libnl-3-200.symbols



After many people experiencing a myriad of problems, Words like 'randomize', 'generate', 'clear-port', 'fix-assertion', 'add-fallback',
makes me nervous! Does anyone else concur? And what does "add a versioned Break" mean??? 

If my machine's hardware/software does not seem to be affected, should I allow these "fixes"?
If my machine is not broken - why fix it?
Should we just assume and blindly trust every "fix" that comes along?
After all, thats how we got into this mess! I've spent hours and days trying to fix my wife's laptop, after she allowed the "fix/update", along with 1000's of other people.  

Don't get me wrong - I LOVE Ubuntu and specifically Xubuntu and UbuntuStudio. 
But I guess my question to everyone is, perhaps it is time to vigilantly scour every update to see if it is really needed. 
If so, then we better all start learning to "code", in order to trust and use "open sourced" OS & software.

What say You?
Rick

---

### Post by grahammechanical on 2016-06-05
We either trust or we do not trust. If we cannot trust, then it is best not to use a computer operating system. Personally, I think that you are over reacting. Still, if you want you can turn off all updates except the security fixes.We would complain if bugs weren't fixed.

---

### Post by Rick St. George on 2016-06-06
I guess then it is a "Catch 22" situation. "Damned if you do - damned if you don't". Perhaps its inevitable that somes fixes will just lead to more bugs. Until I learn to "Code", I will just have to live with it. Meantime, my wifes computer with BroadCom ethernet will just not work with Ubuntu anymore! And perhaps that is the fault of BroadCom - Not Ubuntu Coders.

But it makes me suspect to allow those updates mentioned in Post #1 on my MAIN SYSTEM. I trade everyday and make decisions worth 10's of $1,000 of dollars. I would hate to loose my ability because I chose Ubuntu over Windows. 

So ... IF I allow these updates "Library for dealing with netlink s..." (note rest of it doesn't show), and they cause a FAULT - How do I reverse the damage? Anyone have a clue?  

Maybe this should be moved to "Networking" thread.

Thanks!
Rick

---

### Post by QDR06VV9 on 2016-06-06
Thread moved at OP request.

---

### Post by Rick St. George on 2016-06-06
> **Rick St. George said:**
> 
So ... IF I allow these updates "Library for dealing with netlink s..." (note rest of it doesn't show), and they cause a FAULT - How do I reverse the damage? Anyone have a clue?  


May have found the answer to this question in Post #21 here - [https://bugs.launchpad.net/ubuntu/+source/libnl3/+bug/1511735/comments/21](https://bugs.launchpad.net/ubuntu/+source/libnl3/+bug/1511735/comments/21)

> 
after automatic update of packages libnl-3-200, libnl-route-3-200, and libnl-genl-3-200 to version 3.2.21-1ubuntu1
in my 64-bit Ubuntu 14.04-LTS the network-manager ceased working.
 /var/log/syslog shows:
init: network-manager main process (1057) killed by SEGV signal
init: network-manager main process ended, respawning
init: network-manager main process (1065) killed by SEGV signal
init: network-manager respawning too fast, stopped

 No internet connection thereafter, wire or wireless. Had to manually downgrade back to version 3.2.21-1.



Therefore, I will try the "fixes", although my networking is working fine, even with VBox.

FYI - I'm using the following;

```

lspci
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

---

### Post by Rick St. George on 2016-06-07
System running UbuntuStudio v14.04 LTS seems OK after said updates.

---

