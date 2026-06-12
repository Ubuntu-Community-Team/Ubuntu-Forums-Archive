---
title: "Driver for TP link Archer T2u on Ubuntu 18.04"
date: 2019-12-02
forum: Networking &amp; Wireless
---

### Post by victor131490 on 2019-12-02
@darwinclown how did you get it working? i am having the same problem as you.

Possible reference: [https://ubuntuforums.org/showthread.php?t=2430134](https://ubuntuforums.org/showthread.php?t=2430134)

---

### Post by DuckHook on 2019-12-02
Welcome to the forums, victor131490;

Your post has been moved to its own thread with a new title. Also, just a friendly reminder not to hijack threads. Unrelated problems can sometimes manifest with similar symptoms. You are diluting forum help and denying both yourself and the OP individual attention by hijacking OP's thread.

If you feel that the OP's issue/solution is relevant to your problem, feel free to link to it as follows: [https://ubuntuforums.org/showthread.php?t=2430134](https://ubuntuforums.org/showthread.php?t=2430134)

With respect to your problem, are you certain that you are using exactly the same adapter? As you can see from the OP's first post, s/he included *lsusb* output to precisely ascertain the exact device. You should do the same before assuming that you have the same problem.

Assuming that your problem is exactly the same, it is doubtful that the OP can give you any clearer instructions than those issued by praseodym and jeremy31. Please carefully read the combination of praseodym's and jeremy31's instructions. Admittedly, they are intertwined with an unneeded redundancy that can be eliminated. If I read their combined instructions correctly, the proper instruction set is:```
sudo apt install git dkms build-essential
git clone https://github.com/jeremyb31/rtl8812au-1.git
cd rtl8812au-1
git pull
sudo ./dkms-install.sh
```

***CAUTION***

It is not normally advisable to download and install scripts willy-nilly from unknown sources you are just pointed to on the Internet. However, both praseodym and jeremy31 are gurus who have been on this forum forever and jeremy31 is a fellow staff member. It is your decision whether these credentials are sufficient to alleviate your security concerns.

---

