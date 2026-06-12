---
title: "mp32ogg is deleting my file and giving nothing back"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by anthony62490 on 2009-06-19
Trying to convert a sound effect to ogg format. I've already downloaded mp32ogg. In the terminal, I typed,

```
anthony@anthony-desktop:~$ mp32ogg --quality=10 --delete /home/anthony/Documents/Misc/login.mp3
```

and it spits out,

```
mp32ogg v0.11
(c) 2000-2002 Nathan Walp
Released without warranty under the terms of the Artistic License

Converting /home/anthony/Documents/Misc/login.mp3 to OGG...
login.ogg done!
```

It sounds good, but it just deletes my file. Good thing I had a copy. I must be missing something. Why does it tell me that the conversion was a success, but then give me nothing?

---

### Post by dnairb on 2009-06-19
I assume you mean that it deletes the original .mp3 file (as it should as you used the --delete switch) but the .ogg file is not where you think it should be.

IIRC you need to operate from within the directory where the .mp3 file is. So try this:

```
cd /home/anthony/Documents/Misc
mp32ogg --quality=10 --delete login.mp3
```

---

### Post by anthony62490 on 2009-06-19
Oh. I thought it was asking for a filepath. It was asking for a save destination? That makes sense. Thank you very much. You wouldn't happen to know what happened to the dud conversions, would you? I might have to delete quite a few files.

---

### Post by dnairb on 2009-06-19
> **anthony62490 said:**
> Oh. I thought it was asking for a filepath. It was asking for a save destination?

Not quite (I think). I believe that you have to operate mp32ogg from the directory that the original .mp3 file is in. The .ogg file will be saved in the same direcory.

> **anthony62490 said:**
> You wouldn't happen to know what happened to the dud conversions, would you? I might have to delete quite a few files.

It *might* be in the root directory of your filesystem.

---

### Post by anthony62490 on 2009-06-19
Thank you very much. Your help is invaluable.

---

