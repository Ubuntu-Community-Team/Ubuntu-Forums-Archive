---
title: "Line break problem"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by rogerio.valente on 2009-02-03
Hello All.

I have a process where creates a new output file from one formated file. 
This process has to crate a file with:

original file name + "," + original file crc + "," + original file line.

I do this in a for statement in a shell script.
This is the code:
```

for arq in PCA*.REM ; do 
  crc=`cksum $arquivo | cut -c1-10`
  nomearq=`echo $arquivo | cut -d\/ -f6`
  for line in `cat $arq` ; do
    echo $nomearq ",""0," $crc"," $line  >> newfile.txt
  done
done

```

Example;

The file may.txt contains following line:
"ROGERIO ALCANTARA VALENTE" 

When I check the output file it has the "$line" field does not have the 
entire line from old file. In each space found in the "$line" is 
included a break line and my new file couldn't be read in the next step. 
The newfile.txt contains 3 lines instead of 1.

"may.txt,0,ROGERIO"
"may.txt,0,ALCANTARA"
"may.txt,0,VALENTE"


Does anyone know what is wrong?
Thanks in advance.

---

### Post by rrashkin on 2009-02-03
I'm certainly no BASH expert but no one else seems to be lining up.

I gather that the value of $arg is "may.txt".  What happens if you do: "cat may.txt" by itself in a shell?  That is, are the spaces interpreted properly?

---

### Post by Hospadar on 2009-02-03
Apperently that for loop loops through each word, I don't know why, lines seem more sensible to me, but meh.  Anywho, you'll have to use a different loop.

You could try using, for example:
```

cat $arq | while read line; do
echo $line;
#do whatever else you need to do
done;

```

---

### Post by rogerio.valente on 2009-02-04
> **Hospadar said:**
> Apperently that for loop loops through each word, I don't know why, lines seem more sensible to me, but meh.  Anywho, you'll have to use a different loop.

You could try using, for example:
```

cat $arq | while read line; do
echo $line;
#do whatever else you need to do
done;

```

Thanks Hospadar,

Well, I tried your tip and the result was good.
The new file was generated with just one line for each old file's line.

Now I have to find a solution to mantain the original spaces between the strings sequence from old file.

It's a interface file wich is to send new records from one software to another and has a particular format.

---

### Post by rogerio.valente on 2009-02-04
The "echo" command breaks line every time an space is found in a string. 
I do replace all space character by "#" character in "cat" command at the "for" statement and then replace it by space character when the "echo" command is invoked.

So, my script code looks like:

```

for arq in PCA*.REM ; do 
  crc=`cksum $arquivo | cut -c1-10`
  nomearq=`echo $arquivo | cut -d\/ -f6`
  for line in `cat $arq | tr ' ' '#'` ; do
    echo $nomearq",""0,"$crc","$line | tr '#' ' '  >> newfile.txt
  done
done

```

I don't know if it's the best solution, but it works. :D

---

