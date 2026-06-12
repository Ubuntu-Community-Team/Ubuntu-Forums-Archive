---
title: "Bonding problem"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by methe3 on 2007-10-26
I was trying to bond three NIC's, eth3, eth4 and eth5 . Bonding came up and I was able to ping and tranfer files. I was getting throughput. Then I tried to use two cards eth3 and eth4 instead for three, then I realized that on reboot ethernet alises get changed. I configured bonding on eth3 and eth4 mii-tool output explains

eth3: negotiated, link ok
eth4: no link
eth5: negotiated, link ok

eth5 in above output is actually eth4. How can i stop bonding to change ethnet aliases while loading. I tried to edit /etc/modutils/actions but my editor was opening a new file. Please help. 

menthe3

---

