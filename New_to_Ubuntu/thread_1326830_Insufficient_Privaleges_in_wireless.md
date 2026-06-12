---
title: "Insufficient Privaleges in wireless"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by watto_one on 2009-11-14
Hello. I am getting the above message when trying to connect my eeepc901 to home wireless network. All was OK when I went to bed last night. The message appears when I try to edit old connection or create new connection. The wireless connection is working on the windows and Mac computers in the house.
using UNR 9.10.   Thanks for any help available

---

### Post by Jon Monreal on 2009-11-14
I'll see what I can dig up about this problem. For now, this might prove useful: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/448002](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/448002).

EDIT: Try typing into the terminal "sudo nm-connection-editor". This allows you to edit your connections with elevated privileges, and so should avoid the problem. Remember to always take precautions when using sudo, and try to be aware of what commands do before you type them in.

---

### Post by watto_one on 2009-11-16
Thank you for your assistance. I will try this when I get home. Am reading the bug report now.

---

