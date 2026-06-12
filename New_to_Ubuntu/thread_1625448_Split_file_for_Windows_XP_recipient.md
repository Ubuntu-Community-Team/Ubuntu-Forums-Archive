---
title: "Split file for Windows XP recipient"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-11-19
I have a large PDF file that I need to send to someone.

Unfortunately, it's over 100Mb, but his company computer won't allow downloading files greater than 100Mb. The file is too big for ZIP to compress it to under 100Mb.

He runs **Windows XP**.

Is there a program that I can use to split a file (using a ZIP would be fine) such that he can reconstruct it on Windows XP? I would have used 7z, but the recipient doesn't have the option to download that program onto his company computer.

Any ideas?

---

### Post by coffeecat on 2010-11-19
You will want to do a test run with this, or experiment, because I ended up with a larger (39MB) pdf file than I started. Fwiw this is what I did with a 26MB file.

In Ubuntu:

```
split --bytes 13M test.pdf
```... which output three files, xaa, xab and xac, 26MB, 13MB and 17.5KB in length. As you can see the first chunk is the same size as what I started with - I don't know why - but was not a valid pdf.

Then in the command line in Vista (it should work the same in XP):

```
type xaa,xab,xac > test2.pdf
```Although test2.pdf was 50% larger than test.pdf it seemed to be functionally the same in Adobe reader in both Vista and Ubuntu and in Document Viewer in Ubuntu.

**Edit:** Interestingly, doing:

```
 cat xaa xab xac > test3.pdf
```... in Ubuntu stitches everything back together again into the original size of 26MB.

---

### Post by Paddy Landau on 2010-11-19
Thanks for that idea.

I used split, and it successfully split the file into two chunks with sensible sizes. I didn't get that odd problem you got with the first chunk being too large.

I found out that the Windows command to use is as follows (using your example):
```
copy /b za* test2.pdf
```I shall send the files to my recipient and cross fingers that it works!

EDIT: I wonder if there's a GUI way on Windows to stitch them together?

---

### Post by coffeecat on 2010-11-19
> **Paddy Landau said:**
> I didn't get that odd problem you got with the first chunk being too large.

Perhaps my pdf file was an odd one. It was the largest I could lay my hands on quickly. I shall investigate.

> **Paddy Landau said:**
>  I found out that the Windows command to use is as follows (using your example):
```
copy /b za* test2.pdf
```I shall send the files to my recipient and cross fingers that it works!

That's interesting. I couldn't get the copy command to work properly, but I was using a syntax similar to what I posted for type. Your one for copy works nicely.

---

### Post by Paddy Landau on 2010-11-19
> **coffeecat said:**
> I couldn't get the copy command to work properly, but I was using a syntax similar to what I posted for type.
Windows's *type* command converts to ASCII as it is intended for human display.

The screen output of the *copy* command is not the input, but messages to the screen. That's why it wouldn't work.

I'm still awaiting feedback on whether this worked for my recipient.

And I've just thought to ask whether he has Skype; if so, I can transfer it with that!

---

### Post by Paddy Landau on 2010-11-19
I have found a free GUI program that splits the file and creates an executable "uniter", suitable for sending to people who struggle with command lines. It runs under Wine.

[GSplit by GDG Soft]("http://gdgsoft.com/gsplit/") needs a little understanding to split the files, but it's dead easy to reconstruct; the recipient doesn't need to install the program.

I shall mark this thread solved.

---

### Post by qamelian on 2010-11-19
There is also HJSplit which is cross-platform and has a variety of different versions for almost any need, including a java version.

---

### Post by Paddy Landau on 2010-11-19
> **qamelian said:**
> There is also HJSplit which is cross-platform and has a variety of different versions for almost any need, including a java version.
Nice, thanks. Unfortunately it doesn't create the self-extractor, which would save me from having to post complicated instructions in an email.

---

