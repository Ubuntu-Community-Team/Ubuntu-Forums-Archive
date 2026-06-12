---
title: "Ubuntu 16.10 kernel update broke network and mouse"
date: 2017-03-18
forum: Networking &amp; Wireless
---

### Post by andrehpereira on 2017-03-18
Hello,

Just writing to report that the last update also broke my wifi and my wireless mouse.

My laptop is a Dell Inspiron 15-7559 and the mouse is a Logitech M335

Edit:

Everything works fine if I boot with 4.8.0-41.

And now I also noticed the fn keys were misconfigured (fn+ prt scrn should enable/disable wifi, but pressing the button in 4.8.0-42 disabled the trackpad).

---

### Post by jeremy31 on 2017-03-18
Moved to it's own thread
Post the results for ```
dpkg -l | grep linux-image
```

---

### Post by Doug S on 2017-03-18
It seems as though kernel 4.8.0-42 may have been retracted. It isn't available for me. See also [here]("http://askubuntu.com/questions/893632/ubuntu-16-04-kernel-packages-have-been-kept-back"). And there are multiple reports of issues from people that did get it.

---

### Post by andrehpereira on 2017-03-18
> **jeremy31 said:**
> Moved to it's own thread
Post the results for ```
dpkg -l | grep linux-image
```

Running the requested command yielded the following:

```

rc  linux-image-4.8.0-22-generic                4.8.0-22.24                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-30-generic                4.8.0-30.32                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-34-generic                4.8.0-34.36                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-37-generic                4.8.0-37.39                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-39-generic                4.8.0-39.42                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-40-generic                4.8.0-40.43                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-41-generic                4.8.0-41.44                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-42-generic                4.8.0-42.45                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-22-generic          4.8.0-22.24                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-30-generic          4.8.0-30.32                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-34-generic          4.8.0-34.36                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-37-generic          4.8.0-37.39                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-39-generic          4.8.0-39.42                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-40-generic          4.8.0-40.43                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-41-generic          4.8.0-41.44                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-virtual                   4.8.0.41.52                                   amd64        Extra drivers for Virtual Linux kernel image
ii  linux-image-generic                         4.8.0.41.52                                   amd64        Generic Linux kernel image

```

This is the result running with version 4.8.0-41.

But I guess I will purge 4.8.0-42 as suggested by Doug.

Thanks for the help!

---

