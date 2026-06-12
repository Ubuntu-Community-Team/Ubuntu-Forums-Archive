---
title: "failed to load hibernation, any garbage left?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by mousecat on 2009-07-17
For some personal reason, I missed a load from hibernation several times. Is it gonna leave some garbage in the system? I checked some archives saying that the hibernation image will be located on swap. Does it mean it should not leave garbage in the main system?

Thanks for any input.

---

### Post by niteshifter on 2009-07-17
Hi,

It depends upon what you mean by "garbage".

If garbage means something along the lines of junk files left sprinkled in about under the root of the file system ( / ) taking up space, interfering with system operation in some way - then no.

On the other hand, if garbage means recognizable data left on the drive that could possibly be recovered - then yes.
Recovery of the data is not easy, it's not like you can just point testdisk/photorec at it, hit enter a few times and you're done. One goes at it more along the lines of examining a core dump.

---

### Post by mousecat on 2009-07-17
I am pretty sure I meant the first situation.
Altho I might have to dig into the second sometime in the future. but I am quite happy with the answer for now.

thanks niteshifter.

---

