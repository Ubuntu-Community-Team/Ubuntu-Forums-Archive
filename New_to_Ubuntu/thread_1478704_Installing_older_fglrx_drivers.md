---
title: "Installing older fglrx drivers"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by LJarvis on 2010-05-10
I recently upgraded my dell inspiron 9200 from Karmic to 10.04 Lucid. For the most part, everything works fine but since the update I have lost support for the suspend/hibernate features of the ubuntu OS. I have a hunch that it has something to do with my display driver. When I do attempt to revive my computer from suspend mode, it will continue to play my rhythmbox music, suggesting ubuntu does resume. However, with a black screen I cant really do much, forcing a manual restart. 

Im currently using the open source 'radeon' driver for my radeon mobility 9700 gfx card, the same which worked flawlessly (albeit adobe flash videos would often lag) in my former 9.10 install. Now im playing with the idea of installing the proprietary fglrx driver to remedy my problems. My only predicament is finding a way to install one of the older versions of the driver (based off the catalyst 9.2 driver, or earlier), since the current version has dropped support for my 'legacy' card.

Is there a way to install previous versions of fglrx? I haven't been able to find any information/guides on the subject, despite all my efforts. A quick and straight to the point answer would be greatly appreciated.
Thanks

---

### Post by darkstaar on 2010-05-10
The problem is that Catalyst 9.2 isn't designed to work with newer kernels. In Ubuntu's case, this means everything from 9.04 on up.

---

### Post by LJarvis on 2010-05-10
Ahh that makes sense. So I would have to install a former version of ubuntu to use the older fglrx drivers. Thanks a lot, I guess ill be using the open source drivers for the time being.

---

### Post by darkstaar on 2010-05-10
Yep. And it wouldn't be worth it just for suspend / hibernate.

That said, don't be surprised if the problem is fixed in Lucid within the next few weeks. Regressions like this often happen a short time after a new release. It's the reason that many of us wait a month or so before upgrading to the newest version.

I have one of these ATI "legacy" adapters in my laptop as well. Thankfully, the open source driver works flawlessly for me.

---

