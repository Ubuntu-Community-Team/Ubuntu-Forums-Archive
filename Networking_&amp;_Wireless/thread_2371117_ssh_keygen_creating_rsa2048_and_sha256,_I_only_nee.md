---
title: "ssh keygen creating rsa2048 and sha256, I only need rsa2048"
date: 2017-09-11
forum: Networking &amp; Wireless
---

### Post by Barry_Keegan on 2017-09-11
I'm trying to use public private keys to connect to networking equipment from my ubuntu device. I've gone through many tutorials where you generate the rsa key by running the following command **ssh-keygen -b 2048 -t rsa **and then you get this random art image.

The key's randomart image is:
```
+---[RSA 2048]----+
|    o++=*o       |
|   .oo*B. o      |
|   . *+*ooo      |
|o   o O+=o = .   |
|oo   = *S   = +  |
|oE  + .      o . |
|oo..             |
|  o .            |
|   .             |
+----[SHA256]-----+
```

I've noticed in all tutorials there is no SHA256 at the bottom of their image, only rsa2048 at the top. Also when I try and add my ssh key to the networking equipment it gives an error saying no rsa is supported. Is it possible to generate a key without the sha256? I could be reading this all wrong but I think I'm in the right ball park.

Thanks

---

### Post by QIII on 2017-09-11
Hello!

You have this marked as [Solved].

If it is, would you please share the solution for the benefit of the community and not leave everyone hanging?

If not, please remove the [Solved] tag.

Cheers!

---

