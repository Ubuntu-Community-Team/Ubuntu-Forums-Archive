---
title: "GNU Talk Filters"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Sig Nuka on 2009-03-02
[http://www.hyperrealm.com/main.php?s=talkfilters](http://www.hyperrealm.com/main.php?s=talkfilters)

So, uh, how do I actually use it? I have the compiled .deb installed (through checkinstall, or at least that's what it says when I double-click on the .deb), but I have no idea on how to actually USE it.

I'm pretty sure I'm missing something obvious here. ](*,)

Edit: Well, I can't change the thread title apparently. Oh well. ^^;

---

### Post by blueridgedog on 2009-03-02
From the manual:

```
An example usage might be:
  man ls | jive | wrap -w 78 | less
```

So, you get some input, say a document you wrote called mydocument.txt, then you get it to the filter you want, say austro then wrap the output with the following:

```
cat mydocument.txt | austro | wrap -w 78
```

Or, you can just dump text to it:

```
james@Ripstop:~/extract/talkfilters-2.3.8$ echo "now is the time for all good men to come to the aid of their country" | austro 
nov is ze tim for al good men to kom to ze aid of zeir kuntry
```

---

### Post by Sig Nuka on 2009-03-02
Wait, so I have to use the terminal for all of this? Oy vey. >_<;

So where should I change the terminal directory to before I dump text? Or is that even necessary?

And what's the difference between using man ls and using cat? And what's with the "less" command?

Ugh, my head...

---

### Post by blueridgedog on 2009-03-03
> **Sig Nuka said:**
> Wait, so I have to use the terminal for all of this? Oy vey. >_<;

So where should I change the terminal directory to before I dump text? Or is that even necessary?

And what's the difference between using man ls and using cat? And what's with the "less" command?

Ugh, my head...

These tools or filters are designed to be used with a command line (85% of Linux/Unix if not more is).  Don't think of that as bad.  It is much easier than having only a mouse pointer.  Look down at your desk.  You have two input devices.  One has over 128 input options.  One has only three or so, but lets you point at things.  Which is more likely to be a powerful tool in your computing life?  Right, the keyboard.  

So open up a terminal with Applications -> Assessories -> Terminal.

If you have installed the filters, you can test them with:

```
echo "This is a test of the filter on this fine day" | chef
```

What you get back is:

```
Thees is a test ooff zee feelter oon thees feene-a dey
```

What you did was send a string of text with echo to the filter via what is called a pipe ...that is the "|" thing.  

Now, if you want to type in a document to filter the entire thing, then open gedit and type what you want.  Save your document in your home directory, naming it whatever you want.  For sake of an example, I will save mine as texttofilter.txt.

So, to filter that text, I go to the same terminal as before and need to read the contents of the file to the filter, that is where cat comes in.  cat is a command that simply prints the file or files in question to the display.  So, we can "cat texttofilter.txt" and have the text scroll by.  We can also send that text someplace using the pipe command mentioned above, so using true Linux command line flexibility we can cat the file, then pipe it to any of the filters with:

```
cat ~/texttofilter.txt | austro
```

The end result is that the filtered text displays on screen.  You can copy and paste it as needed (hey...the mouse!).  If you would rather send the output (the goofy text) to a file, you can extend the command a bit by using the great "goesinto" argument ">", which means "take whatever output the preceding code creates and that "goesinto" the following file.  

So the new syntax may look like:

```
cat ~/texttofilter.txt | austro > ~/anewfile.txt
```

Just for clarity, > is goesinto and creates a file and >> is goesinto and appends to a file, just in case you come across it.  Also ~/ is short hand for "your home directory".

As for your question about man versus cat, the example from the manual used "man ls" as a source of text.  It is simply the Linux command for "show me the manual for the ls command" and really is/was misleading.  

The filters are best used by "cat"ing an existing text file and piping it to a filter.  Try it, you will find that you may like the power of being able to do great things with a few keystrokes.

---

### Post by Sig Nuka on 2009-03-03
[QUOTE=Geico]"It's so easy a caveman could do it."[/QUOTE]
```
echo "It's so easy a caveman could do it." | pirate | valspeak
'Tis so easy a caveman could do it, like, wow arrrr.
```

Ooh, I'm gonna love this. :biggrin:

Many thanks for everything. I'll be sure to save this info for future reference. :D

---

