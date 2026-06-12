---
title: "does having more than one video driver installed slow computer down?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by libihero on 2010-05-27
i added the repository for the xorg development drivers, and i realized that i also have video drivers which are targeted for other cards other than my own downloaded.  does having them installed interfere with the video driver that targets my chip?

---

### Post by c00lwaterz on 2010-05-27
for me, I will remove the one that is not useful for me. choose the better driver for your video card that is running smoothly for ubuntu. Just for me.

---

### Post by Ozymandias_117 on 2010-05-27
> **libihero said:**
> i added the repository for the xorg development drivers, and i realized that i also have video drivers which are targeted for other cards other than my own downloaded.  does having them installed interfere with the video driver that targets my chip?

I can't think of any ways that it would. You can't load multiple kernel modules (drivers) for a device at a time, which means the other ones you downloaded are only wasting some of your hard drive space.

---

### Post by steveneddy on 2010-05-27
You can delete them if you like. They offer no performance gains nor do they take away any performance from the machine.

The reason this is done is so that when one first installs Ubuntu the probability of the correct video driver already being installed makes the install process much easier.

---

