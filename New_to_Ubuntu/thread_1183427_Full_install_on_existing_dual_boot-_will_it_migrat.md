---
title: "Full install on existing dual boot- will it migrate my pre-existing files and data?"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by SuperVectorGirl on 2009-06-10
I started with Ubuntu 9.04 Jaunty on a dual boot with Vista, and since I neither use or miss Windows Vista I would like to do a full Ubuntu install. Will the full install recognize and keep my pre-existing Ubuntu settings, files, etc.?

---

### Post by nothingspecial on 2009-06-10
I would use gparted to delete the vista partition and resize the ubuntu one. I know it says this in my tag but make sure you know what you`re doing first.

Also backup anything you don`t want to loose before you do it, just in case.

You have to do it from the live cd.

---

### Post by SuperVectorGirl on 2009-06-10
Thank you! I'm going to research it first and back up my files on a flash disk before attempting it. Many thanks!

---

### Post by Elfy on 2009-06-10
Can I just add that if you have ubuntu installed inside Vista with wubi then to do what you want you will have to do so slightly differently as wubi uses a virtual partition within windows.

[https://wiki.ubuntu.com/WubiGuide#How do I migrate to a real partition, and/or get rid of Windows entirely?](https://wiki.ubuntu.com/WubiGuide#How do I migrate to a real partition, and/or get rid of Windows entirely?)

If you didn't install with wubi then just ignore me :)

---

### Post by ikisham on 2009-07-26
Sorry for diggin' this post alive. But I would note that unless the ubuntu partition is short in space _one should keep oneself from resizing it_.

The solution here would be just reformat the ex-Vista partition and keep it for data, future test systems etc.

---

