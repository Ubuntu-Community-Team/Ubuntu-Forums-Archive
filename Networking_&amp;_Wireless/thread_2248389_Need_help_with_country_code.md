---
title: "Need help with country code"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by Grone1985 on 2014-10-14
Hi,
I'm creating this thread as suggested by Bucky in my other thread [here]("http://ubuntuforums.org/showthread.php?t=2248279"). This time I need help setting the country code and some IPv4/IPv6 settings as suggested by Hadaka. Thanks!

---

### Post by Vladlenin5000 on 2014-10-14
Why didn't you ask in that same thread?

---

### Post by Hadaka on 2014-10-14
Hi,please open a terminal and do..
Please COPY and paste to avoid typo.
to view current stetting..do
```
cat /etc/default/crda 
```
to set US do..
```
sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
to also view.
```
sudo iw reg get
```
and to set US do.
```
sudo iw reg set US
```
please set your IPv4 and IPv6 network mgr settings to match the attached
[ATTACH=CONFIG]257211[/ATTACH][ATTACH=CONFIG]257212[/ATTACH]

---

### Post by Grone1985 on 2014-10-14
Thanks for all your help Hadaka! Internet seems faster now and wifi is working flawlessly.

Cheers!

> **Vladlenin5000 said:**
> Why didn't you ask in that same thread?
Seriously? The first sentence in my post says why.

---

### Post by Hadaka on 2014-10-14
Great ! Please mark this solved.

---

