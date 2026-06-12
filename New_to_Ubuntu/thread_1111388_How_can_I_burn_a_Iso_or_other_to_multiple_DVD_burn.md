---
title: "How can I burn a Iso or other to multiple DVD burners?"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by arce on 2009-03-30
How can I burn a Iso or other to multiple DVD burners?

I don't see this option in Brasero.

I have more then 1 burner and sometimes like to burn the same Project/ISO/CD/DVD to all of the drives. What project would let me do this? I also need to burn at specific speeds. I need many choices at what speeds I burn.

---

### Post by supersonicdarky on 2009-03-30
Perhaps you can try just opening 2 instances of bracero and let each have its own drive?

---

### Post by kanikilu on 2009-03-30
If you don't mind installing all the KDE-related stuff that comes along with it, **K3b** is about the best CD/DVD burning program around...

---

### Post by arce on 2009-03-30
Ok K3B works great. But it doesn't support multiple drivers.

Supersonic.

I used to use Nero and it would be no problem. I think it is more of a hassle to open individual instances of K3b or Brasero to burn across multiple DVD's.

Any suggestions?

---

### Post by MockY on 2009-03-31
If Nero worked for you, why not continue to use it?
[http://www.nero.com/enu/linux3.html](http://www.nero.com/enu/linux3.html)

---

### Post by arce on 2009-03-31
You made my day!

Thanks

---

### Post by arce on 2009-03-31
Well its great to see the familiar Nero,,, But not support to burn to multiple drives. Any ideas?

---

### Post by 3rdalbum on 2009-04-01
There used to be a program in the repositories that could burn to multiple discs simultaneously, but it's not there anymore.

On the odd occasion that I need some simultaneous burning, I just open three instances of whatever program I'm using.

If you do a lot of burning you could write a simple script like this:

```

#!/bin/sh
growisofs -dvd-compat -Z /dev/scd0=image.iso &
sleep 2
growisofs -dvd-compat -Z /dev/scd1=image.iso &
sleep 2
growisofs -dvd-compat -Z /dev/scd2=image.iso

```

Replace "image.iso" with the path of your disc image, and /dev/scd0 with the device file name of your first DVD burner, and the other device file names accordingly.

The reason why there doesn't seem to be a program to wrap this up in a GUI is because I started, but never finished, writing the program :-)

---

### Post by arce on 2009-04-01
Please finish it:) I can't believe the Nero Linux doesn't have it.

---

