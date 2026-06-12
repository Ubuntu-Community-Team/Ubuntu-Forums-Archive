---
title: "Unzipping multiple Zipfiles"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Bob63 on 2009-08-19
First...
I have a directory which contains multiple zipfiles:
a.zip
b.zip
   .
   .
   .
z.zip
I am interested in a script that will unzip each archive in the directory. I can create a file listing with [FONT=Courier New]ls[/FONT], piped to a textfile, but cannot figure out how to use this as the input to unzip.

Second...
Originally the above archives were in a larger "master archive" with directories containing the sub-archives (each sub-archive contains one or more textfiles). Is it possible to write a script that either a) extracts all archives to one directory and then extracts each file to the same directory, or b) extracts the archives in their directories then "walks" the resulting directory tree, extracting all archives as it goes.

I'm a noob at scripting, but willing to try anything (bash, python, etc.) to get what I'm after here.

Thanks in advance,
Bob

---

### Post by nikhilbhardwaj on 2009-08-19
a bash script 
with a for loop should do it for you
i'll assume that you have used ls to get the names of the zip files one file per line


```

!/bin/bash
#change filelist to the name of your file whhere ls output is stored
for i in `grep -v '^#' filelist`
do
  unzip $i
done
# that should unzip all your files

```
save it and make the file executable

let me know if this works for you
and the other tasks you mentioned arent that complex either and you can do them with minimal scripting
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
should be a good place to start

---

### Post by kanikilu on 2009-08-19
If you just want to unzip all files in your current directory to the same directory, something as simple as this should work:
```
for file in *.zip; do unzip $file; done
```
I'm not really sure about the second part of your question.

---

### Post by nikhilbhardwaj on 2009-08-19
after you unzip the files
remove the .zip files or move them to a new location

now create a list of files lets say filelist that has the name of all the new zip files that were extracted from the original zip file

find . -name \*.zip
does the trick
and use the first script that i've written again

if you don't understand this
let me know and i'll write a polished version that can do all that you want

but i'd recommend that you try it out
and learn bash scripting you wont regret it

best of luck

---

### Post by Penguin Guy on 2009-08-19
If you're willing to learn, [[COLOR="Blue"]Linux Command[/COLOR]]("http://linuxcommand.gds.tuwien.ac.at/") is a good bash guide.

---

### Post by Bob63 on 2009-08-19
> **nikhilbhardwaj said:**
> a bash script 
with a for loop should do it for you
i'll assume that you have used ls to get the names of the zip files one file per line


```

!/bin/bash
#change filelist to the name of your file whhere ls output is stored
for i in `grep -v '^#' filelist`
do
  unzip i
done
# that should unzip all your files

```save it and make the file executable

let me know if this works for you
and the other tasks you mentioned arent that complex either and you can do them with minimal scripting
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
should be a good place to start

nikhilbhardwaj,
Tried your script. Seems to iterate the correct number of times, but variable i doesn't seem to be getting replaced by the filename from the list file. In the terminal I get:

unzip:  cannot find or open i, i.zip or i.ZIP.

57 times. :confused: If I run the grep statement by itself in the terminal, I do get the listing of the filenames, so that part does work.

---

### Post by Bob63 on 2009-08-19
> **kanikilu said:**
> If you just want to unzip all files in your current directory to the same directory, something as simple as this should work:
```
for file in *.zip; do unzip $file; done
```I'm not really sure about the second part of your question.

kanikilu,

Now that worked! Exactly what I needed, at least for part one.

---

### Post by nikhilbhardwaj on 2009-08-20
> **Bob63 said:**
> nikhilbhardwaj,
Tried your script. Seems to iterate the correct number of times, but variable i doesn't seem to be getting replaced by the filename from the list file. In the terminal I get:

unzip:  cannot find or open i, i.zip or i.ZIP.

57 times. :confused: If I run the grep statement by itself in the terminal, I do get the listing of the filenames, so that part does work.

i am an idiot
and i apologize for it
it should be $i and not just i

---

### Post by Bob63 on 2009-08-21
> **nikhilbhardwaj said:**
> i am an idiot
and i apologize for it
it should be $i and not just i

nikhilbhardwaj,

Eh, don't be too hard on yourself.  On the other hand, you didn't say which i to add the $ to, but I figured it out, thanks to your help. :)

[wishful thinking] Now if only I could figure out my second problem...[/wishful thinking]

Thank you for your help everyone!

---

### Post by nikhilbhardwaj on 2009-08-21
> **Bob63 said:**
> 
 b) extracts the archives in their directories then "walks" the resulting directory tree, extracting all archives as it goes.

let me understand you clearly
you are saying that those zip files create more zip files
into the same directory or subdirectories within the directory from which they had been extracted

and you want to extract them all to a single directory

is this what you want ?? 
if yes then its not that hard and with a slight modification to the original script we can achieve this

if not then explain clearly what you want
and we'll be able to do it too most probably

---

### Post by Bob63 on 2009-08-21
nikhilbhardwaj,

Yes. Inside the "master" zipfile is a directory tree with other zipfiles in the subdirectories. I want every zipfile expanded. Either extract all to one directory, or re-create the tree and extract them to their locations, makes no real difference, as long as I do not have to re-run unzip in each subdirectory.

Running unzip on the master zipfile, extract using re-create folders option will replicate the original tree, but using the extract all files option does not seem to unzip the subs.

---

### Post by nikhilbhardwaj on 2009-08-22
> **Bob63 said:**
> nikhilbhardwaj,

Yes. Inside the "master" zipfile is a directory tree with other zipfiles in the subdirectories. I want every zipfile expanded. Either extract all to one directory, or re-create the tree and extract them to their locations, makes no real difference, as long as I do not have to re-run unzip in each subdirectory.

Running unzip on the master zipfile, extract using re-create folders option will replicate the original tree, but using the extract all files option does not seem to unzip the subs.

```
#!/bin/bash

# first create a directory where we put the zip files after extracting them
if [ -d "../ZipFiles" ]
then
  echo ""
else
  mkdir ../ZipFiles
fi

# now create a list of zip files in filelist
find . -name '*.zip' > filelist

# also find the number of zip files this will tell us when to stop
totalFiles=`wc -l filelist| cut -d" " -f1`

if [ $totalFiles -ge 1 ]
then
  for i in `grep -v '^#' filelist`
  do
    unzip $i
    mv $i ../ZipFiles
  done
else
  echo "No Zipped files found in this directory"
fi
```

save it then execute it
that will extract the master archives
execute it again and all the newly extracted archives will be unzipped maintaining the directory tree
ie they will be extracted in the sub sub directories where they were created from the mater archives

if you need more help with this then let me know
you can even extract them all to the same directory
but i'll let you figure that out yourself

---

### Post by Bob63 on 2009-08-22
nikhilbhardwaj,

You sir, have the bash-ninjutsu! =D> This worked quite well. I did not need to re-run the script, and it extracted everything to the same directory which is fine.

To complete my understanding, please explain. I see the line:
```
find . -name '*.zip' > filelist

```I know that Linux is case-sensitive, so does this only find archives with a lowercase .zip extension? I have not looked at every zip file in the master archive; there are over 2000 files in the archive. I was not the person who originally created the master zipfile(s), and I do not know which OS they were created under, but I have seen some zipfiles elsewhere that have uppercase filenames and extensions.

Thank you so much for your help.

---

### Post by nikhilbhardwaj on 2009-08-23
> **Bob63 said:**
> nikhilbhardwaj,

You sir, have the bash-ninjutsu! =D> This worked quite well. I did not need to re-run the script, and it extracted everything to the same directory which is fine.

To complete my understanding, please explain. I see the line:
```
find . -name '*.zip' > filelist

```

i'm glad that i could help you
yes you are right linux is case sensitive and it only extracts the files that end with lower case 
but if you want case insensitive then replace it with
```

find . -iname '*.zip' > filelist

```
now it'll extract all files upper lower or mixed

what this does is that it finds all the files that have a .zip in their name and stores the result to a file named filelist

later in the script i check if the filelist is empty
if it is we do nothing otherwise the files are extracted and the zip files are moved to ../ZipFiles

---

### Post by Bob63 on 2009-08-23
nikhilbhardwaj,

Again, thanks very much for your help. As a point of interest, there were over 11,000 files in five master Zipfiles, once each of the masters had been unzipped. Your assistance has saved me quite a bit of additional work.

---

