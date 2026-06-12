---
title: "network manager default network?"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by madcap_magician on 2006-07-17
Is it possible to set a default wireless network with network manager?

My laptop picks up 2 signals, an open network and my encrypted network.  When network manager starts it always defaults to the open network and also rewrites the resolv.conf file.  

I have to manually switch networks and then I use a shell script to rewrite resolv.conf.  Doing this every time I turn on my laptop is getting to be a pain.  Is there any way I can specify a default network or give priority to one network over another?  I've set up network manager to no longer require a password for connecting to secure networks but it still defaults to the open network.

Any advice would be appreciated.

---

### Post by madcap_magician on 2006-07-29
It's been a week and no one has commented.  Thought I'd give it another try.

---

### Post by That Other Guy on 2006-07-29
I'd like to know, too.  Also, can I get network manager to remember the WPA2 password?  It may be less secure, but on the other hand, it's a pain to re-enter it every time.

---

### Post by teimu on 2006-08-02
yes. i am having the same problem. my machine also connects to the wrong network. the little wireless applet on the panel has no options to configure either. i dont know where to start. :cry:

---

### Post by akwatve on 2008-02-07
I too have the same problem. knetworkmanager simply does not let me choose preferred network. I tried declaring other networks un-trusted. I even removed them from the list.But no success.
In fact, after I recently upgraded knetworkmanager, it has stopped connecting automatically to a wireless network. Everytime I have to explicitly ask it to connect to wireless network which is stupid...... Is no one bothered about knetworkmanager's problems?

---

### Post by tylerious on 2008-05-25
I'm using Gutsy right now and am also having this problem. This is NetworkManager 0.6.5.

I think Hardy uses NetworkManager 0.6.6, but don't quote me on it. Not sure if that has similar issues. I won't upgrade until I know Hardy will work correctly.

Fedora 9 uses NetworkManager 0.7.0, which lets one right click on the panel applet and setup which wireless networks to connect to. I guess it makes sense that Fedora has the most up-to-date version since the program is maintained by Red Hat. ;)

---

