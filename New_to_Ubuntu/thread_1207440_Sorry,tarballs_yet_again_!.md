---
title: "Sorry,tarballs yet again !"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-07-08
I have read all the threads on tarballs but still can't get the hang of decompressing them . I have been told to write tar -xjvf and the filename in terminal , but when I do I get " No such file " and then child 2 , whats that all about ? I know the file location is correct because I copied and pasted it from my download directory . I am trying to install further language directories for Freedict and they only seem to be available in tarballs. I know this topic has been explained before but mostly not in absolute beginner language . Thanks for reading this , I know you must get bored answering the same questions .

---

### Post by wpshooter on 2009-07-08
Have you tried just simply right-hand clicking on the file and then choosing **extract to here** from the menu ?

---

### Post by philinux on 2009-07-08
+1 wpshooter.
And just double click it to see the contents before you extract. Simple

---

### Post by tchoklat on 2009-07-08
**# 1: Uncompress tarball**

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/
**# 2: Build and install software**

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install
Where,
[LIST]
[*]./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
[*]make will compile all the source files into executable binaries.
[*]Finally, make install will install the binaries and any supporting files into the appropriate locations.
[/LIST]

---

### Post by AndyCee on 2009-07-08
+1 to what has already been said.

Just for technical closure (if you want) what is the extension of the file (or whole name)? I normally use:

```
$ tar -xvvf <filename>
```

if my file ends in a ".tar.gz". The man page I'm reading says to be safe for ".tar.bz" (or whatever so long as it's been zipped using bzip) is to use:
```

$ tar -xvf --bzip <filename>
```

Just curious.

EDIT: Looks like tchoklat answered my question (though I think you need a '-' before flags)

---

### Post by ex-wirecutter on 2009-07-08
Thanks for the suggestions , but I'm afraid they don't help with this problem of the tar command not being able to find the file , and when I try right cliking to extract the file I want is greyed out and wont respond . I think I will give up on tarballs ,fortunately I can just boot into Windows and use  a translation dictionary on that .
Thanks anyway fellas .

---

### Post by Paqman on 2009-07-08
> **ex-wirecutter said:**
> when I try right cliking to extract the file I want is greyed out and wont respond

What are the permissions on the tarball?

---

### Post by Celauran on 2009-07-08
If you're going to use the tar command from the terminal, make sure you either navigate to the directory containing the file or specify the path as an argument to tar. If tar isn't finding the file, you're not having it look in the right place.

---

### Post by tchoklat on 2009-07-08
> **Celauran said:**
> If you're going to use the tar command from the terminal, make sure you either navigate to the directory containing the file or specify the path as an argument to tar. If tar isn't finding the file, you're not having it look in the right place.

correct. You need to cd to the directory with the tar ball in it. Then execute the unzip command, and yes you need a '-' before the options.

tchoklat

---

### Post by ex-wirecutter on 2009-07-08
Sorry you've got me with this permissions , all I know is it ends in tar.bz2 and as regards the tar not looking in the right place if I've cut and pasted the file location how can it be wrong ? As I say I think despite all the help , for which I am grateful , I will give up .

---

### Post by Mornedhel on 2009-07-08
> **tchoklat said:**
> and yes you need a '-' before the options.

No you don't. Several programs, including tar and ps, can use bare letter options. The man page makes no mention of this for tar and uses short (single-dash) and long (double-dash) options everywhere, but it does work.

---

### Post by Paqman on 2009-07-08
> **ex-wirecutter said:**
> Sorry you've got me with this permissions , all I know is it ends in tar.bz2 and as regards the tar not looking in the right place if I've cut and pasted the file location how can it be wrong ? As I say I think despite all the help , for which I am grateful , I will give up .

On a Linux system every file has permissions. They define who is allowed to do what to that file. Your problem is that you weren't the file's owner. There's a lot of ways around that, but the simplest would be to open the terminal and:
```

chown username:username /name/of/file

```

I'm a bit confused about how you ended up with a tarball that wasn't owned by you, since everything you download through your browser should be yours.

---

### Post by AndyCee on 2009-07-10
> **Mornedhel said:**
> No you don't. Several programs, including tar and ps, can use bare letter options. The man page makes no mention of this for tar and uses short (single-dash) and long (double-dash) options everywhere, but it does work.

So it does. Creepy. Personally I wouldn't advise it for the sake of consistency across apps and platforms, but interesting to know.

---

