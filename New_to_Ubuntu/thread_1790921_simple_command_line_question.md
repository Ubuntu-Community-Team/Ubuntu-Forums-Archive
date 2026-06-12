---
title: "simple command line question"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by querent on 2011-06-25
Howdy,

So I've got this command that lets me recursively clean out everything that's not a given file type:

find /target/directory ! -iname '*.mp3' -type f -exec echo /bin/rm -f '{}' \;

I run this on, say, a musician's discography to clean out all the .jpeg's and such.  I run it once with "echo" in place to check, and then without the "echo" to actually do the cleaning.

My question is, how do I include an "or" statement in this to allow, for instance, both mp3's and wma's to survive the cleansing?

Advanced thanks,
querent

---

### Post by Ozymandias_117 on 2011-06-25
Another way to do the same thing would be:
```
find /directory ! -iname "*.mp3" -type f -delete
```

To run it as a "test" without deleting, simply do:
```
find /directory ! -iname "*.mp3" -type f
```

For multiple filetypes, mess with the regular expression:
```
find /directory ! -iname "*.(mp3|avi)" -type f -delete
```

Sorry. After you posted that I looked at the man page more. I thought name had full regex capabilities, but it doesn't, and -iregex doesn't look like it's quite what you want either.

---

### Post by diesch on 2011-06-25
```
find /target/directory   -not \( -iname \*.mp3  -or -iname \*.wma \) -type f -exec echo /bin/rm -f '{}' \;
```

---

### Post by querent on 2011-06-25
diesch's solution works.  The regex thing isn't working...don't know why.  I'll play with it.

Thanks all!

---

### Post by inameiname on 2011-06-25
> **diesch said:**
> ```
find /target/directory   -not \( -iname \*.mp3  -or -iname \*.wma \) -type f -exec echo /bin/rm -f '{}' \;
```


Cool command. Thanks for sharing.

Also, is it possible to add more two file extensions to exclude from removal, simply by adding more than one "-or"?

---

### Post by diesch on 2011-06-26
You can add as many as you want or build more complex expressions (there's [FONT=Courier New]-and[/FONT], too)

---

### Post by inameiname on 2011-06-27
> **diesch said:**
> You can add as many as you want or build more complex expressions (there's [FONT=Courier New]-and[/FONT], too)

Okay, cool. Thanks for the info.

---

