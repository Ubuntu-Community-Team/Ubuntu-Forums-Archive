---
title: "WEP key index"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by balloniw on 2006-11-02
A couple of quick questions about wireless keys and the key index. In my wireless environment it would appear that I need to use a key index of 2 for my 128-bit WEP key. In Windows, if I specify any key index other than 2, I don't get an IP address. So the first question is, what is the key index and how is it used?

In Edgy, I am trying to use key index 2. If I manually issue the command "iwconfig eth1 key s:<my-ascii-key> [2] open", and then "iwconfig eth1 key [2], I see my key listed as index 2. And I get an IP address (after issuing "ifdown eth1; ifup eth1")! Problem is, in the network settings applet I see no way to specify the key index. How do I configure *and* select a key index of 2 using the network settings applet? Can /etc/network/interfaces be modified so that the wireless-key specification can contain the key index? Is there any good documentation for all the wireless-xxx directives that can be used in the interfaces file?

Thanks for any help,

Bill

---

### Post by balloniw on 2006-11-03
Well, some more digging and I think I have an answer to the question of how the key index is used. The index is transmitted with the encrypted message. The receiver then looks-up the key corresponding to the transmitted index and uses it to decrypt the message.

I still have no idea how to configure wireless on Edgy to use key 2. If I manually issue "iwconfig eth1 key [2]" my wireless works. But I can't see  any way to do this configuration in the network settings.

Any and all help here will be much appreciated!

Bill

---

### Post by dulljeff on 2006-11-12
Hi Bill,

if that is still an issue for you, you may wanna try the setting in the last post of this thread: [http://ubuntuforums.org/showthread.php?t=293444&page=2]("http://ubuntuforums.org/showthread.php?t=293444&page=2")

---

### Post by balloniw on 2006-11-15
dulljeff,

Thanks so much for taking the time to reply. The wireless-key2 and wireless-defaultkey items from that post worked great! I can now boot and have wireless (Broadcom no less) running with no intervention. Ubuntu is now my fav distro.

---

