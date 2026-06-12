---
title: "how to do a sed loop?"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by Miguellint on 2011-01-15
Hi all...I'm very confused.

Not even sure if it's really an ubuntuforums problem but this is the only place I know where I might find computerates on a Saturday night :-)

I have a text file which has info on sixty people.
Each person has three pieces of info (name, age, sex), each piece of info on a consecutive line.

For example:

Bob
25
Male

Alice
28
Female
   .
   .
   .
   .
Jim
36
Male

I want sed to output the first line (Bob) to a new file called everyone.csv, then insert a comma, then **on the same line** add the next bit of info about Bob, which is 25, then a comma then **again on the same line** add the third bit of info, which is Male.

Then sed starts a new line in everyone.csv and does the same for Alice.

Then the next line etc...until finishing up with Jim.

The output file (everyone.csv) should look like this....

Bob, 25, Male
Alice, 28, Female
   .
   .
   .
Jim, 36, Male

everyone.csv is then ready for gnumeric to load.

I think a nested loop is what I'm looking for. The inner loop counting to three and the outer loop counting to sixty.

Plus, obviously, a working sed command. Unless sed is the wrong tool and I've wasted the last few hours of my life.

Can anyone help. Or point me to a forum where I might get some sed help.

Many thanks
Miguel

---

### Post by Vaphell on 2011-01-15
sed is a great tool to know, so you haven't really wasted anything. It will come handy later.

```
cat ppl.txt | sed '/^$/d' | awk '{printf("%s%s", $0, (NR%3 ? "," : "\n"))}' > everyone.csv
```

1. read ppl.txt
2. remove empty lines to get a predictable format
3. construct a new line from threes of lines and write it in everyone.csv
- take rows in order, if the row number is not divisible by 3 print **LINE,** otherwise print **LINE<newline>**

---

### Post by The Cog on 2011-01-15
or
```
cat ppl.txt | tr '\n' ',' | sed 's/,,/\n/g' > everyone.csv
```
* read the file
* translate newlines to commas
* replace double commas with newlines

I haven't had the courage to look at awk yet.

---

### Post by Vaphell on 2011-01-15
your version makes an assumption of only 1 line of space between records which may or may not be the case
mine is not perfect either, single space in empty line would make if fail, ^\s*$ in sed should make things more robust.

---

### Post by zer010 on 2011-01-15
I've only scratched the surface of using sed and have shyed away from awk. What I'm wondering is how one gets to know the meaning of things like 
"%s%s", $0, (NR%3 ? "," : "\n"
'/^$/d' and such.

---

### Post by tgm4883 on 2011-01-15
> **zer010 said:**
> I've only scratched the surface of using sed and have shyed away from awk. What I'm wondering is how one gets to know the meaning of things like 
"%s%s", $0, (NR%3 ? "," : "\n"
'/^$/d' and such.

Man pages and help switches. It's all syntax of some command or another.

---

### Post by sisco311 on 2011-01-15
> **Vaphell said:**
> your version makes an assumption of only 1 line of space between records which may or may not be the case
mine is not perfect either, single space in empty line would make if fail, ^\s*$ in sed should make things more robust.

This should do the trick:
```
awk '{if ($NF>0) printf("%s%s", $0, (NR%3 ? ", " : "\n")); else NR--}' file > newfile
```

Also, cat is a useful command, but it's overused. 

Instead of **cat file | sed whatever**, one should use:
```
sed whatever file
```
If the command doesn't accept a filename as an argument, like tr, then one should use redirection:
```
tr ' ' '\n' < file
```

---

### Post by Vaphell on 2011-01-15
i learnt a lot by googling e.g by 'bash replace', 'bash substring' or 'bash merge lines single line'
you can find a lot of neat tricks and with the help of man pages you can deconstruct them to understand what they exactly do

actually this is the 2nd time i used awk, yesterday being the first :-)

---

### Post by tgm4883 on 2011-01-15
I was bored, so I decided to do it in Python since everyone else was using bash commands. As you can see, for a small task like just putting it into a csv file Python might not be the best choice. But at the count == 4 section, you could do anything you wanted with the record.

```
#!/usr/bin/env python

f = open("people.txt") # Open the text file
rf = open("people.csv", "w") # Open a new CSV file for writing.

count = 1 # Keep count of what datatype we are working with
for l in f: # Examine each line in the open file
  data = l.strip()  # Strips out all non-printable characters, extra leading/trailing spaces
  if not data == "":  # Strips out empty lines
    if count == 1:  
      name = data
    elif count == 2: 
      age = data
    elif count == 3:
      sex = data
    count = count+1  # Increase count to the next datatype
  else:  # If an empty line, skip it altogether
    pass
  if count == 4: # If we have all three data types, do something with the record
    rf.write(name+','+age+','+sex+'\n')  ## Add the record to the csv file (this doesn't write the file yet)
    count = 1 # Reset count to 1 to get the next persons name
f.close() # Close the text file now that it is no longer needed
rf.close() # close and write to the csv file
```

---

### Post by sisco311 on 2011-01-15
Mine is in awk (awk != bash). Well except the redirection part which should work in most of the shells. 

Here is a bash variant:
```
#!/usr/bin/env bash

_err ()
{
  echo "$0: $1: No such file" >&2
  echo "USAGE: $0 [ filename ]" >&2
  exit 1
}

FILE="$1"
FILE="${FILE:-/home/sisco/xtmp/file}"
[ ! -f "$FILE" ] && _err "$FILE"

i=1
for line in $(< "$FILE"); do
  LINE="${line//[ \t]/}"
  if [ "$LINE" ]; then
    if (( i%3 )); then
      echo -n "${line}, "
    else
      echo "${line}" 
    fi
    i=$((++i))
  fi
done

```

---

### Post by Vaphell on 2011-01-15
some kind of array and modulo arithmetic would shave few lines off

```
record[count%3] = data
if count%3 == 0:
  rf.write( ",".join( record ) )
```

---

### Post by tgm4883 on 2011-01-15
> **sisco311 said:**
> Mine is in awk (awk != bash). Well except the redirection part which should work in most of the shells. 

Here is a bash variant:
```
#!/usr/bin/env bash

_err ()
{
  echo "$0: $1: No such file" >&2
  echo "USAGE: $0 [ filename ]" >&2
  exit 1
}

FILE="$1"
FILE="${FILE:-/home/sisco/xtmp/file}"
[ ! -f "$FILE" ] && _err "$FILE"

i=1
for line in $(< "$FILE"); do
  LINE="${line//[ \t]/}"
  if [ "$LINE" ]; then
    if (( i%3 )); then
      echo -n "${line}, "
    else
      echo "${line}" 
    fi
    i=$((++i))
  fi
done

```

Sorry, I didn't really mean bash. I meant cmd line variants.

---

### Post by The Cog on 2011-01-16
> **Vaphell said:**
> some kind of array and modulo arithmetic would shave few lines off

```
record[count%3] = data
if count%3 == 0:
  rf.write( ",".join( record ) )
```

Oh, that's elegant!

---

