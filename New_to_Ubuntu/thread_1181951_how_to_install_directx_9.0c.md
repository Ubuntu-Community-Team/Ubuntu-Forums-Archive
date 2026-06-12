---
title: "how to install directx 9.0c"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by bobin on 2009-06-08
help me

---

### Post by CatKiller on 2009-06-08
Why would you want to? DirectX is a Windows technology and has no place in your Linux install. Whatever the reason is that you think you need to install DirectX, you don't.

---

### Post by bobin on 2009-06-08
to play windows based games on wine.

---

### Post by Mortus Pryde on 2009-06-08
And for a friendlier response...

You will only need Direct X for applications run under Wine. If this is the case if you right click there should be an option to install it using Wine. Direct X as mentioned before is Windows only and so like any other Windows programs you may be trying to run would need to be installed and run with Wine.

---

### Post by CatKiller on 2009-06-08
> **bobin said:**
> to play windows based games on wine.

You don't need to install DirectX in Wine. It has its own DirectX implementation, and installing DirectX under Wine will both not work, and likely break Wine's own internal DirectX implementation.

Honestly, don't try.

There are a handful of Windows-specific .dll files that can be useful under certain circumstances (like dinput.dll) but if find that you need them, you'll also generally be given instructions on how to use them. Installing the whole of DirectX will just break things.

---

### Post by NightwishFan on 2009-06-08
I believe Wine already has DirectX 9 support. You will never need to install directx, and if you application complains and will not work, installing DirectX will likely not solve anything.

If you need some help on Wine, I have a thread here. I will add the DirectX issue to the main post.

[http://ubuntuforums.org/showthread.php?p=7410323](http://ubuntuforums.org/showthread.php?p=7410323)

---

