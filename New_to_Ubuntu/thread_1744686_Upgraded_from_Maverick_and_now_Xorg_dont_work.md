---
title: "Upgraded from Maverick and now Xorg dont work"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Adeons on 2011-04-30
Hello

I upgraded from Maverick to Natty and when the system loads, it only shows the login for tty2.

In the Xorg log is written something like "cant load nvidia module"; then i removed the driver by uninstalling the package nvidia-current, but the same error is still there :confused:. Also reinstalling it is the same.

The previous kernel loaded fine once, and from now when loads gets frozen by a kernel oops.

May i use nouveau, or reinstall the nvidia driver? or how to install these from console correctly?

Thanks

---

### Post by sikander3786 on 2011-04-30
Which graphics card is there? Model? And is there an xorg.conf file? Run this command and see if it exists. We might need to remove it.

```
cat /etc/X11/xorg.conf
```

Running this command will tell you if your PC is able to run Unity or not. Please post the output if possible.

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Adeons on 2011-04-30
Hello

Here I use a Nvidia GeForce 6200, and I use Kubuntu, so idont have Unity.

Thanks for the reply

---

### Post by sikander3786 on 2011-04-30
> **Adeons said:**
> Hello

Here I use a Nvidia GeForce 6200, and I use Kubuntu, so idont have Unity.

Thanks for the reply
Sorry I missed your [Kubuntu] part. Most issues nowadays are coming with Unity so I guessed you were using Unity. You might wait for some other member to jump in.

---

