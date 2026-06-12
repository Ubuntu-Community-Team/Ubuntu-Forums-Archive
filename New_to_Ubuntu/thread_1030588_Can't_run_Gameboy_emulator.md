---
title: "Can't run Gameboy emulator?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by slapperig on 2009-01-04
I've been using ubuntu (intrepid) for all of a month now, and I've just now gotten around to looking for solid emus. I read up and heard that gnuboy was a good one, and installed gnuboy-x from the terminal (including the SDL and SVGA libs) and confirmed that it was installed in SPM.

Now I can't run the stinkin' thing. I had to search my file system just to find where it had been installed, but the executable file does nothing when I try to run it.

Any help?

---

### Post by stoogiebuncho on 2009-01-04
This is a shot in the dark, but have you tried pressing Alt+F2 and typing 
```
gnuboy
```

You could also try
```
gnuboy-x
```

If either of those work, you can add a launcher to your Applications menu with the proper command.  If you need help doing that let us know.

---

### Post by slapperig on 2009-01-04
> **stoogiebuncho said:**
> This is a shot in the dark, but have you tried pressing Alt+F2 and typing 
```
gnuboy
```

You could also try
```
gnuboy-x
```

If either of those work, you can add a launcher to your Applications menu with the proper command.  If you need help doing that let us know.

Neither worked. Both returned the error that there was no such file or directory.

---

### Post by stoogiebuncho on 2009-01-04
Looks like you have to specify the rom you want it to load as well.  As in:

```
gnuboy my_game.gb
```

There's info here:

[http://web.archive.org/web/20041119012233/http://gnuboy.unix-fu.org/]("http://web.archive.org/web/20041119012233/http://gnuboy.unix-fu.org/")

---

### Post by slapperig on 2009-01-04
> **stoogiebuncho said:**
> Looks like you have to specify the rom you want it to load as well.  As in:

```
gnuboy my_game.gb
```

There's info here:

[http://web.archive.org/web/20041119012233/http://gnuboy.unix-fu.org/]("http://web.archive.org/web/20041119012233/http://gnuboy.unix-fu.org/")

Still nothing, and it's getting kind of infuriating.
I've moved the gnuboy folder into my /home/<me> dir, as per "No such directory in /home/..." and alt-F2 ```
gnuboy-x game.gb
```, and it returns the same error message, though I know that the gnuboy folder, executable file, and game is there.:confused:

---

### Post by evilkastel on 2009-01-04
Well... gnuboy never worked for me. for GBA emu i use vbaexpress, frontend to visual boy advance. And works like a charm. 

```
sudo apt get install vbaexpress
```

I'll suggest you try it too, is really easy to set up and use.

---

### Post by slapperig on 2009-01-04
> **evilkastel said:**
> Well... gnuboy never worked for me. for GBA emu i use vbaexpress, frontend to visual boy advance. And works like a charm. 

```
sudo apt get install vbaexpress
```

I'll suggest you try it too, is really easy to set up and use.

Thanks, worked like a charm

---

### Post by evilkastel on 2009-01-05
there is no need to post a ty note. there is a medallion at right bottom corner that does that. Anyway, glad it worked. :)

---

### Post by okamishadow on 2009-03-15
I try installing that but the interface and the implementation are garbage compared with the RbVBA... Not meet my spectations...

---

