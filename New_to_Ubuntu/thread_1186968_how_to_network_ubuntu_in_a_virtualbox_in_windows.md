---
title: "how to network ubuntu in a virtualbox in windows"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by powel212 on 2009-06-14
I had a problem getting Ubuntu to see my network computers running in a virtualbox on windows 7.

I changed the default network adapter settings in the virtualbox settings and then was able to network correctly.

I just wanted to post what I did to fix it in case someone else has the same difficulty in the future.

The virtualbox default settings for network controller were set to "NAT"

With this setting I could not see my network shares.

After changing the network controller to "Bridged" it worked perfectly.

Powel

---

