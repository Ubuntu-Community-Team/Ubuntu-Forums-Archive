---
title: "Question about using sed to extract content between two strings"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by amylase on 2010-11-18
I have an index.txt file and in there amongst other code contains this line:
<h1>This is the answer</h1>

I would like to use sed to extract the string between <h1> and </h1> ie. the output I want is: **This is the answer**.

The first expression I tried immediately was this:
```
sed -n '/<h1>/ s/<\/h1>//p' index.txt

```
The output I got was this:
**<h1>This is the answer**

[COLOR="Magenta"]Why is my expression listed above inadequate? Why does it print the <h1> as well?
[/COLOR]
I then did a bit of searching online. Have to say it was not easy finding an answer. Lots of suggestions about using perl or awk or other more complicated ways. Anyway I finally found someone who used this sed expression to do the job:
```
sed 's/<h1>\(.*\)<\/h1>/\1/g' index.txt
```

The output was correctly: **This is the answer**.

[COLOR="Magenta"]What does the s mean? what does (.*\) mean? what does the \1 mean? and what does the /g mean please?
[/COLOR]
Thanks a lot.

---

### Post by fly-by-night on 2010-11-18
If no-one can help here, you could ask a mod to move it.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)
Programming Talk

The home of /regular expressions\.

---

### Post by DaithiF on 2010-11-18
> **amylase said:**
> 
[COLOR=Magenta]What does the s mean? what does (.*\) mean? what does the \1 mean? and what does the /g mean please?
[/COLOR]
Thanks a lot.
s = substitute command, s/a/b/ replaces a with b
\(.*\) ... .* means one or more occurrence of any character.  surrounding this with \( \) 'captures' it ... ie. remembers it for later in the command...
\1 is a reference to the first 'captured' expression
g means that the substitute command acts globally, which means that if you had more than one occurrence of the <h1>something</h1> pattern on a line that the substitution would be performed on each occurrence.

there are any number of quick sed tutorials available online that will explain these and more.

---

### Post by amylase on 2010-11-21
> **DaithiF said:**
> s = substitute command, s/a/b/ replaces a with b
\(.*\) ... .* means one or more occurrence of any character.  surrounding this with \( \) 'captures' it ... ie. remembers it for later in the command...
\1 is a reference to the first 'captured' expression
g means that the substitute command acts globally, which means that if you had more than one occurrence of the <h1>something</h1> pattern on a line that the substitution would be performed on each occurrence.

there are any number of quick sed tutorials available online that will explain these and more.

Thanks! :KS

---

