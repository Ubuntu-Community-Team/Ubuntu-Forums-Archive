---
title: "Help with deleting some files."
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Max Williams on 2009-06-29
I have a big directory with a lot of nested files and folders.  I want to keep all of the folders, but delete all of the files EXCEPT 

files ending in 'thumbnail.jpg'
xml files.

I'm struggling to put the rm call together - i guess i would use a regex like this to describe the files i want to *keep*:

/.*thumbnail\.jpg$|.*\.xml$/

but i can't work out how to incorporate this into the call to rm (if indeed rm is the best tool for this)

thanks!
max

---

### Post by Wim Sturkenboom on 2009-06-29
use find and xargs

there is an example on [this page](http://www.ss64.com/bash/find.html) that involves the rm command

You can search that page (or your local manpage) for regex and xargs

---

### Post by Max Williams on 2009-06-29
> **Wim Sturkenboom said:**
> use find and xargs

there is an example on [this page](http://www.ss64.com/bash/find.html) that involves the rm command

You can search that page (or your local manpage) for regex and xargs

Thanks Wim

I'm getting closer - this finds all the files i want to keep:

find -regextype posix-egrep -iregex '.*\.xml|.*thumbnail.jpg'

then i guess i can just say 

 | xargs rm

but, i can't work out how to say 'everything that *doesn't* match this'.  it really bugs me how both NOT and 'START OF STRING' both use the ^ symbol in regular expressions.  I tried the following to no avail:

'^(.*\.xml|.*thumbnail.jpg)'  
  => gets the files i want to keep

'.*\.^xml|.*^thumbnail.jpg'
  => gets no files

'.*(^\.xml)|.*(^thumbnail.jpg)'
  => gets no files

---

### Post by geirha on 2009-06-29
```
find -type f -not -name "*.xml" -not -name "*.thumbnail.jpg"
```
If that prints the list of files you want to delete, just add a -delete at the end of that command to have it delete them.

The proper way to use xargs (though not needed in this particular case), would be
```
find -type f -not -name "*.xml" -not -name "*.thumbnail.jpg" -print0 | xargs -0 -- rm
```

-print0 will print the files with zeroes (\0) between them, instead of newlines (\n). The -0 argument to xargs tells it to expect the input to be zero delimited. \0 and / are the only two characters that can not appear in a filename, so this protects against filenames with whitespace.

---

### Post by Max Williams on 2009-06-30
> **geirha said:**
> ```
find -type f -not -name "*.xml" -not -name "*.thumbnail.jpg"
```
If that prints the list of files you want to delete, just add a -delete at the end of that command to have it delete them.


That's perfect, thanks a lot gheirha!  I should have read the man page for find, it's in there, many pages down :)

cheers
max

---

