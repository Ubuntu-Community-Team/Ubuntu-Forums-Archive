---
title: "need to find a file"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by robotz421 on 2011-03-15
I am trying to find a file.  I don't know which directory it is in but I know the filename.  How would I get ls to do a recursive search starting at the root directory?  Also, does anyone know of a good pdf book about using the command line that would answer these kinds of questions?

---

### Post by TheQuasar on 2011-03-15
You could go to "Places", look at the option "Search For Files". I think thats how. 

And how do you post a question on this forum because I just joined and I can't seem to post a question. Thank you.

---

### Post by Vaphell on 2011-03-15
2 commands can find it - locate and find

```
locate name
```
uses database so it's fast but database may need refreshing by **sudo updatedb** first

find is the most powerful searching command, recursive by default and a must-have-in-your-toolbox as long as command line is concerned
```
find ~ -type f -iname 'name_pattern'
```
this example looks in home for a file matching name_pattern
**find --help** for more info about options - there are tons of them (and google is your friend too)

---

### Post by robotz421 on 2011-03-15
Go to the forum you want and click on the "New Thread" button.  Thanks for trying to help but nautilus does not seem to want to tell me what directory the file is in.  It gives me a nice icon and lets me open the file if I want but no location (okay forget that I just found out how to dredge up the directory.)  However, I would like to know how to do things like this from the command line.

---

### Post by robotz421 on 2011-03-15
Thanks very much Vaphell, that is just what I needed to know.  Is there a way to make non-recursive commands recursive, like passing them to some kind of recurse command?  Also, any book recommendations?

---

### Post by sisco311 on 2011-03-15
> **Vaphell said:**
> 
```
find ~ -iname 'name_pattern' -type f
```


fixed :)

The -iname test should come before the -type test in order to avoid having to call stat(2) on every file.

---

### Post by rotave on 2011-03-16
> **robotz421 said:**
> Also, any book recommendations?
 
Try "The Linux Command Line", you can download it from here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by Vaphell on 2011-03-16
> **sisco311 said:**
> fixed :)

The -iname test should come before the -type test in order to avoid having to call stat(2) on every file.

good to know :) i wouldn't mind find optimizing search query though. If it's well known that some things should go before others then the program should do it on its own at least in trivial cases.

---

### Post by viditgoyal3009 on 2011-03-16
if u want to learn linux and its terminal commands nicely then i would recommend reading "Linux Bible" which can be downloaded using torrents...

---

