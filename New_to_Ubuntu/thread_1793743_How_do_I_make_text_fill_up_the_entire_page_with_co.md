---
title: "How do I make text fill up the entire page with copy and paste?"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-06-30
I'm trying to copy and paste the entire text to OfficeOpen Writer from this page:

[http://www.gutenberg.org/cache/epub/7849/pg7849.txt](http://www.gutenberg.org/cache/epub/7849/pg7849.txt)

There's a lot of white space wasted on the right side of the page. How  do I change this so that all that text is moved to fill the entire page?

---

### Post by saphil on 2011-06-30
The original text is full of hard returns [enter] key on the keyboard.
To see this, click the hidden character icon on the openoffice icon strip. It is a backward capital P.  The original text is formatted to the line length in the book they scanned.

---

### Post by brawnypandora0 on 2011-06-30
> **saphil said:**
> The original text is full of hard returns [enter] key on the keyboard.
To see this, click the hidden character icon on the openoffice icon strip. It is a backward capital P.  The original text is formatted to the line length in the book they scanned.

So there's no way to realign it to fill the whole page?

---

### Post by saphil on 2011-06-30
Backspace from the becoming of line 2. Add a space so the words aren't crammed together. Go to the beginning of the next line-  repeat. It is time-consuming, but if the ' non-printing characters are turned visible, it isn't hard.

---

### Post by brawnypandora0 on 2011-06-30
> **saphil said:**
> Backspace from the becoming of line 2. Add a space so the words aren't crammed together. Go to the beginning of the next line-  repeat. It is time-consuming, but if the ' non-printing characters are turned visible, it isn't hard.

Yikes, there are thousands of lines.

What does "non-printing characters are turned visible" mean?

---

### Post by Bachstelze on 2011-06-30
You can use tr to replace all newlines by spaces:

```
cat foo.txt | tr "\n" " " > foo2.txt
```

---

### Post by Bachstelze on 2011-06-30
Though of course even better would be to use LaTeX instead of the clunky OpenOffice, then the problem would not appear. ;)

---

### Post by frisket on 2011-07-02
> **Bachstelze said:**
> Though of course even better would be to use LaTeX instead of the clunky OpenOffice, then the problem would not appear. ;)
I agree...if you want to manipulate text, learn to use the proper tools and don't try to rely on broken visual paradigms like wordprocessors.

---

### Post by brawnypandora0 on 2011-07-02
> **Bachstelze said:**
> You can use tr to replace all newlines by spaces:

```
cat foo.txt | tr "\n" " " > foo2.txt
```

I'm supposed to type that into the terminal? I get this:

cat: foo.txt: No such file or directory

Why can't word processors allow you to do such a simple task?

---

### Post by nzjethro on 2011-07-02
> **brawnypandora0 said:**
> I'm supposed to type that into the terminal? I get this:

cat: foo.txt: No such file or directory

Why can't word processors allow you to do such a simple task?

"foo.txt" is used as a placeholder to indicate where you should put your own file name (check out [this]("http://en.wikipedia.org/wiki/Foo")).

Copy the text to a text file (e.g. using gedit or mousepad), and save it as <your-filename-here>.txt (e.g. gutenberg.txt). Then, run the command again, substituting "foo.txt" with the path and name of your file (e.g. "~/Documents/gutenberg.txt").

---

### Post by Hagar Delest on 2011-07-03
See also that macro for OOo: [Convert ASCII text files by deleting extra paragraph breaks](http://user.services.openoffice.org/en/forum/viewtopic.php?f=21&t=37181).

And (if necessary): [[Tutorial] How to install a code snippet](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=5519).

---

