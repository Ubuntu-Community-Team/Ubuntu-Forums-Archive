---
title: "Removing characters from file names"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by dagoss on 2011-03-06
I have a set of files where every file is like this
```

0135 - file name.pdf
0136 - file name.pdf
0137 - file name.pdf

```

I want to remove the numbers at the beginning of each file, replace all spaces with '-' and make all characters lower case.  I've managed to accomplish the later 2 by doing this:

```

for f in *
do
     file=$(echo $f | tr A-Z a-z | tr ' ' '-')
     [ ! -f $file ] && mv "$f" $file
done

```

Now I still want to remove the first 7 characters of the file name.  I tried this:

```

for f in *
     do 
     file=$(echo $f | sed 's/.......\(.*\)/\1/')
     [ ! -f $file ] && mv "$f" $file
done

```

It removes only the characters from the 1st file. What, probably simple, thing am I missing?

---

### Post by col48 on 2011-03-06
I'm not familiar with the language, but since no-one else has offered a suggestion....

I wonder how it knows what the next file is each time it goes found the loop?  Could it be that having done it once it has a [revised first] file name which is 'after' the last one in the [unrevised] list?

The loop mechanism must have some means of knowing whether it has processed a file already and it could either do this by making a list at the start of the loop of all the files it will need to process (could be a list of millions) or having some kind of bookmark whereby all the ones it has done are before the mark and all the ones it has still to do are after - but it mustn't reprocess one it has done already.  Hats off to the interpreter/compiler writer if they have an elegant solution to what must be a standard problem.

---

### Post by asp314 on 2011-03-06
As much as I love to see people using the shell to solve their problems, sometimes a reliable GUI is just as useful.  Thunar, the XFCE file manager, comes with a very useful Bulk Rename Tool that I use for such purposes.  Just my 2 cents.

---

### Post by col48 on 2011-03-06
Here's my 2p worth!  (my earlier post was worth about 5p)

I'd make a file with the old file names in using (say) dir > filelist
then edit this list with a GUI file editor to turn each entry into a rename, then execute the result in the shell.

Only really appropriate as a one-off.

It's one thing I like about Linux.  There's usually several ways of doing things and each person can have their favourite, depending on what they know.

---

### Post by gmargo on 2011-03-06
A single **rename(1)** command will do it all:
```

rename 'tr/A-Z/a-z/; s/ /-/g; s/^\d+\-+//' *

``````

$ ls -1
0135 - file one.pdf
0136 - FILE two.pdf
0137 - file THR.pdf
$ rename 'tr/A-Z/a-z/; s/ /-/g; s/^\d+\-+//' *
$ ls -1
file-one.pdf
file-thr.pdf
file-two.pdf

```

---

### Post by col48 on 2011-03-06
gmargo

But that doesn't remove the first seven characters from what's left of the files names, as in the original post.

---

### Post by gmargo on 2011-03-06
> **dagoss said:**
> 
```

0135 - file name.pdf
0136 - file name.pdf
0137 - file name.pdf

for f in *
     do 
     file=$(echo $f | sed 's/.......\(.*\)/\1/')
     [ ! -f $file ] && mv "$f" $file
done

```It removes only the characters from the 1st file. What, probably simple, thing am I missing?
If the files all have the same base ("file name") in it, your second statement ("[ ! -f $file ]") prevents the overwrite.  That's why it seems that only the first one works.

---

### Post by gmargo on 2011-03-06
> **col48 said:**
> gmargo

But that doesn't remove the first seven characters from what's left of the files names, as in the original post.

Well, I did it based on the filename after the first two steps:
```

$ rename 'tr/A-Z/a-z/; s/ /-/g;' *
$ ls -1
0135---file-one.pdf
0136---file-two.pdf
0137---file-thr.pdf

```There are 4 digits and three dashs (7 characters).  I removed a string of digits and dashes instead of just 7 characters.  It can be recoded to remove the first 7 characters like this.  It amounts to the same thing for this example, but would not work right if there were, say, only three digits:
```

rename 'tr/A-Z/a-z/; s/ /-/g; s/^.{7}//' *

```

---

### Post by rpm13 on 2011-03-06
> **asp314 said:**
> As much as I love to see people using the shell to solve their problems, sometimes a reliable GUI is just as useful.  Thunar, the XFCE file manager, comes with a very useful Bulk Rename Tool that I use for such purposes.  Just my 2 cents.

Or if you can use emacs use the directory editor [URL=
"http://www.gnu.org/software/emacs/manual/html_node/emacs/Dired.html"]dired[/URL]

Go to writeable dired: [wdired]("http://www.gnu.org/software/emacs/manual/html_node/emacs/Wdired.html#Wdired")

And then edit ur filenames like any other text!!

---

