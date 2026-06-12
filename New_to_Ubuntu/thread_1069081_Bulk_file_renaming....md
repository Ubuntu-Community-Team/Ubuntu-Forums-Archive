---
title: "Bulk file renaming..."
date: 2009-02-13
forum: New to Ubuntu
---

### Post by AndrewS on 2009-02-13
Hello

I have a lot of files that I want to rename, and I can't figure out how to do it with any of the simple tools available (Thunar, Krename, Metamorphose).

The files have a common format:

AA1234_xx_xx_x.jpg

The string before the first "_" is up to six characters long and there is a variable number of "_" before the period preceding the extension.

What I want is to get rid of everything from the first "_" to the period, i.e. the above file name would become:

AA1234.jpg

Thanks in advance

Andrew

---

### Post by kanikilu on 2009-02-13
I'm by no means a regex expert, but I think this would work:

```
$ rename -v 's/(\w{6})[\w]+\.jpg$/$1\.jpg/' *
```

Note, this assumes several things:

1) You are in the directory that has the files that need to be renamed
2) The files you want to rename have *exactly* 6 characters that you want to keep in the final name.
3) The files all end in ".jpg" (not ".JPG" or anything else)

Lastly, you may substitute the "-n" option instead of "-v" to test it first. Once you know that it will work, then go back and run it with "-v".

---

### Post by AndrewS on 2009-02-13
Thanks for the reply - I'm sure that would work for files with six characters I want to keep, but the number is variable (3, 4, 5, or 6).  I guess I could sort them manually then try that sort of thing.

Thanks again

Andrew

---

### Post by apostate on 2009-02-13
Naw, you can use a FOR loop to go through and mass rename them. I wrote a script to do it on videos, but I lost it. Let me decompress fromthe IT world for a few and I will try to write you a script that will do it.

---

### Post by kaibob on 2009-02-13
I suspect there's an easier way, but the following works regardless of the number of characters before the underscore. 

```
#!/bin/bash
cd /directory/name
for FILE in *_*.jpg ; do
FILENAME="$(echo "$FILE" | cut -d _ -f1).jpg"
cp "$FILE" "$FILENAME"
done
```

---

### Post by AndrewS on 2009-02-13
kaibob

That's brilliant, worked a treat (although it left me with the original file as well as the renamed one, but that's being really picky!).

The only question is, what did I actually do??? (I'm totally new to that sort of command-line work).  If you have time, can you describe what happened?

Thanks again

Andrew

---

### Post by kaibob on 2009-02-13
To actually rename the files, you can use the move command (mv) in the script rather than the copy command (cp). I used the latter to be safe until the script has been run a few times. Another alternative is to use the copy command and to direct the renamed files to a different directory. 

The script uses a for loop to process the files and the cut command-line utility to extract the desired string from the existing file name. 

The following contains a good discussion of for loops:

[http://linuxcommand.org/wss0140.php](http://linuxcommand.org/wss0140.php)

And, the following is a decent explanation of the cut utility: 

[http://lowfatlinux.com/linux-columns-cut.html](http://lowfatlinux.com/linux-columns-cut.html)

In this instance, the cut command extracts the first field (-f 1) from the file name with each field being defined by the underscore (-d _). The file names are piped to the cut command by the echo command and the output is assigned to the variable, FILENAME, by command substitution.

I'm new to shell scripting and my explanation is probably lacking, but the above links should help to explain things.

---

### Post by geirha on 2009-02-13
I would've used rename with this regular expression, which says, remove all characters from the first '_' that is not a '.'.
```
rename -n 's/_[^.]*//' *.jpg
```

Note the -n means dry-run. It will just display what it intends to do, but not actually do it.

---

### Post by newbee70 on 2009-02-13
> **AndrewS said:**
> Hello

I have a lot of files that I want to rename, and I can't figure out how to do it with any of the simple tools available (Thunar, Krename, Metamorphose).

The files have a common format:

AA1234_xx_xx_x.jpg

The string before the first "_" is up to six characters long and there is a variable number of "_" before the period preceding the extension.

What I want is to get rid of everything from the first "_" to the period, i.e. the above file name would become:

AA1234.jpg

Thanks in advance

Andrew

You could try Purr! it is available in the repositories.

you can control it with a name and a unique numerical identifier.

---

### Post by kaibob on 2009-02-13
> **geirha said:**
> I would've used rename with this regular expression, which says, remove all characters from the first '_' that is not a '.'.
```
rename -n 's/_[^.]*//' *.jpg
```...
Geirha. I knew there had to be an easier way--your solution is much better. Thanks!

---

### Post by AndrewS on 2009-02-14
Thanks all, I've got some reading to do!

Andrew

---

### Post by abhigyan91 on 2009-06-25
> **AndrewS said:**
> kaibob

That's brilliant, worked a treat (although it left me with the original file as well as the renamed one, but that's being really picky!).


Andrew

if you dont want the original files then u can change "cp" in the secondlast line to "mv"

```

#!/bin/bash
cd /directory/name
for FILE in *_*.jpg ; do
FILENAME="$(echo "$FILE" | cut -d _ -f1).jpg"
**mv** "$FILE" "$FILENAME"
done


```

---

### Post by stewiefet on 2009-07-10
So how would you change that bash script to move the fields in the filename around instead of just cutting them?
 
I have a bunch of txt files in the general format
 
Firstname Maybe Middlename Lastname - other info - possible other info.txt
 
I'd like to move the lastname to the front of the filename.. but I'm not clear on how cut and paste work together in the command line.
 
 
Stew

---

### Post by Mornedhel on 2009-07-10
Just to make sure, your filenames look like this :

<single word> <possibly single word> <single word> - <maybe something> - <maybe something> - info.txt ?

If the first, middle and last names are always single words, then you could do

```
rename -n 's/^(\w+) (\w+)? (\w+)/$3 $2 $1/' *.txt
```

Check that everything seems fine, then run the command again without the -n so it actually renames the files. I have tested it on a file called "foo bar tiger.txt", but you never know. I'm particularly concerned about accents.

Tweak "*.txt" if all the .txt files in the directory are not to be renamed, possibly replacing it with "*info.txt".

If the names aren't always single words, you're in trouble unless you have a dictionary of common names for your language somewhere.

---

### Post by geirha on 2009-07-10
Since we don't know how many names there will be before the last name, the first ' - ' would be the logical anchor point to build the regex around. So first off, lets match everything we don't care about. ' - .*' should take care of that, since * is gready and will match as much as possible, so ```
rename -n 's/ - .*//' *.txt
``` should show that the first - and everything behind it will be removed.

Now let's match the last word before the -. The special character class \s will match whitespace, while \S will match the complement (everything but whitespace), so '\S+ - .*'. We want to remember that word, so put it in parenthesis. '(\S+) - .*'

Lastly, we need to match the one or more names from the start of the line (^) up to  the last name, but .* just won't do it, because * is greedy, and the first greedy match will take precedence over the ending .*, so we have to make sure that we don't go past the first - . [^-] means any character except -, so if we match the largest sequence of [^-], that should hopefully cover it. '^([^-]*) (\S+) - (.*)'. Now we have three groups we can move around.
```
$ rename -n 's/^([^-]*) (\S+) - (.*)/$2, $1 - $3/' *.txt
Firstname Maybe Middlename Lastname - other info - possible other info.txt renamed as Lastname, Firstname Maybe Middlename - other info - possible other info.txt

```

If any of the first names has a dash (-) in them, though, the [^-]* would stop at that position, making the regex possibly not match at all. Let me know if that is the case and we can change it further. (Or if it's just one or two files, you could just rename them manually)

---

### Post by stewiefet on 2009-07-10
geirha, this one got it.  Very nice and neat.   There are a handful of hyphenated names but only a handful so easy enough to deal with those manually.   Thanks!
 
 
```
$ rename -n 's/^([^-]*) (\S+) - (.*)/$2, $1 - $3/' *.txt
Firstname Maybe Middlename Lastname - other info - possible other info.txt renamed as Lastname, Firstname Maybe Middlename - other info - possible other info.txt

```

---

