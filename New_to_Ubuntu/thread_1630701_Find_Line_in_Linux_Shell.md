---
title: "Find Line in Linux Shell"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-11-25
Hei Community,

I like to process a text file by finding a line with a certain word. Then I would like to copy the lines that are followed by that line into another file. The trouble is, that I do not know the command which gives me the line number, in which I can find the word. If I enter something like
```
grep -n 'Christmas'
```the programm will not only return the line number but also the line itsself.

Can you help me out with that?

---

### Post by skillet-thief on 2010-11-25
You might consider csplit. From the docs:
> 

`/REGEXP/[OFFSET]'
     Create an output file containing the current line up to (but not
     including) the next line of the input file that contains a match
     for REGEXP.  The optional OFFSET is an integer.  If it is given,
     the input up to (but not including) the matching line plus or
     minus OFFSET is put into the output file, and the line after that
     begins the next section of input.

`%REGEXP%[OFFSET]'
     Like the previous type, except that it does not create an output
     file, so that section of the input file is effectively ignored.


---

### Post by Peter.Paul on 2010-11-25
thx for that. I do not know how to use your quote

csplit filename 'Christmas' does not work and I can not find examples with google.

---

### Post by Hippytaff on 2010-11-25
try
```

cat text.file | grep -i christmas > output.txt

```
where text.file is the name of the file you want to find the line in

---

### Post by skillet-thief on 2010-11-25
csplit makes little files from your initial file.

```
$ csplit myfile.txt --prefix output /Christmas/
```

should creat two new files, output00 and output01. output01 should contain the lines you want. You may have to play around with it some more to get exactly what you want.

For the details:

```
$ info coreutils
```

csplit is in the "Output of parts of files" section.

---

