---
title: "Dual Booting Windows and Mint, how do I replace Mint with Ubuntu?"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Tannn3r on 2011-07-19
Hi. I am currently dual booting Linux Mint and Windows 7. But, I want to replace Mint with Ubuntu now. However, I want to keep dual booting Windows as well. So I would be dual booting Ubuntu and Windows 7 now.

What is the best way to do this?

As I understand, when I insert the Live CD (the Ubuntu one), it'll be easy to uninstall Mint and dual boot Ubuntu and Windows instead. Is it that easy?

I don't have much experience partitioning or Linux, so I'd prefer the easiest way, if possible.

Thanks.

---

### Post by MG&amp;TL on 2011-07-19
Yes, I am fairly certain that you can easily remove the mint from the partition, and install ubuntu over it. It should have an option at the partition screen. If not, you can manually partition. Manual partitions are not difficult, but 'install ubuntu over mint' is preferable. Report back here if you want support manually partitioning.

---

### Post by oldfred on 2011-07-19
If you want to reuse the same partitions you now have use just have to use the manual install (Something else in Natty) and choose your current Mint / (root) as your new / partition. Choose format as ext4. It will find swap automatically and install. If you have a separate /home you need to choose it also but do not format it.

---

### Post by Tannn3r on 2011-07-19
> **oldfred said:**
> If you want to reuse the same partitions you now have use just have to use the manual install (Something else in Natty) and choose your current Mint / (root) as your new / partition. Choose format as ext4. It will find swap automatically and install. If you have a separate /home you need to choose it also but do not format it.

Thanks, it worked! Ubuntu was installed successfully. :)

---

