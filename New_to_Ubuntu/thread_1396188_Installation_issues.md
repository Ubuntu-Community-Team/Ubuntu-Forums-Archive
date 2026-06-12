---
title: "Installation issues"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by MixelPixOrItDidntHappen on 2010-02-01
I dont really need a sex change.

The install process of unbuntu has kinda skewed my opinion of Linux. I'm getting the type of error you'd expect from DOS5 or Windows 3.X

"No root file system defined."

So, I define it in the mount field as boot. No change. Someone mentioned to define it as ROOT... that option, doesn't even appear on the list.

So far, the way of IT's future is reminding me considerably of IT's horrible past.

Any suggestions?

---

### Post by Vaphell on 2010-02-01
are you talking about partitioning phase of install process? root file system = /, it's an equivalent of C: in windows world.

[http://nguyenhai.files.wordpress.com/2008/12/gparted_1_big.jpg](http://nguyenhai.files.wordpress.com/2008/12/gparted_1_big.jpg)
you see that hda3 in example screenshot? it has / as a mountpoint

/ is the only partition that is required, though it's good to have separate /home (with user data) and in case of disaster and reinstall user configuration is left untouched.

---

### Post by MixelPixOrItDidntHappen on 2010-02-01
Hey Mangs! 

Thanks for your swift response. I've sorted that root means "/" but ah, when making the swap partition? that the install instructions demand, the whole ******* thing seems to have hung. Like, I can click on the really original 'start' bar in the background and it works but the ap in foreground however, the partioning phase of the install, has hung.

I fear from this point fwd we'll be spinning our wheels. I called a buddy at HP and told him that I was installing Ubuntu and he laughed at me before repremanding me and directing me to what he termed "a distribution that actually works".

Thanks again for you help though :)

---

