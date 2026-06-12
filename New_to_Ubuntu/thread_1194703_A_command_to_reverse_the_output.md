---
title: "A command to reverse the output"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Kedster on 2009-06-22
what i would like to do is use the echo command with the sort cmmand i think to give a reverse  output so if i type in 
Jordan Ketterer
it will come out 
rerettek nadroj

i think it is something similar to this 
```
echo "Jordan Ketterer" | sort -r
```
but that doesn't change it the sort doesn't work, it comes out the same (forward). Any ideas

---

### Post by unutbu on 2009-06-22
```
echo "Jordan Ketterer" | rev
```

PS. I didn't know the right command, but I found it by typing
```

man -k reverse
```

---

### Post by Kedster on 2009-06-22
Thank you.
That was very quick. but would you be able to explain how you got the command. As in what is 
```
man -k reverse
```

how does it work and how could I use it in the future

---

### Post by Kedster on 2009-06-22
lol ok now id like to try something else. What i would like to do is save this to the bottom of a txt file and have it put the regular name then on the next line the reverse name and then a blank line so that is would look like this after it were done a few times 
> Jordan Ketterer
reretteK nadorJ

Harry Ketterer
reretteK yrraH


and so on
is there a way to do this

---

### Post by Clorow on 2009-06-23
Here's a shell script:

```

#!/bin/bash
echo $1
echo $1 | rev
exit 0

```Save that as a file, and make it executable by right-clicking the file in nautilus and going to Properties > Permissions.

Now cd to the directory you put the file in and type in:
```

./filename "Jordan Ketterer" >> output_file
./filename "Harry Ketterer" >> output_file

```

---

### Post by Clorow on 2009-06-23
Even better:
```

#!/bin/bash
while [ -n "$1" ]
do
    echo $1
    echo $1 | rev
    echo
    shift
done
exit 0

```Now you can do:
```

./filename "Jordan Ketterer" "Harry Ketterer" >> output_file

```

Also, "man -k reverse" searches the man pages for a command that has "reverse" in its description. It will do the same thing as typing "apropos reverse", and I like apropos better just because of the name.

---

### Post by Kedster on 2009-06-23
Thanks Clorow That works perfectly. Im happy that I'm learning as i do this. That would be called a script right? or is it something else. Well thank you for your knowledge and that works great. LOL the reason i need this is actually for school sorta. its for an extra assignment for a book that we were reading. I knew that id seen the reverse command used with echo to do this before but i thought it was piped through sort to reverse it. Now I even have it doing that formating for me thanks again.

---

### Post by VCoolio on 2009-06-23
You may like [this]("http://www.revfad.com/flip.html").

---

### Post by decoherence on 2009-06-23
> **Kedster said:**
> Thank you.
That was very quick. but would you be able to explain how you got the command. As in what is 
```
man -k reverse
```

how does it work and how could I use it in the future

maybe i missed the answer, but here it is anyway

man -k reserve searches the manual pages for the keyword "reverse." You also commonly see "apropos reverse" which would do the same thing.

so, if you wanted to see what commands had something to do with networking, you'd do 'man -k network' or 'apropos network' .... remember, this is just a keyword. rather than 'network' you could say 'networking' or 'net' -- you'd get different results. treat it like google and experiment.

apropos/man -k is a great way to explore what the system is capable of. use a straight man command to figure out how a command you found works, for instance.
```

decoherence@mine:~$ man -k reverse
build-rdeps (1)      - find packages that depend on a specific package to bui...
col (1)              - filter reverse line feeds from input
GG_CIRCLEQ_FOREACH_REVERSE (3) - implementations of singly-linked lists, simp...
GG_TAILQ_FOREACH_REVERSE (3) - implementations of singly-linked lists, simple...
rev (1)              - reverse lines of a file or files
tac (1)              - concatenate and print files in reverse
xxd (1)              - make a hexdump or do the reverse.

decoherence@mine:~$ man rev
REV(1)                    BSD General Commands Manual                   REV(1)

NAME
     rev - reverse lines of a file or files

SYNOPSIS
     rev [file ...]

DESCRIPTION
     The rev utility copies the specified files to the standard output,
     reversing the order of characters in every line.  If no files are speci&#8208;
     fied, the standard input is read...

etc.

```

I'll say again, this is the best way to explore your system. Unlike what you find on Google, you can be certain this documentation actually applies to your specific system. Don't get me wrong, Google is a great supplement when manual pages are too terse or verbose, but being able to navigate the wealth of built-in docs will give you a huge edge.

---

### Post by ghostdog74 on 2009-06-24
> **Kedster said:**
> lol ok now id like to try something else. What i would like to do is save this to the bottom of a txt file and have it put the regular name then on the next line the reverse name and then a blank line so that is would look like this after it were done a few times 

and so on
is there a way to do this

put your names in a file, one name per line
```

#!/bin/bash
awk '{
    print     
    rev($0) 
    print "\n-----------"
}
function rev(s  ,r){
    m=split(s,str,"")
    for(i=m;i>0;i--){ printf str[i] }
}' file


```

output
```

# more file
Jordan Ketterer
Harry Ketterer

# ./test.sh
Jordan Ketterer
reretteK nadroJ
-----------
Harry Ketterer
reretteK yrraH
-----------


```

using rev
```

# rev < file

```

---

