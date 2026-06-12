---
title: "[SOLVED] internet connection sharing with ubuntu"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by allouh on 2008-08-05
hello
here is my problem with ubuntu
i installed ubintu inside a virtual machine(vmware) with a host os, windows xp.
i want the windows xp to connect to the internet and share the connection with ubuntu.
first windows xp is connected directly to the isp through pppoe.
here what i achived so far.
-when using the bridge connection, i can setup an adsl connection inside ubuntu but it will not be share with windows xp, and vice versa.
but the thing i noticed is that i can connect both os to use adsl connection even with different accounts and different ip's.
i cant use this always sine it may cause me some legal issues.
-when using NAT connection, connection sharing is working from windows xp but the problem is that i can use the p2p only(bit torrent clients) inside ubuntu and the browsing or any http protocol isnt working.
i tried dhcp with nat for ubuntu but the same problem still.
it seems the problem is in dns config.
i dont know how to configurate dns so it will work.

i hope someone can tell me where is the problem and what i can do to make the connection shared between the two os.

if anyone have another method to share the connection i hope he can suggest it.
thanks and looking for replies.

if someone can point me to a topic that can help me i will appreciate it.
***************************************************************
I managed to solve this problem with a help from the channel.
i just added this dns when using NAT connection, and problem solved.
216.17.3.121

---

### Post by dmizer on 2008-08-05
For your setup, you'll have to compile in support for NAT in vmware.  You may have already compiled it in (if you didn't make any changes during vmware's install).

You can try by going into your virtual machine network settings and change it to "NAT".

If that doesn't work, what vmware product are you using?

---

