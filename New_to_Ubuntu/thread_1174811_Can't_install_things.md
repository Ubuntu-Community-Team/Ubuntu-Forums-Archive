---
title: "Can't install things"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by cedar.bristol on 2009-05-31
I tried to install Emacs by downloading it, building it, and running it, which worked with puppy linux, but then I get this "can't open termcap database file" when I try to run emacs.  

Then I find out that you're really supposed to use the package manager to install things and shouldn't install by downloading source and building, so I try doing that to get the emacs package, and still get the same error.  

Should I always use the package manager to install things?

How can I get emacs to work?

When I go to add/remove and search on emacs, I see it checked, but don't see it in any of my menus.  Is it supposed to be that way?

---

### Post by jbrown96 on 2009-05-31
Emacs is usually run from a terminal. I know that there are graphical versions, but I doubt that is what you installed. Open a terminal (Apps-->Accessories-->Terminal) and then try ```
emacs
```

---

### Post by cedar.bristol on 2009-05-31
I was trying to run emacs from the terminal when I got the error:

emacs: cannot open termcap database file

That's when I tried to install it via the visual package manager, hoping that would do something different, but it didn't.  

I wonder if I created a link when I did the first attempted install and if that is what I'm hitting when I type 'emacs' at the terminal?

The first time I tried typing 'emacs' it told me to run something like sudo get-install emacs or something like that.  I ignored that to do it the way I had done it under puppy linux.

---

### Post by sandyd on 2009-05-31
go to the source direcoty and
```

sudo make uninstall

```

i hope you haven't deleted it yet. it could make things difficult

---

