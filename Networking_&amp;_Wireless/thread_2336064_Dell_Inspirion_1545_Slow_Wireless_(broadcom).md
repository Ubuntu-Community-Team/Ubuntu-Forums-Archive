---
title: "Dell Inspirion 1545 Slow Wireless (broadcom)"
date: 2016-09-04
forum: Networking &amp; Wireless
---

### Post by 1200n on 2016-09-04
[COLOR=#000000]*Installed Ubuntu Friday night. Everything works well except the wireless adapter.  The wired connection is fast. Wireless is slow.*[/COLOR]

[COLOR=#000000][I]Followed the the instructions on the sticky thread regarding the Broadcom posted by chili555.
[/I][/COLOR]
unfortunately, still slow.

TLDR:

[COLOR=#000000]*Ubuntu 16.xx, dell Inspiron 1545 (Broadcom). Wired = fast. Wireless = painfully slow.*[/COLOR]

[COLOR=#000000]*help please?*[/COLOR]

---

### Post by chili555 on 2016-09-04
I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Post back with your results.

---

### Post by 1200n on 2016-09-04
Much better. Thank you! How do I mark this thread as SOLVED?

---

### Post by chili555 on 2016-09-04
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

