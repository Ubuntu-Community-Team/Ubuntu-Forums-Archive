---
title: "ls * [b]"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Drenriza on 2010-01-08
i know what ls * does, but if you put a [b] or something else into the command what does it then do?.

thanks on advance

---

### Post by audiomick on 2010-01-08
Hallo.
In
```
man bash
```
I found this:
       > The special pattern characters have the following meanings:

       *****      Matches  any  string, including the null string.  When the glob&#8208;star shell option is enabled, and * is used in a filename expansion  context,  two  adjacent  *s  used as a single pattern will match all files and zero or more directories and subdirectories. If  followed by a /, two adjacent *s will match only directories and subdirectories.
       **?**      Matches any single character.
       **[...]**  Matches any one of the enclosed characters.  A pair  of  characters separated by a hyphen denotes a range expression; any chaacter that sorts between those two characters, inclusive,  using the  current  locale's  collating sequence and character set, is matched.  If the first character following the [ is a !  or a  ^ then  any  character not enclosed is matched.  The sorting order of characters in range expressions is determined by the  current locale  and  the value of the LC_COLLATE shell variable, if set. A - may be matched by including it as the first or last  character in the set. A ] may be matched by including it as the first character in the set.

so it looks like it will do "ls" on anything with "b" in the name.

---

