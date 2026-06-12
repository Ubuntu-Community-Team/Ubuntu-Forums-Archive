---
title: "Help with a command..."
date: 2009-11-21
forum: New to Ubuntu
---

### Post by gannon12raiders on 2009-11-21
I'm pretty sure I read somewhere that Ubuntu terminal has the ability to do a kind of "not equal to" thing...as in, if I have several files but only want to keep the .pdf, is there a way to basically "invert" the *rm *.pdf* command?

---

### Post by lloyd_b on 2009-11-21
> **gannon12raiders said:**
> I'm pretty sure I read somewhere that Ubuntu terminal has the ability to do a kind of "not equal to" thing...as in, if I have several files but only want to keep the .pdf, is there a way to basically "invert" the *rm *.pdf* command?

Try```
ls * | grep -v "\.pdf$" | xargs rm
```Here's a breakdown on what it's doing:
1.  **ls *** - get a list of the files in the current directory
2.  **grep -v "\.pdf$"** - filter out any that end in ".pdf"
3.  **xargs rm** - take the results from the grep, and build a "rm file1 file2 ..." command from them

The "|" is the "pipe" symbol, which takes the output from one command, and passes it to another command.

Lloyd B.

---

### Post by gannon12raiders on 2009-11-21
Hey, thanks a lot, that's exactly what I needed.

I'm wondering, though...when I look at that code, it all makes sense to me being an absolute beginner...except **grep "\.pdf$"** . I tried some messing around, and I guess I just don't understand why **grep "*.pdf" **doesn't do the same thing. Could you explain?

---

### Post by diesch on 2009-11-21
If you have extglob switched on in bash (shopt -s extglob) you can use
```
 rm *.!(pdf)
```

---

### Post by sisco311 on 2009-11-21
```
man bash | less --pattern\="QUOTING"
```
[http://en.wikipedia.org/wiki/Regular_expression]("http://en.wikipedia.org/wiki/Regular_expression")

In a regular expression a period (.) matches any single character.

A non-quoted backslash (\) is the escape character.  It preserves  the literal  value  of the next character that follows.

$ matches the ending position of the string.

---

### Post by lloyd_b on 2009-11-21
> **gannon12raiders said:**
> Hey, thanks a lot, that's exactly what I needed.

I'm wondering, though...when I look at that code, it all makes sense to me being an absolute beginner...except **grep "\.pdf$"** . I tried some messing around, and I guess I just don't understand why **grep "*.pdf" **doesn't do the same thing. Could you explain?

Sisco311 covered this already, but here's my version.

The first thing to remember is that 'grep' uses "regular expressions", NOT shell wildcards.  So "*.pdf" in 'grep' will not get you "all files that end in .pdf" the way "ls *.pdf" would.  In a regular expression, "." means "match any character", so it needs to be "escaped" with a backslash to look for the literal ".".

Another thing to remember is that 'grep' searches for the pattern anywhere in the string, unless you tell it otherwise.  So 'grep -v "pdf"' will match "thispdf.txt", as well as "thisfile.pdf".  The "$" characters matches "end of line".

So "\.pdf$" = "The literal character ." (/.), the string "pdf" (pdf), occurring at the end of the line ($).

Lloyd B.

---

### Post by emigrant on 2009-11-21
@[lloyd_b]("http://ubuntuforums.org/member.php?u=181262"), thank you for your explanation, was useful for me too.
and of course thank you all, i will look at the other options as well.

---

### Post by gannon12raiders on 2009-11-21
lloyd_b, thanks a lot. Your explanation was very clear. Just so we're clear - when you say "." means "match any character", you're saying that it is the equivalent of the ? wildcard?

---

