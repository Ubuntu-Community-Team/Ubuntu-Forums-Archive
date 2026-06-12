---
title: "Downgrading (Kile)"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by LillaEpsilon on 2009-04-29
I want to downgrade Kile 2.1 to an older version as the new one is slow and unstable. I tried 

sudo apt-get downgrade Kile

but received back

Invalid operation downgrade

Of course, I tried the synaptic package manager but there are no old versions available there either.

Ideas anyone?

---

### Post by sandr on 2009-04-30
I wasn't happy with the new Kile version either, it was very slow except on small files, and my shortcuts were gone.
What worked for me was the manually downloading the previous (intrepid) package from
[http://packages.ubuntu.com/intrepid/i386/kile/download](http://packages.ubuntu.com/intrepid/i386/kile/download)
and installing it with the GDebi program that starts up when you click on the file. Then, in synaptic, I checked the option 'lock version' on the newly installed package to stop the update manager from suggesting updates.
This gave me back the faster (non-KDE4) Kile 2.0.1, but unfortunately not my shortcuts.

Something else that you might try is running Kile with the option
--graphicssystem raster
as is suggested in
[https://bugs.launchpad.net/ubuntu/+source/kile/+bug/361843](https://bugs.launchpad.net/ubuntu/+source/kile/+bug/361843)

However, they warn that this option is not considered stable yet.

---

### Post by LillaEpsilon on 2009-05-05
> **sandr said:**
> I wasn't happy with the new Kile version either, it was very slow except on small files, and my shortcuts were gone.
What worked for me was the manually downloading the previous (intrepid) package from
[http://packages.ubuntu.com/intrepid/i386/kile/download](http://packages.ubuntu.com/intrepid/i386/kile/download)
and installing it with the GDebi program that starts up when you click on the file. Then, in synaptic, I checked the option 'lock version' on the newly installed package to stop the update manager from suggesting updates.


Thank you Sandr! At a first glance, this seems to work :D

---

### Post by evencoil on 2009-05-18
i wanted to do the same thing and this worked seamlessly, thanks for posting this!

---

