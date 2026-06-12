---
title: "gpart and wipe?"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by degarb on 2011-02-13
Can gparted really wipe a drive to FBI certified cleanliness?  Or must use dban?

---

### Post by spikoley on 2011-02-13
I don't think Gparted has an option to wipe to FBI standards.  Run the live CD and install wipe.

```
sudo apt-get install wipe
```

```
man wipe
```

---

### Post by HermanAB on 2011-02-14
Well, since there is no such thing as 'FBI cleanliness'...

If you want to re-use a disk at the same or higher classification level, then overwrite it three times with /dev/urandom.  Otherwise, melt the disk with a torch.

---

### Post by degarb on 2011-02-14
> **HermanAB said:**
> Well, since there is no such thing as 'FBI cleanliness'...

If you want to re-use a disk at the same or higher classification level, then overwrite it three times with /dev/urandom.  Otherwise, melt the disk with a torch.

Got examples of /dev/urandom?    

Will wipe or /dev/urandom wipe free space without destroying your OS and data?  I re ad wipe can wipe folders or nuke files, but what about just something to wipe everything.

---

### Post by kn0w-b1nary on 2011-02-14
you can also use bleachbit:

sudo apt-get install bleachbit
sudo bleachbit

then select "wipe free disk space"

you can also shred files and folders with this tool, as well as log deletion, and other privacy related commands.

Hope this helps!

---

### Post by degarb on 2011-02-14
> **kn0w-b1nary said:**
> you can also use bleachbit:

then select "wipe free disk space"

you can also shred files and folders with this tool, as well as log deletion, and other privacy related commands.

Hope this helps!

I like this solution.  (Don't see info on number of passes by googling.  But could just do it several times to be sure.)

The problem with dban, I see, is it might wipe all drives and partitions on a computer.  Fine, in many cases, but possibly bad in others.  .... diskwipe looks like best windows solution (better than eraser).

Wipe's problem appears that it doesn't work after the fact of deletion.

So, if I got a friend with old computer they wish to give me, and I don't have dban.  I could install linux and do a bleachbit wipe, and be fairly certain they are safe.  

The other concern with all these is time it takes to wipe each 100 gig of space.  Dban, the machine would need to be dedicated.  While bleachbit's wipe, you might be able to still work on machine, and do later after I left with machine. 

The caveats that the FBI still might be able to recover, is bad.  While I doubt they could after 4 scrubs, this clause keeps the Salvation Army/Goodwill/someComputerShops/SomePeople from helping the poor with good cheap machines.  I also suspect the caveats (even after 3 or 4 scrubs) are more paranoia than rational.

---

### Post by jmszr on 2011-02-14
degarb,

You might find this of interest: [http://www.linux.com/learn/tutorials/406976:weekend-project-scrub-files-and-old-hard-drives-securely-on-linux](http://www.linux.com/learn/tutorials/406976:weekend-project-scrub-files-and-old-hard-drives-securely-on-linux).

---

