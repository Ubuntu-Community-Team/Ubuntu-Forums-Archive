---
title: "Terminal Transparency Issues"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by SoulMazer on 2009-07-16
This isn't a huge problem, but I just like to have my OS look as clean and perfect as possible.

So, I have 9.04 installed on my desktop computer, and I just recently installed 9.04 on my laptop. I have been transferring all my theme stuff/files over, but I encountered a problem. On my desktop computer, I got my terminal to look like so:

["Good Terminal"]("http://i189.photobucket.com/albums/z266/Capn_Soul/Terminal2.png")

Yet, when I configured my theme on my laptop, I was only able to make my terminal look like this:

["Bad Terminal"]("http://i189.photobucket.com/albums/z266/Capn_Soul/Terminal1.png")

I have them both set to use the same colors, options, and transparency settings, so what could I do to make my "bad terminal" look like my "good terminal"?

Thanks in advance.

---

### Post by CatKiller on 2009-07-16
> **SoulMazer said:**
> what could I do to make my "bad terminal" look like my "good terminal"?

Use a compositing window manager like Compiz on your laptop. It's the only way you'll get true transparency like you have on your desktop.

---

### Post by mcduck on 2009-07-16
Catkiler is right, you need to have desktop effects enabled or some other compositing manager running to get real transparency.

---

### Post by benj1 on 2009-07-16
> **CatKiller said:**
> Use a compositing window manager like Compiz on your laptop. It's the only way you'll get true transparency like you have on your desktop.

+1

go to system-->preferences-->appearance-->visual effects and set it to normal or extra (compiz)

---

### Post by jmszr on 2009-07-16
SoulMazer,

This is a good resource: [https://help.ubuntu.com/community/TransparentTerminals](https://help.ubuntu.com/community/TransparentTerminals)

---

### Post by SoulMazer on 2009-07-16
Thanks for all the ideas guys, except I ran into a little problem. When I tried to change my "Visual Effects" from None to Normal, I receive an error that says "Desktop effects could not be enabled".

So, I took the next step and assumed it was a graphics driver problem. I have an ATI Radeon 3200 graphics card, or what might help more, "01:05.0 VGA compatible controller [0300]: ATI Technologies INC RS780M/RS780MN ]Radeon HD 3200 Graphics] [1002:9612]".

When I look in "System -> Administration -> Hardware Drivers", I see an un-activated "ATI/AMD proprietary FGLRX graphics driver".

Shall I activate this driver? And if so, will it have a large system resources impact? Or what should I do?

Thanks again.

---

### Post by mcduck on 2009-07-16
> **SoulMazer said:**
> Thanks for all the ideas guys, except I ran into a little problem. When I tried to change my "Visual Effects" from None to Normal, I receive an error that says "Desktop effects could not be enabled".

So, I took the next step and assumed it was a graphics driver problem. I have an ATI Radeon 3200 graphics card, or what might help more, "01:05.0 VGA compatible controller [0300]: ATI Technologies INC RS780M/RS780MN ]Radeon HD 3200 Graphics] [1002:9612]".

When I look in "System -> Administration -> Hardware Drivers", I see an un-activated "ATI/AMD proprietary FGLRX graphics driver".

Shall I activate this driver? And if so, will it have a large system resources impact? Or what should I do?

Thanks again.

Yes, for that graphics card you should enable Ati's own driver (fglrx). It will give you better graphics performance than what the default open-source driver does.

Enable that, and after a reboot you should be able to enable desktop effects.

---

### Post by SoulMazer on 2009-07-17
Ok, that did it. Thanks everybody for the input.

---

