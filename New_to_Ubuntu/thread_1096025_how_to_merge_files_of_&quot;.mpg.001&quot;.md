---
title: "how to merge files of &quot;.mpg.001&quot;"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-14
Hi,
I was wondering how to merge files of ".mpg.001,...,.mpg.010"? Any package to install? How to use the command in the terminal?
Thanks in advance!

---

### Post by kaivalagi on 2009-03-14
If you downloaded these via BT I would assume they are part files for an archive and should be dealt with the app...probably rar based

You should be able to open the .001 file with "Archive Manager" and extract all...

I may be totally wrong, in which case you need to know what tool was used to split the original file and deal with accordingly...at a guess

---

### Post by Jose Catre-Vandis on 2009-03-14
hjsplit ?

or try lxsplit

it's a java app so cross platform

---

### Post by flylehe on 2009-03-14
I think the files are not rar-based, since there is no "rar" in the extension of the file names. Their names are just myvideo.mpg.001, myvideo.mpg.002,....
I used to use an application called "hjsplit.exe" to merge such files in Windows. I just don't know what is the equivalence in linux?

---

### Post by Francewhoa on 2009-09-06
HJsplit for Ubuntu [http://ubuntuforums.org/showthread.php?p=7909007#post7909007](http://ubuntuforums.org/showthread.php?p=7909007#post7909007)
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

---

### Post by leguman on 2009-09-30
nope it's not an archive, just a split file

you don't need to install hjsplit either

check out the command lines there :

[http://altbin.net/2009/09/split-001-002-files-with-linux.html](http://altbin.net/2009/09/split-001-002-files-with-linux.html)

as explained the best way is to use the par2 files that you probably "found" with your mpg, as it will check, repair, and join your file back together at the same time

if not, just use cat

---

### Post by RedRat on 2009-09-30
I use hjsplit, it runs quite well under Wine. Very easy to use and a very small program.

---

### Post by little_penguin on 2009-10-04
You can also use a mencoder command or Avidemux, see this thread:

[http://ubuntuforums.org/showthread.php?t=1281685](http://ubuntuforums.org/showthread.php?t=1281685)

---

### Post by stefangr1 on 2009-10-04
It's actually much simpler, mpeg is encoded on a per frame basis. You can just have the os past the files together, by something like:

cat file1.mpg file2.mpg > newfile.mpg

If you have some 100 files in a folder, you can do:

cat *.mpg > newfile.mpeg

---

### Post by leguman on 2009-10-07
little_penguin, I'm afraid this is not what is asked

---

### Post by little_penguin on 2009-10-07
@leguman
Hm ok, I thought it was about merging / joining mpg part files...

---

### Post by fulopattila122 on 2012-12-29
Alternatively you can use Double Commander: select all the files (.001, .002, etc) within Double Commander and choose Main menu -> Files -> Combine.

---

### Post by howefield on 2012-12-29
Old thread closed.

---

