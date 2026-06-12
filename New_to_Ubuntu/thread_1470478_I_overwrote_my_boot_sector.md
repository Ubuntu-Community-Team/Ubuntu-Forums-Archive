---
title: "I overwrote my boot sector"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by His on 2010-05-02
Oops. I overwrote my boot sector apparently. 

I was running Lucid. I have a Karmic LiveCD. How should I go about repairing the damage from this liveCD?

---

### Post by GSF1200S on 2010-05-02
> **His said:**
> Oops. I overwrote my boot sector apparently. 

I was running Lucid. I have a Karmic LiveCD. How should I go about repairing the damage from this liveCD?

We need a little bit more info than that ;)

Are you dual booting? What is the problem? Is grub giving you an error message? Is grub showing? What is the computer not doing that you want it to do?

If you have an Ubuntu Karmic LiveCD, try going to this link:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and download the bootscript to your desktop on the LiveCD. Then, do:
```
sudo bash ~/Desktop/boot_info_script055.sh
```
which will put the results in a file called RESULTS.TXT. Paste the contents of that file here in a reply.

---

