---
title: "The tar trick"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by sulekha on 2009-06-04
Hi all,

this is what i saw in the book  "Running linux 4 th edition" page no:184,

suppose we have a directory containing 2 sub directories from-stuff

and to-stuff, from-stuff contains an entire tree of files , symbolic links and so forth. something that is difficult to mirror precisely using a recursive cp. in  order to mirror the entire tree beneath from-stuff to to-stuff , we could use the commands:

cd from-stuff

tar cf - . | (cd ../to-stuff; tar xvf -)

can any one explain me how this command works ?

what is this - ?

---

### Post by Cypher on 2009-06-05
Let's take a look arguments first to Tar.

[C]reate
[F]ile
e[X]tract
[V]erbose

So the first thing is to go into the "from-stuff" directory and the command
```

tar -cf - .

```
This says create a TAR archive to a file name "-" from the current directories contents (".") The "-" means send the contents to the screen.

The outout of this first part is "piped" (|) to the second part which changes the directory to "to-stuff" and then does
```

tar xvf -

```
So this tar command is extracting with verbositing the file named "-" and in this context "-" is screen contents that were "piped" to us from the previous tar command.

TAR is VERY smart about dealing with hidden files, symbolic links and other things so it sanely sends all that information to the screen which is piped ot the second tar command that "extracts" the data to the new directory.

There ya go..

---

### Post by KIAaze on 2009-06-05
```
tar c . | (cd ../to-stuff; tar xv)
```
works too, since tar uses standard output/input by default. :)

It seems I was too slow. I didn't know what the '-' was for and finally found an explanation here: [https://vb.serverknecht.de/showthread.php?t=143562](https://vb.serverknecht.de/showthread.php?t=143562)

---

