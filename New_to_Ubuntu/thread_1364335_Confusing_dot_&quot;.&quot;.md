---
title: "Confusing dot &quot;.&quot;"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by Albert Net on 2009-12-25
It seems that "." is also a special character in terminal.

Does anyone tell me some information about it?

---

### Post by Mrandersonjr on 2009-12-25
Pretty sure it is the same as *.* meaning everything in a directory.

---

### Post by paul_in_london on 2009-12-25
. is a metacharacter that has special meaning to the Linux shell (the shell is something like COMMAND.COM, the command processor under DOS).

**You cannot have a file called . or a file called .. (dot or two dots) - they mean "current" and "parent of the current" directory respectively, exactly like in DOS.**

Here are some of the other metacharacters:
 
*** = Matches any sequence of zero or more characters, except for "." (a dot) at the beginning of a filename. **
? = Matches any single character. 
[abC1] = Matches a single character in the enumerated set. In this example the set contains: 'a', 'b', 'C', and '1'. 
[a-z] = Matches any lower-case letter. 
[A-F] = Matches any upper-case letter from A to F. 
[0-9] = Matches any single digit. 
[a-zA-Z0-9] = Matches any letter (lower or upper case) or any digit.

The character \ (backslash) is also special. It makes the subsequent special character aquire literal meaning.

Examples. This command will list any filename in the current directory, with the exception of filenames starting with "." (dot): 

ls * 

An equivalent to this command is to type just ls or dir (without the "*"). **Files with names starting with "." are not shown because "." as the first character of a filename is not matched by "*". Think of files with names starting with "." as an equivalent of DOS hidden files. Use ls -a (list with the option "all") or ls .* to see these "dot" files. The "dot-files" are common in the user home directories and they typically contain user-level configurations. **

This command will list any file (in the current directory) that contains a dot (except files starting with a dot):

ls *.* 

This command will list any filename that contains two dots (except those starting with a dot):

ls *.*.* 

Note that Linux does not have "filename extensions" the way DOS does, but you can still use them. For example, I can have a file my_text.txt.zip. Some other DOS-kind file-naming features are completely absent ("Micros~1.doc" comes to mind). 

This command will find (on the whole filesystem) any file with the extension "htm" optionally followed by any one more character:

locate *.htm?

This command will show all filenames in the current directory that start with "a" or "b", or any capital letter:

ls [abA-Z]* 

This command will list any file starting with "a" and ending with "n"

ls a*n

---

### Post by laceration on 2009-12-26
Wow, Paul in London, you gave him a whole tutorial in Regular Expressions, but I don't think you answered his question.  Are you trying to drive him nuts? Regular Expressions are a bitch, you should only take them on if you have to;).

Regular Expressions can be used in the terminal and a "." would mean any single character.
The dot also means the current working directory, as in
cd ./somesubdirectory
2 dots means the parent directory, for instance
ls ../someotherdirectory

In bash "." is also synonymous with "source"
. somefile
or 
source somefile
includes somefile, meaning that scripts, functions, variables within  the file are available to be used.

---

### Post by bodhi.zazen on 2009-12-26
In a terminal , . is short hand for "source"

[http://ss64.com/bash/source.html](http://ss64.com/bash/source.html)

---

### Post by Albert Net on 2009-12-26
I got it.

It seems that instead using ./filename to execute the script, I also can use the . filename(. filename).

This is powerful, for I don't even set it executable. 

Thank you all, especially "bodhi.zazen".

Solved.

---

### Post by audiomick on 2009-12-26
my thanks too.:popcorn:

---

### Post by The Cog on 2009-12-26
It's not so much that dot is a magic character to the shell (command interpreter), it is that dot tends to have special meaning to lots of different programs, in lots of different contexts.

As Bodhi pointed out, in ". filename", the dot is a command to "source" the named file, treating it as keyboard input.

The interpreter also treats dot as meaning "the current directory" as in "./filename". Similarly, programs such as ls treats dot as "the current directory" as in "ls .", but I think this is actually a second program (ls) interpreting the dot in this case.

Programs that use regular expressions have a special meaning for dot when doing pattern matching, where is means "any one character".

They are all the special cases I can think of offhand, but I'm sure there must be others.

---

### Post by paul_in_london on 2009-12-26
Yes, thanks guys. I'd forgotten about the use of . as equivalent to the source command...

---

### Post by Albert Net on 2009-12-26
Reply to "The Cog", 

I think you made a mistake. 

"." indeed has special meaning in terminal, which is "source". 

What you  are saying is "?", match any single character.


In fact, this question derives from the following command:

ls | sed -n 's/.//p'

Since "." is a special character or operator, I need to put "\" before it, if I want to use it.

Actually, the above gives me some interesting result. All the files in the current directory lose the first character of their names.

I can't understand it. Maybe someone can explain it.

---

### Post by bodhi.zazen on 2009-12-26
> **Albert Net said:**
> I can't understand it. Maybe someone can explain it.

The use and syntax of "." is variable. . as a command, . in the path, . as in hidden files, and . as in regular expressions.

and is influenced by quotes ( " != ') as well as brackets [] and can be escaped \. 

I advise you see the man pages as needed.

> Matches any single character (many applications exclude [newlines]("http://en.wikipedia.org/wiki/Newline"), and exactly which characters are considered newlines is flavor, character encoding, and platform specific, but it is safe to assume that the line feed character is included). Within POSIX bracket expressions, the dot character matches a literal dot. For example, a.c matches "*abc*", etc., but [a.c] matches only "*a*", "*.*", or "*c*".

---

### Post by sisco311 on 2009-12-26
> **Albert Net said:**
> Reply to "The Cog", 

I think you made a mistake. 

"." indeed has special meaning in terminal, which is "source". 

What you  are saying is "?", match any single character.


. or source is the name of the bash buildin command.
```
man bash | less +/"\.  filename \[arguments\]"
```

?, **in a pattern**,  matches any single character.
```
man bash | less +2/"Pattern Matching"
```

 
> **Albert Net said:**
> 
In fact, this question derives from the following command:

ls | sed -n 's/.//p'

Since "." is a special character or operator, I need to put "\" before it, if I want to use it.

Actually, the above gives me some interesting result. All the files in the current directory lose the first character of their names.

I can't understand it. Maybe someone can explain it.

In a regular expression, in sed, . matches zero or more characters. 

's/.//' = replace the first character with *nothing*.

---

### Post by bodhi.zazen on 2009-12-26
thank you [sisco311]("http://ubuntuforums.org/member.php?u=244665")

---

### Post by Albert Net on 2009-12-26
> . or source is the name of the bash buildin command.
 	Code:
 	man bash | less +/"\.  filename \[arguments\]" 
?, **in a pattern**,  matches any single character.
 	Code:
 	man bash | less +2/"Pattern Matching" 
 

Powful command.

After reading them, I found there is a slight difference between "?" and ".".

For example, "riddle..oc" will match "riddle.doc" "riddle[doc" and "riddle..oc", while it give me some weird output"grep: Unmatched [ or [^", when I use "riddle??oc".

> In a regular expression, in sed, . matches zero or more characters. 

In regular expression, "." match any single character, not zero or more characters.

---

### Post by sisco311 on 2009-12-26
> **Albert Net said:**
> 

In regular expression, "." match any single character, not zero or more characters.

D'oh, of course, you're right... or almost right. :evil:

The meaning of a special character depends on the command interpreter (bash, awk, less, sed...).

i.e. in a basic regular expression, ? is not special character,
while in an extended regular expression, ? indicates there is zero or one of the preceding element. :
```

sisco@acme:~$ echo "color" | grep -G ^colou?r
sisco@acme:~$ echo "colour" | grep -G ^colou?r


sisco@acme:~$ echo "colour" | grep -E ^colou?r
colour
sisco@acme:~$ echo "color" | grep -E ^colou?r
color

```
NOTE: the ?, in the above commands, is interpreted by grep and not by bash.

example2:

man sed:
```
REGULAR EXPRESSIONS
       POSIX.2 BREs _[U]should_[/U] be supported, but they **aren't** completely because of
       performance problems.  The \n sequence in a regular expression  matches
       the newline character, and similarly for \a, \t, and other sequences.
```

---

### Post by Albert Net on 2009-12-26
You have got to get me out of here. 

When I tried your examples, something unbelievable happened.

```

echo colour | grep c?lour   --------no output
echo colour | grep -E c?lour    colour  ------so far so good
echo colour | grep -E col?ur   -------no output

```

How is this happening?

Besides,
```
man grep | less +2/"GNU grep"
```

"In GNU grep, there is no difference in available functionality using either syntax."

A bug?

---

### Post by Christmas on 2009-12-26
Except for source (which is a Bash builtin, equivalent to source), . also means the current directory. For example:
```
ls .
```
Will list the contents of the current directory (same as ls without parameters. Or:
```
cp /var/log/somefile .
```
Will copy /var/log/somefile to the current directory.
```
$ file .
.: directory
```

---

### Post by paul_in_london on 2009-12-26
> echo colour | grep -E c?lour    colour  ------so far so good
echo colour | grep -E col?ur   -------no output

? matches either 0 or 1 occurrence of the preceding character.

In your first example, grep is trying to match **lour** or **clour** and matches **lour**.

In your second example, grep is trying to match **cour** or **colur** and matches neither.

---

### Post by sisco311 on 2009-12-26
> **Albert Net said:**
> You have got to get me out of here. 

When I tried your examples, something unbelievable happened.

```

echo colour | grep c?lour   --------no output
echo colour | grep -E c?lour    colour  ------so far so good
echo colour | grep -E col?ur   -------no output

```

How is this happening?


```
echo colour | grep c?lour
```
is the equivalent of:
```
echo colour | grep -E "c\?lour"
```

```
echo colour | grep -E c?lour
```
-->
```
echo colour | grep -e lour -e clour
``` 

and

```
echo colour | grep -E col?ur
```
-->
```
echo colour | grep -e cour -e colur
```

> **Albert Net said:**
> 
Besides,
```
man grep | less +2/"GNU grep"
```

"In GNU grep, there is no difference in available functionality using either syntax."

A bug?

Nope, in basic regular expressions you have to use the backslashed versions of ?, +, { ...

```
echo colour | grep "c\?lour"
```
```
man grep | less +/"Basic vs Extended Regular Expressions"
```


Different syntax, but same functionality.

> **Christmas said:**
> Except for source (which is a Bash builtin, equivalent to source), . also means the current directory. For example:
```
ls .
```
Will list the contents of the current directory (same as ls without parameters. Or:
```
cp /var/log/somefile .
```
Will copy /var/log/somefile to the current directory.
```
$ file .
.: directory
```

The name of a file is a hard link. A given file can have more than one hard link to itself. For example, a directory has at least two hard links: the directory name (dirname) and . (dirname/.).

. is hard link to the current directory and
.. is a hard link to the parent directory.

They are filenames = hard links. 

(yes, directories are files too :)).

So, the period in *ls .* has no special meaning because . is a valid directory name.

---

### Post by Albert Net on 2009-12-27
Why is
echo colour | grep -E c?lourequivalent to

```
echo colour | grep -e clour -e lour
```I  have to admit you are right, but it is  quite confusing, for "?" just matches any single character. In this case, apparently, "?" can even delete the letter before it.


sisco311 is right that is not a bug. I misunderstood it. They achieve the same function with different syntax.

```
echo colour |  grep c\?lour
echo colour | grep "c\?lour"
```Why is quotation marker essential here?

---

### Post by Albert Net on 2010-01-05
Finally, question solved.


The dot special character is used to match any single character except a new line character.

Since this thread is derived from Regular Expression, I should close it with a clear summary.

ASTERISK
Placing an asterisk after a character signifies that the character must appear zero or more times in text to match the pattern.

QUESTION MARK
The question mark indicates the preceding character can appear zero or one time, but that is all.

---

