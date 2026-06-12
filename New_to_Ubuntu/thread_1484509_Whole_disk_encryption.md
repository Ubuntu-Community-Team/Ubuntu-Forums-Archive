---
title: "Whole disk encryption"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by eddski on 2010-05-15
I wanted to know if I can encrypt an entire dual-boot disk with ubuntu and xp? is it difficult, time consuming, etc.

---

### Post by ubudog on 2010-05-16
Yes, but I don't believe you can dual boot.  You will need an alternate install disk (available from releases.ubuntu.com) and boot from that.  It shouldn't be that hard - I have it like that right now (without Windows dual boot though) It was very easy to set up.  Just took a little longer to install (set aside at least an 1.5 hours)

---

### Post by frostschutz on 2010-05-16
You can encrypt Linux and Windows separately, using dmcrypt / LUKS for Linux, and TrueCrypt for Windows. You could also choose to use TrueCrypt for Linux, but... it's really only popular with Windows users since they don't have anything else. However if you want to be able to access your Windows data from the Linux side, you'd have no choice but to use Linux TrueCrypt for that as well... so...

Personally I only encrypt the Linux side of things since that's where I keep all my mail and work, whereas I use Windows for gaming only, which does not require encryption, and would probably even cost me some valuable performance in games... so it'd be impractical to encrypt it really.

---

