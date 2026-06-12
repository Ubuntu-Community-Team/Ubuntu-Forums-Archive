---
title: "help with a script"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-05-15
Hi everyone.
I have a script and I need it to search something in a file, and then replace the line it is located with other text I need.
Can anybody say me how to do this? for example with grep or sed or awk?

---

### Post by yeats on 2011-05-15
> Quoting from [here]("http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1305462931071+28353475&threadId=219828")

"Say the string you are looking for is STRING_TO_BE_REPLACED.
And the line you want to insert is LINE_TO_REPLACE_WITH.
The input file is 'file', the output file is 'new_file':

cat file | sed 's/^.*STRING_TO_BE_REPLACED.*$/LINE_TO_REPLACE_WITH/' >new_file

The ^ is a start of line anchor, the '.*' is a wildcard, the $ is a end of line anchor."

Hope that helps!

---

### Post by Avidanborisov on 2011-05-15
> **yeats said:**
> Hope that helps!

Are the dots also count as text?

---

### Post by jakupl on 2011-05-15
I'm no sed expert, but the forwardslashes are the seperators, so I believe that the punctuations are included. Everything between the forwardslashes will be replaced...

---

### Post by yeats on 2011-05-15
> Are the dots also count as text? 

Yes - it breaks down this way:

'sed' - calls the sed program

'' - you always wrap the sed command in single quotes to keep the bash shell from trying to evaluate it

's///' - sed substitution (s) requires two arguments, usually delineated by forward slashes (but you can use other characters too).  The first argument '^.*STRING_TO_BE_REPLACED.*$' is what you're telling sed to look for and the second argument 'LINE_TO_REPLACE_WITH' is what you're telling sed to replace it with

'^' - beginning of line

'.' - any single character

'*' - the previous character can be repeated any number of times (including zero times)

(when combined, '.*' means 'any bit of text, even if there is no text')

'$' - end of line

I'm hoping the rest is obvious.  If you're going to be doing a lot of this kind of thing, you might want to look into a book or other resource about regular expressions.

Good luck!

---

### Post by Avidanborisov on 2011-05-15
> **yeats said:**
> Yes - it breaks down this way:

'sed' - calls the sed program

'' - you always wrap the sed command in single quotes to keep the bash shell from trying to evaluate it

's///' - sed substitution (s) requires two arguments, usually delineated by forward slashes (but you can use other characters too).  The first argument '^.*STRING_TO_BE_REPLACED.*$' is what you're telling sed to look for and the second argument 'LINE_TO_REPLACE_WITH' is what you're telling sed to replace it with

'^' - beginning of line

'.' - any single character

'*' - the previous character can be repeated any number of times (including zero times)

(when combined, '.*' means 'any bit of text, even if there is no text')

'$' - end of line

I'm hoping the rest is obvious.  If you're going to be doing a lot of this kind of thing, you might want to look into a book or other resource about regular expressions.

Good luck!

so if I have this text:

```

red red red
orange orange orange
brown crown

```

and I want to search for:

```
brown crown
```

and replace the whole line with:

```
yellow yellow
```

I will write this command?

```
cat file | sed 's/^.*brown crown*$/yellow yellow/' >file

```

---

### Post by yeats on 2011-05-15
Why don't you try and see? ;-)

---

