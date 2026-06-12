---
title: "viewing info pages"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by hunvilr on 2009-06-13
i use ubuntu 8.10. in terminal window when i type in command "info ls" it gives me the same page as "man ls". why is that? do i have to install separate package so that i can view info pages?

---

### Post by jonobr on 2009-06-13
AFAIK info was the NBT which never really caught on and in most cases just prints the same result as the man pages.

(im now expecting a lot of info supporters to blast me out of it:-) )
These man pages go back to earlier unix systems and as such are a bit entrenched, like vi vs vim....
I dont think many people use man pages either, they are (in some cases, not very intuitive or helpful and in most cases your better off going to the forums)


newer there is better but people still use the older.....

Also, just for a giggle

I man'd info

```
INFO(1)                          User Commands                         INFO(1)

NAME
       info - read Info documents

SYNOPSIS
       info [OPTION]... [MENU-ITEM...]

DESCRIPTION
       Read documentation in Info format.

OPTIONS
       --apropos=STRING
              look up STRING in all indices of all manuals.

       -d, --directory=DIR
              add DIR to INFOPATH.

       --dribble=FILENAME
              remember user keystrokes in FILENAME.

       -f, --file=FILENAME
              specify Info file to visit.
 Manual page info(1) line 1

```

And then infoed the man

```
File: *manpages*,  Node: man,  Up: (dir)

MAN(1)                        Manual pager utils                        MAN(1)

NAME
       man - an interface to the on-line reference manuals

SYNOPSIS
       man  [-c|-w|-tZ] [-H[browser]] [-T[device]] [-X[dpi]] [-adhu7V] [-i|-I]
       [-m system[,...]] [-L locale] [-p  string]  [-C  file]  [-M  path]  [-P
       pager]  [-r  prompt]  [-S  list] [-e extension] [--warnings [warnings]]
       [[section] page ...] ...
       man -l [-7] [-tZ] [-H[browser]] [-T[device]] [-X[dpi]] [-p string]  [-P
       pager] [-r prompt] [--warnings[warnings]] file ...
       man -k [apropos options] regexp ...
       man -f [whatis options] page ...

DESCRIPTION
       man  is  the  system's manual pager. Each page argument given to man is
       normally the name of a program, utility or function.  The  manual  page
       associated  with each of these arguments is then found and displayed. A
       section, if provided, will direct man to look only in that  section  of
-----Info: (*manpages*)man, 897 lines --Top-------------------------------------
Welcome to Info version 4.11. Type ? for help, m for menu item.

```

Then info'd info

```
File: *manpages*,  Node: info,  Up: (dir)

INFO(1)                          User Commands                         INFO(1)

NAME
       info - read Info documents

SYNOPSIS
       info [OPTION]... [MENU-ITEM...]

DESCRIPTION
       Read documentation in Info format.

OPTIONS
       --apropos=STRING
              look up STRING in all indices of all manuals.

       -d, --directory=DIR
              add DIR to INFOPATH.

       --dribble=FILENAME
              remember user keystrokes in FILENAME.
-----Info: (*manpages*)info, 134 lines --Top------------------------------------
Welcome to Info version 4.11. Type ? for help, m for menu item.

```

And of course, day 1 of your first unix / linux coaurse is not complete without 
man man


```
File: *manpages*,  Node: info,  Up: (dir)

INFO(1)                          User Commands                         INFO(1)

NAME
       info - read Info documents

SYNOPSIS
       info [OPTION]... [MENU-ITEM...]

DESCRIPTION
       Read documentation in Info format.

OPTIONS
       --apropos=STRING
              look up STRING in all indices of all manuals.

       -d, --directory=DIR
              add DIR to INFOPATH.

       --dribble=FILENAME
              remember user keystrokes in FILENAME.
-----Info: (*manpages*)info, 134 lines --Top------------------------------------
Welcome to Info version 4.11. Type ? for help, m for menu item.

```

---

### Post by hunvilr on 2009-06-13
what u said is all fine. but I dont' see a answer to my question anywhere.

---

### Post by niteshifter on 2009-06-13
> **hunvilr said:**
> i use ubuntu 8.10. in terminal window when i type in command "info ls" it gives me the same page as "man ls". why is that? do i have to install separate package so that i can view info pages?

No. Both man and info pages (if info is available) are installed from a proper package.

There is a difference (yep, here comes the blast ;) ). Programs like du, df, awk, sed, & co are called the coreutils in Gnu-speak. So let's find out more:
```
man coreutils
```

No biscuit :(

Now try this:
```
info coreutils
```
Joy! Useful stuff to read!

man pages tend to be terse. info pages, if **specifically generated for a program** tend be more verbose. However, as noted, the effort to produce an info page is usually not done, so essentially the man page text is 'copied'.

---

