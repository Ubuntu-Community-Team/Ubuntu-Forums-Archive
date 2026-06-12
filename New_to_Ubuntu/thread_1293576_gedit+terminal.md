---
title: "gedit+terminal"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by kvakili on 2009-10-17
hey, i'm new to linux,

I have a bunch of text files with non-standard names in the same directory,
is there a way to use the terminal to copy past the content of all these files unto
a single text file ?

tia,

---

### Post by jrandolph on 2009-10-17
I dont really know the answer to this but you may want to look into the "cat" concatenate command 

Maybe someone on here can tell you is this would do what you wanted

---

### Post by sisco311 on 2009-10-17
Hi and welcome to the forums!

You can use the *cat* command to concatenate files.

cd to the directory where the files are:
```
cd path/to/dir
```

and run:
```
cat file1 file2 file3 > newfile
```

or:
```
cat ./* > newfile
```
to concatenate all the files.

---

### Post by jrandolph on 2009-10-17
Wow I cant believe i was actually right in my thinking - I dont know much about Linux but I knew I had used that once before

---

### Post by kvakili on 2009-10-17
> **sisco311 said:**
> Hi and welcome to the forums!

You can use the *cat* command to concatenate files.

cd to the directory where the files are:
```
cd path/to/dir
```and run:
```
cat file1 file2 file3 > newfile
```or:
```
cat ./* > newfile
```to concatenate all the files.


Hi,

thanks for the fast reply, works great

---

### Post by jrandolph on 2009-10-17
Does anyone know if this works for text files?
I cant get it to make a new file with all the text from other generic files that I created

---

### Post by jrandolph on 2009-10-17
I have tried and tried again and cant make it work - above my level of knowledge.
Maybe someone else will be able to help more

---

### Post by anaconda on 2009-10-17
> **jrandolph said:**
> Does anyone know if this works for text files?
I cant get it to make a new file with all the text from other generic files that I created

Yes it will work on text files.

Basically it works for any file that cat can show.

What kind of text files you have? And do they show correctly when you type:
cat filename.txt
???

---

### Post by jrandolph on 2009-10-17
well i just typed some useless text into some files to see if there was a way to put them together for the OP wanting to see if there was a way to put all files together without typing each file, but when i tried it i could not even get 3 files to cat together 
the files were jus text from open office word

---

### Post by MountainX on 2009-10-17
> **jrandolph said:**
> well i just typed some useless text into some files to see if there was a way to put them together for the OP wanting to see if there was a way to put all files together without typing each file, but when i tried it i could not even get 3 files to cat together 
the files were jus text from open office word

You know that the default file format for open office writer is .odt, right? That's not a plain text format. To make the "cat" command work correctlly, you need to save the files as Text (.txt). Is that what you were doing? If so, the command will work - make sure you type it exactly right.

---

### Post by jrandolph on 2009-10-17
> **MountainX said:**
> You know that the default file format for open office writer is .odt, right? That's not a plain text format. To make the "cat" command work correctlly, you need to save the files as Text (.txt). Is that what you were doing? If so, the command will work - make sure you type it exactly right.


I just found that out - i guess i have no idea what type of file the OP was using - i didnt know that it wouldnt work with a .odt file 
I got it to work with some files i made with text editor

---

### Post by Paqman on 2009-10-17
> **jrandolph said:**
> i didnt know that it wouldnt work with a .odt file 


That's because they have a ton of formatting and metadata in them, they aren't just the text you enter.

When you "cat" things together, all that metadata and stuff will just get stuck together and make a mess that isn't a valid .odt file.

Some types of file that have some error correction built into them (eg: video and audio) will work when you do this though.

---

### Post by jrandolph on 2009-10-17
Well to help out the Original Poster does anyone know if there is a command that you can use with cat to do all the files in a directory?

I mean i was only using a few files but they are talkin 500+ with odd names I looked into it and found that you can have the files numbered but i didnt know if there was another option that you could add in to cat all files of a certain directory

---

### Post by mcduck on 2009-10-17
> **jrandolph said:**
> Well to help out the Original Poster does anyone know if there is a command that you can use with cat to do all the files in a directory?

I mean i was only using a few files but they are talkin 500+ with odd names I looked into it and found that you can have the files numbered but i didnt know if there was another option that you could add in to cat all files of a certain directory

Assuming they are all .txt files, you can do something like this:
```

for f in *.txt; do cat $f >> newfile.txt; done
```

---

### Post by kvakili on 2009-10-17
> **mcduck said:**
> Assuming they are all .txt files, you can do something like this:
```

for f in *.txt; do cat $f >> newfile.txt; done
```


thanks mcduck, **sisco311's code solved the problem at hand, but i'm sure **your suggestion will come handy soon...

---

