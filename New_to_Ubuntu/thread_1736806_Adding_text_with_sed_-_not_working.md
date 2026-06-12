---
title: "Adding text with sed - not working"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by aleifr on 2011-04-22
Ok, I'm pretty sure I'm doing, but it just isn't working.

```
touch test.rtf
sed '$a\
line1\
line2\
last line' test.rtf
```

"cat test.rtf" shows nothing. I also tried:

```
touch test.rtf
sed '$a\
line1\
line2\
last line' test.rtf > test2.rtf
mv test2.rtf test.rtf
```

But got the same result. I just don't understand it because I'm pretty damn close to 100% sure I'm doing it right, but nothing happens.

---

### Post by Vaphell on 2011-04-22
these certainly work
```
echo | sed '$a\
line1\
line2\
last line'

echo | sed '$a\nline1\nline2\nlast line'
```

most likely empty file is so empty that it doesn't trigger anything in sed (no newline)

---

### Post by aleifr on 2011-04-23
> **Vaphell said:**
> these certainly work
```
echo | sed '$a\
line1\
line2\
last line'

echo | sed '$a\nline1\nline2\nlast line'
```

most likely empty file is so empty that it doesn't trigger anything in sed (no newline)

Mmh, I think that got me closer, but where does the name of the file come in in that code? Using only that, I get some output in the terminal, but it doesn't change the file.

---

### Post by lloyd_b on 2011-04-23
> **aleifr said:**
> Mmh, I think that got me closer, but where does the name of the file come in in that code? Using only that, I get some output in the terminal, but it doesn't change the file.

sed's default behavior is to make the changes, and then send the output to "STDOUT" (the terminal, unless you've redirected it.

Two ways to change this:

1.  Use the "-i" option of sed.  This tells sed to write the changes back to the input file.
```
sed -i 's/fred/wilma/g' infile.txt
```

2.  Use shell redirection to write STDOUT to a file
```
sed 's/fred/wilma/g' infile.txt > outfile.txt
```

Lloyd B.

---

### Post by Vaphell on 2011-04-23
my example didn't use any file but echoed an empty string to show that the sed part was sound.

**echo 'string' | sed '...'** means that sed takes input from echo output, not from file (sed '...' file)
if you want to change file in place you need -i to modify source or redirect to output file just as lloyd_b said.
there is 1 problem though - empty file has NO lines and sed works line by line. If there are no lines, it won't do anything. Put 1 or 2 enters in the file and your command will magically start to work.

---

