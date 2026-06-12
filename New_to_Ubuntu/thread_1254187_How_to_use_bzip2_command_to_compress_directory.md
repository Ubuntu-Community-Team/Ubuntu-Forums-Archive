---
title: "How to use bzip2 command to compress directory?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by colau on 2009-08-31
Hi,
```

bzip2 -c -1 workspace/ > abc.bz
bzip2: Input file workspace/ is a directory.

```
How can create a file named **abc.bz** compressing the directory **workspace**?

---

### Post by Cheezespread on 2009-08-31
> **colau said:**
> Hi,
```

bzip2 -c -1 workspace/ > abc.bz
bzip2: Input file workspace/ is a directory.

```
How can create a file named **abc.bz** compressing the directory **workspace**?

You can archive it using Tar and then zip it ?

---

### Post by colau on 2009-08-31
> **Cheezespread said:**
> You can archive it using Tar and then zip it ?
Trying to do that from command line.

---

### Post by gardara on 2009-08-31
> The bzip2 tools are not archiving tools. In order to compress a directory, the directory must be archived first. If you have a large directory, say TEMP, and you want more compression than gzip gives you, you will have to use the tar archiving tool to first archive the directory. Once the directory is archived it can be compressed with gzip2. So both commands for this would look like:

tar cf TEMP.tar TEMP

bzip2 TEMP.tar

The resulting file would be TEMP.tar.bz2

Taken from [http://www.brighthub.com/computing/linux/articles/16999.aspx](http://www.brighthub.com/computing/linux/articles/16999.aspx)

---

### Post by Rubicon_82 on 2009-08-31
You should use tar to archive the contents of a directory:

```

tar -cjf abc.tar.bz2 workspace/

```

---

### Post by Cheezespread on 2009-08-31
If you specifically want to use "bzip2 " command :

```
tar cf workspace.tar "path to workspace" (without the quotes)
bzip2 workspace.tar

```

Or

```
tar cjf workspace.tar.bz2 "path to workspace"
```

---

### Post by colau on 2009-08-31
Is it possible to do that using only bzip2 command?
Is making .tar format must before making .bz format?

---

### Post by Cheezespread on 2009-08-31
> **colau said:**
> Is it possible to do that using only bzip2 command?
Is making .tar format must before making .bz format?

As I understand , bzip and gzip are just compression algorithms. ANd they lack archiving properties and hence we using it alongside tar in Unix/Linux.

Hope [this]("http://en.wikipedia.org/wiki/Bzip2") helps.

---

### Post by Lampi on 2009-08-31
@Cheezespread: that's true but the OP talks about the application bzip2 - this one has poor file handling skills for the bzip algorithm (I quote from the manpage):
> bzip2 expects a list of file names to accompany the command-line flags.  Each file is replaced by a compressed version of itself, with the name  "original_name.bz2".   Each  com&#8208;
       pressed  file  has  the  same  modification  date, permissions, and, when possible, ownership as the corresponding original, so that these properties can be correctly restored at
       decompression time.  File name handling is naive in the sense that there is no mechanism for preserving original file names, permissions, ownerships or dates in filesystems which
       lack these concepts, or have serious file name length restrictions, such as MS-DOS.
So yes, I would always prefer tar over bzip2, because it has the better file handling.

---

### Post by Cheezespread on 2009-08-31
Oops.that was a typo. meant bzip2 infact :)

---

### Post by Liolikas on 2009-08-31
> **Lampi said:**
> @Cheezespread: that's true but the OP talks about the application bzip2 - this one has poor file handling skills for the bzip algorithm (I quote from the manpage):

So yes, I would always prefer tar over bzip2, because it has the better file handling.
if you do tar c so tar calls bzip2 to compress things.
Basically tar is like "glue" to make one file from entire folder and then you have to compress tar file. Looks like strange mess but in this way compression is ~10% better than just compress folder in winzip way. And after all you can do it simply by adding c option to tar command. Or use your favorite compression algorithm on tar file as other command. Or use default one with compress file.tar. Maybe more ways to do same. For xp users favorite should be GUI gnome fronted like "file roller" etc. where you click in windows style and still get better.

---

### Post by wojox on 2009-08-31
I like:

```
tar -cjf file.tar.bz2 dir
```

Replacing file with name of file and dir with directory.

---

