---
title: "Nautilus search for file contents"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by lemmyc on 2009-07-23
This seems pretty basic. If I'm in a folder in Nautilus and I do a search, it only returns items with the search term in the title. I want Nautilus to look at the file contents too. Any ideas?
Thanks.

---

### Post by drs305 on 2009-07-23
For a GUI solution, you can use Places, Search, Select More Options, 'Contains the text' option. It may not be exactly what you are looking for but it does provide a way to search for text without using CLI.

---

### Post by lemmyc on 2009-07-23
Thanks for that.
It would be useful if this could be baked into Nautilus... Seems pretty fundamental for a file browser.

---

### Post by starcannon on 2009-07-23
if your not adverse to the command line, this is how I do it:

First install the Nautilus Open Terminal Here plugin:
```

sudo apt-get install nautilus-open-terminal

```
Log out, and back in to make changes take effect.

Second, using Nautilus to browse to the folder you want to search, Right Click inside the folder and then left click on "Open Terminal"

Third:
```

find . -name filename.extension

```
You can use wild cards as well; for instance, if you wanted to find all the jpg extensioned files in a folder:
```

find . -name *.jpg

```

Or if you wanted to find all files with the letter sequence of "freedom" in them:
```

find . -name *freedom*

```

Or if you wanted to find all jpg's with the letter sequence of "freedom" in them:
```

find . -name *freedom*.jpg

```
mix and match as needed and so on.

I'm sure that Nautilus has great search abilities built in, I just find have a personal preference to use the terminal for this particular job; I use what works for me.

I hope you find a solution that will work fine for you.

GL and HF

P.S. 
A great hint would be:
```

man find

```

---

### Post by heyyy on 2009-07-23
you can try beagle

---

### Post by Johnny B on 2009-07-23
you can use nautilus scrips to add any functionality you want to nautilus
search google for a nautilus script that searches file contents
put the script in $HOME/.gnome2/nautilus-scripts and make it executable

---

### Post by lemmyc on 2009-07-23
Thanks for the hints. I might take a look at Beagle.
I knew there were CL options, but I prefer a graphical interface for some operations. I'm also thinking about new linux users coming to Ubuntu and the features they might expect.

---

### Post by lemmyc on 2009-07-23
Thanks JohnnyB, I'll try that.

---

### Post by lemmyc on 2009-07-23
One solution here:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=25114](http://forums.linuxmint.com/viewtopic.php?f=42&t=25114)

---

### Post by airtonix on 2009-12-14
Problem with all these ideas is that it means you can;t make use of the saved searchs as virtual folders anymore.

Or maybe there is a way to modify the saved.search xml file (that is translated as a folder by nautilus) to run these terminal commands (and thus return a list of URIs that result from them.

---

### Post by johntkucz on 2011-06-02
> **starcannon said:**
> if your not adverse to the command line, this is how I do it:

First install the Nautilus Open Terminal Here plugin:
```

sudo apt-get install nautilus-open-terminal

```
Log out, and back in to make changes take effect.

Second, using Nautilus to browse to the folder you want to search, Right Click inside the folder and then left click on "Open Terminal"

Third:
```

find . -name filename.extension

```
You can use wild cards as well; for instance, if you wanted to find all the jpg extensioned files in a folder:
```

find . -name *.jpg

```

Or if you wanted to find all files with the letter sequence of "freedom" in them:
```

find . -name *freedom*

```

Or if you wanted to find all jpg's with the letter sequence of "freedom" in them:
```

find . -name *freedom*.jpg

```
mix and match as needed and so on.

I'm sure that Nautilus has great search abilities built in, I just find have a personal preference to use the terminal for this particular job; I use what works for me.

I hope you find a solution that will work fine for you.

GL and HF

P.S. 
A great hint would be:
```

man find

```


Wow this is excellent!  I did man find but didn't comprehend a lot of the arguments.  Anyone know of a good intro to using console to search for files with boolean operators 

like return results without "x_string"
and wildcards and whatnot?  

I love using console. it's so much faster, and more precise than gui!

---

### Post by johntkucz on 2011-06-02
[http://geekwentfreak.wordpress.com/2009/11/30/find-files-using-terminal-find-and-grep/#comment-427](http://geekwentfreak.wordpress.com/2009/11/30/find-files-using-terminal-find-and-grep/#comment-427)

Definitely did the trick.

---

### Post by johntkucz on 2011-06-02
hhmm I don&#8217;t understand:
&#8220;. This is non recursive. We have to use quotes to make sure that the shell does not expand the pattern, otherwise this would be like:&#8221;

what is the difference from searching for &#8216;*.html&#8217; and *.html ???

How do you use boolan searches like

find -name *thisword* ! -name *thatword*.  That didnt' work.

okay that kind of worked.  How can I use boolean AND NOT (!) OR in nautilus?

---

### Post by emartinhowell on 2012-03-15
Use space instead of asterisk as wild card for single or multiple characters. Wildcards are assumed before and after search string. For example searching for il will find Illinois, William, and Bill where the string is found at the beginning, middle, and end of results. The 'standard' wildcard for a single character, ? or question mark, does not seem to work. I've not found an alternative for that yet. Also " or double quotation marks seem to be taken literally.

---

