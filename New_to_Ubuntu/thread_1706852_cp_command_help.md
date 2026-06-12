---
title: "cp command help"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by mpranav007 on 2011-03-14
Hi,

I have around 500 files in a folder. But I don't want to copy all of them. The name of the files that I want to copy is in a txt file.

The question is how to use the names from the txt file as arguments for the cp command.

---

### Post by johntaylor1887 on 2011-03-14
```
cp /home/user/folder/*.txt /destination/directory 
```
Just as an example. It will copy all of the txt files.

---

### Post by cap10Ibraim on 2011-03-14
```

cp `cat 1.txt` /destination

```
note the quotes ! files names are in 1.txt (example)
this quote in near the 1 key in the top of the keyboard

---

### Post by mpranav007 on 2011-03-14
$ cp `cat try.txt` /home/pranav/ansari/
cp: cannot stat `/home/pranav/Azureus': No such file or directory
cp: cannot stat `Downloads/OReilly': No such file or directory
cp: cannot stat `4': No such file or directory
cp: cannot stat `GB': No such file or directory
cp: cannot stat `Collection/O\'Reilly': No such file or directory
cp: cannot stat `-': No such file or directory
cp: cannot stat `802.11': No such file or directory
cp: cannot stat `Wireles': No such file or directory
cp: cannot stat `Networks': No such file or directory
cp: cannot stat `The': No such file or directory
cp: cannot stat `Definitive': No such file or directory
cp: cannot stat `Guide.pdf': No such file or directory


this is my output..:(

---

### Post by cap10Ibraim on 2011-03-14
try 
```

cp `cat 1.txt` /destination -R

```

---

### Post by mpranav007 on 2011-03-14
still i get the same output as above :(

---

### Post by cap10Ibraim on 2011-03-14
I think the file names are wrong 
like 
are these files in your home ? 
```

cp: cannot stat `4': No such file or directory
cp: cannot stat `GB': No such file or directory
cp: cannot stat `Collection/O\'Reilly': No such file or directory
cp: cannot stat `-': No such file or directory
cp: cannot stat `802.11': No such file or directory
cp: cannot stat `Wireles': No such file or directory
cp: cannot stat `Networks': No such file or directory
cp: cannot stat `The': No such file or directory
cp: cannot stat `Definitive': No such file or directory
cp: cannot stat `Guide.pdf': No such file or directory

```

---

### Post by mpranav007 on 2011-03-14
they aren't fileS actually.....it is a single file. "O'Reilly - 802.11 Wireles Networks The Definitive Guide" is the name of the file

---

### Post by cap10Ibraim on 2011-03-14
oh , i think the problem is in the spaces when there is a space the command think it's the next file

---

### Post by mpranav007 on 2011-03-14
so wat should i do??

---

### Post by GWBouge on 2011-03-14
Use a script!  XoD

I know more about Python than bash or shell commands, so I just threw this together.

```
#! /usr/bin/python

import os, sys, shutil

src = sys.argv[-2]
dest = sys.argv[-1]

FILE = open(os.path.abspath(src), 'r')
files = FILE.readlines()
FILE.close()

for f in files:
	shutil.copy(os.path.abspath(f.rstrip()), dest)
```

Copy that and save it as copy_from_text.py or whatever.  Easiest to save it in the same directory as the txt file you're using.  Run it with python, or make it executable and run it directly.  Usage:

```
# With python
$ python copy_from_text.py input.txt /output/path

# Directly
$ chmod +x copy_from_text.py
$ ./copy_from_text.py input.txt /output/path
```

---

### Post by cap10Ibraim on 2011-03-14
another approach is to replace the spaces with a * int the text file if the following is the text file 
```

1.txt
2*2.txt
dir1
new
Unsaved*Document*1

```
the again
cp `cat 1.txt` /destination -R

---

### Post by sisco311 on 2011-03-14
Assuming that the filenames are separated by a newline in the text file, you can do something like:
```
while read -r file ; do
  cp --backup=numbered -- "$file" /path/to/destination/directory
done < /path/to/txt/file.txt
```

---

### Post by gmargo on 2011-03-14
> **mpranav007 said:**
> $ cp `cat try.txt` /home/pranav/ansari/

Classic **xargs(1)** usage case:
```

xargs -d '\n' cp -p -t /home/pranav/ansari/ < try.txt

```(Added '-p' to preserve timestamps.)

---

### Post by Stephen Morgan on 2011-03-15
You could change the IFS variable, which indicates field seperator, from a space to a new-line.

---

