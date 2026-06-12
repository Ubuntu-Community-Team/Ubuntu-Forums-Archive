---
title: "Script + txt files"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by any.linux12 on 2009-01-08
Hi 

I need to know how I open a txt file to search for a word with bash script. Maybe I should give an exemple:

>  I need to enter in a txt file in this case with the following content, search for the following lines and store in a variable the content next to lib32

changed: lib32
metadata the same, data changed: lib32/jniwrap.lic
new: lib32/ruben file
new: lib32/ruben file 2
new: lib32/ruben file 2~

Thanks in advance!

---

### Post by Titan8990 on 2009-01-08
You don't have to open it...


See:


man grep

---

### Post by any.linux12 on 2009-01-08
Sorry but I'm a little blind

How can I do a 

grep ex1.txt (and search for one word?)

---

### Post by Achetar on 2009-01-08
```

$ cat -n ex1.txt | grep whatever

```The -n prints the line number along with the line. The | pipes the results of cat through grep, which searches for the word whatever (change the word to anything you like). To search for a phrase, enclose it in quotes, like so:

```

$ cat -n ex1.txt | grep "My phrase that I am searching for"

```Note that grep is case sensitive. There may be a flag, to make it case insensitive, I am not sure.

You can also use regex by using the -e flag with grep. Example:
```

$ cat -n ex1.txt | grep -e "[Mm]y [Pp]hrase [Ww]ith [Rr]egex"

```That would find all lines that contain "My Phrase With Regex", 'my phrase with regex', 'My phrase With regex', etc. Full guides and cheatsheets on regex are available via google.

To search and replace, you can use sed:
```

$ sed -i 's/alpha/beta/g' ex1.txt

```That would  replace all instances of alpha with beta. That would also change '2alpha1' to '2beta1'. If you want to do whole words only, just place spaces before and after the word like so:
```

$ sed -i 's/ alpha / beta /g' ex1.txt

```Regex also works with sed.

---

### Post by bodhi.zazen on 2009-01-08
:lolflag:

It is "bad form" to cat | grep , just grep directly

so ... rather then 

cat file.txt | grep "Search parameters"

just 

```
grep "Search parameters" file.txt
```congrats on getting the sed correct though, some people do not know the -i flag and will

cat | sed > file_new.txt

:guitar:

---

### Post by Titan8990 on 2009-01-08
Good tip on the grep -e, I was under the impression from school teachings that grep always used Regex.

---

### Post by kaibob on 2009-01-08
Good thread--I'm not familiar with grep and this thread is instructive. 

The OP said that he wants to obtain the "content next to lib32." I assume he means after lib32. Is the following the best way to do this?

```
grep 'lib32' filename | cut -d '/' -f2
```

---

### Post by unutbu on 2009-01-08
```
awk 'BEGIN { FS="lib32/"; } { print $2; }' filename
```

FS="lib32/" sets the field separator to "lib32/". This breaks each line into separate fields each time the string "lib32/" is encountered. The second field is everything after "lib32/" -- assuming the string "lib32/" appears only once per line.

The output would be 
```

jniwrap.lic
ruben file
ruben file 2
ruben file 2~ 
```

Here is a second way which could handle multiple occurrences of "lib32/":
```

grep -o 'lib32.*' filename | cut -c 7-
```

The -o flag tells grep to print only the part of the line which matches the pattern.
So ```


grep -o 'lib32.*' filename
```

returns 
```

lib32
lib32/jniwrap.lic
lib32/ruben file
lib32/ruben file 2
lib32/ruben file 2~ 
```

The 
```

cut -c 7-

```
command then prints everything from the 7th character till the end of the line.

---

### Post by Achetar on 2009-01-12
> **bodhi.zazen said:**
> :lolflag:

It is "bad form" to cat | grep , just grep directly

so ... rather then 

cat file.txt | grep "Search parameters"

just 

```
grep "Search parameters" file.txt
```congrats on getting the sed correct though, some people do not know the -i flag and will

cat | sed > file_new.txt

:guitar:
I used cat because it can print the line numbers, which grep won't do (to my knowledge).

---

### Post by bodhi.zazen on 2009-01-12
> **Achetar said:**
> I used cat because it can print the line numbers, which grep won't do (to my knowledge).

use -n

> grep -n . /etc/fstab
1:# /etc/fstab: static file system information.
2:#
3:# <file system> <mount point>   <type>  <options>       <dump>  <pass>
[noparse]4:proc[/noparse]            /proc           proc    defaults        0       0
5:# /dev/mapper/jaunty-root
6:UUID=a7741f2b-3e0c-44c3-9a57-538484672197 /               ext3    relatime,errors=remount-ro 0       1
7:# /dev/sda5
8:UUID=e14b44f8-fbe3-4b59-bace-348c8601677a /boot           ext2    relatime        0       2
9:# /dev/mapper/jaunty-swap_1
10:UUID=7b7cc1d2-2f37-4caf-832d-ab086c5de02f none            swap    sw              0       0
11:/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0Notice the line numbers :twisted:

---

### Post by Achetar on 2009-01-12
Ah tyvm. Maybe I should write a guide about this...

---

### Post by bodhi.zazen on 2009-01-12
> **Achetar said:**
> Ah tyvm. Maybe I should write a guide about this...

You are most welcome. Learning grep, sed, awk all very powerful.

---

