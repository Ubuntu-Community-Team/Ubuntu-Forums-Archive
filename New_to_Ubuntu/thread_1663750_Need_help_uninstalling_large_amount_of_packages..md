---
title: "Need help uninstalling large amount of packages."
date: 2011-01-10
forum: New to Ubuntu
---

### Post by MollyWop on 2011-01-10
I followed this guide:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
and installed alot of packages I don't think I want any more. I tried out that multimedia thing with Ardour, and I don't like how everything is all separate (Reason is all-in-one, which is what I prefer). Also, I couldn't get JACK to work on my desktop (much like how ASIO4ALL doesnt work on my computer either??) :/

Anyways since I've had problems, I just want all this stuff off my computer. I like everything to run smoothly and cleanly so I'm wondering if I missed a few things, would it slow it down? or just take up space since its being unused? Thanks..

---

### Post by Synthetic Sam on 2011-01-10
if you installed with this:
```
sudo apt-get install ardour audacious hydrogen jackd jack-rack qjackctl seq24 vkeybd zynaddsubfx patchage vlc kino pitivi acidrip ubuntu-restricted-extras ubuntustudio-menu gcdmaster
```

then you can remove all the listed packages with:
```
sudo apt-get remove --purge ardour audacious hydrogen jackd jack-rack qjackctl seq24 vkeybd zynaddsubfx patchage vlc kino pitivi acidrip ubuntu-restricted-extras ubuntustudio-menu gcdmaster
```

(add and remove the packages that you wish to remove from the command as appropriate)

I tend to find with Linux that nothing ever really takes a lot of space, so I wouldn't worry about missing anything.

If you want to remove packages that were automatically installed by installing the other software, and are no longer needed, then run:

```
sudo apt-get autoremove
```

---

### Post by MollyWop on 2011-01-10
> **Synthetic Sam said:**
> if you installed with this:
```
sudo apt-get install ardour audacious hydrogen jackd jack-rack qjackctl seq24 vkeybd zynaddsubfx patchage vlc kino pitivi acidrip ubuntu-restricted-extras ubuntustudio-menu gcdmaster
```then you can remove all the listed packages with:
```
sudo apt-get remove --purge ardour audacious hydrogen jackd jack-rack qjackctl seq24 vkeybd zynaddsubfx patchage vlc kino pitivi acidrip ubuntu-restricted-extras ubuntustudio-menu gcdmaster
```(add and remove the packages that you wish to remove from the command as appropriate)

I tend to find with Linux that nothing ever really takes a lot of space, so I wouldn't worry about missing anything.

If you want to remove packages that were automatically installed by installing the other software, and are no longer needed, then run:

```
sudo apt-get autoremove
```
Thank you!
what is the purge --function?
and wouldn't auto remove be the same as 'computer janitor?'

---

### Post by Synthetic Sam on 2011-01-10
Purge will delete all of the associated configuration files, it's not necessary as these will be using kB of space, and may come in handy if you want to reinstall the software at a later point in time.

I've not used computer janitor, but from a quick google search, it looks like it performs the same task.

---

