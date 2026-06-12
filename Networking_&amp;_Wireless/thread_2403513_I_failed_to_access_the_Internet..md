---
title: "I failed to access the Internet."
date: 2018-10-12
forum: Networking &amp; Wireless
---

### Post by matthew-wai on 2018-10-12
I failed to access the Internet.
```
matthew@matthew-pc:~$ sudo pppoeconf
[sudo] password for matthew: 
Plugin rp-pppoe.so loaded.
matthew@matthew-pc:~$ plog
Oct 11 23:48:59 matthew-pc pppd[4471]: Plugin rp-pppoe.so loaded.
Oct 11 23:48:59 matthew-pc pppd[4472]: pppd 2.4.7 started by root, uid 0
Oct 11 23:49:05 matthew-pc pppd[3235]: No response to PAP authenticate-requests
Oct 11 23:49:05 matthew-pc pppd[3235]: Connection terminated.
matthew@matthew-pc:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
Is "System Files" missing from "Home Folder" in the screenshot below?
I could not find "/etc/ppp/peers/dsl-provider".

[https://ubuntuforums.org/attachment.php?attachmentid=281306&d=1539257609](https://ubuntuforums.org/attachment.php?attachmentid=281306&d=1539257609)

---

### Post by ajgreeny on 2018-10-12
I can not help much with your internet problem and I think we will all need a lot more information to be able to give you any help.

[LIST=1]
[*]What hardware do you have?
[*]Why do you have **pppoeconf** installed as it is not normally needed on a desktop machine; network-manager does the full job?
[*]Is this a wireless or cable network connection that you have the problem with?
[*]If wireless see **Wireless-info** in my signature below, download it and run the script, then report back the output here or using [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) if the output is too large to add direct. One of our wifi experts will hopefully be able to suggest a solution.
[/LIST]


The lack of the filesystem showing in the file manager is simply because you have not added it to the Places (or bookmarks) that show in the left pane.  If you change to **Tree-view** instead of Places it might show, or you can click twice on the up arrow (next to the home icon) to get there and then add that as a bookmark if you wish.
However, please do not start manually editing system files unless you know exactly what you're doing and why otherwise you may be back here again having killed the system completely.

---

### Post by matthew-wai on 2018-10-13
> **ajgreeny said:**
> What hardware do you have?
RTL8168/8111 on GA-H81M-DS2.
> **ajgreeny said:**
> Why do you have **pppoeconf** installed as it is not normally needed on a desktop machine; network-manager does the full job?
A few days ago, I successfully set up a PPPoE connection via "pppoeconf". See [https://ubuntuforums.org/showthread.php?t=2386971&page=4&p=13807165#post13807165](https://ubuntuforums.org/showthread.php?t=2386971&page=4&p=13807165#post13807165)
Two days ago, I failed to do the same. I am sure I can do the same by re-installing Lubuntu, but is there an alternative?
> **ajgreeny said:**
> Is this a wireless or cable network connection that you have the problem with?

A cable network, which I am now using on Windows 10.

---

### Post by matthew-wai on 2018-10-14
Three days ago, I selected "Windows Recovery Environment" out of curiosity and an error message appeared. Then I pressed a key to continue and let it boot into Lubuntu as usual. But then I failed to access the Internet.

---

