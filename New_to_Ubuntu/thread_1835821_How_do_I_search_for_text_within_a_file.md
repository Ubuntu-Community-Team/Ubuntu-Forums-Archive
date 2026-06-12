---
title: "How do I search for text within a file?"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by userub on 2011-08-30
Hello,

I've been trying to figure out how to search for text within a file. Grep was the only lead I could find, and I don't know how to get it to work. I've tried reading tutorials and other help guides, but they're full of Linux terminology that I just don't understand.

---

### Post by nothingspecial on 2011-08-30
If you are searching for a specific bit of text that you know eg "banana" in a file named file.txt

Then ```
grep "banana" file.txt
``` will print the line that contains that string (bit of text). If it's more complicated than that then either read up on regular expressions or give more details.

---

### Post by jasonrisenburg on 2011-08-30
this might help 

[http://www.howtogeek.com/howto/ubuntu/find-files-containing-search-terms-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/find-files-containing-search-terms-on-ubuntu/)

---

### Post by userub on 2011-08-30
I'm trying to search within files that are themselves within a folder.

---

### Post by Lampi on 2011-08-30
use recursive grep:
```
grep -r "banana" fishbones/
```

---

### Post by userub on 2011-08-30
> **Lampi said:**
> use recursive grep:
```
grep -r "banana" fishbones/
```

Is "fishbones/" the folder?

Should I use 'cd' beforehand to switch to "fishbones/"? Or the folder above it?

---

### Post by raja.genupula on 2011-08-30
> **userub said:**
> Is "fishbones/" the folder?

Should I use 'cd' beforehand to switch to "fishbones/"? Or the folder above it?

no need to go for using cd 
  follow as he said

---

### Post by userub on 2011-08-30
Okay, it worked.

I have a few more questions, though:

It wasn't working before because I spelled out the folder as "~/fishbones." Why wouldn't that have worked? What if I want to search in a file that's in a folder with a common name? How would grep know which folder to search in if I can't specify the folder location?

The output shows up in the terminal window. How do I arrange for the output to go out to a file?

Also, what are "regular expressions"?

---

### Post by Lampi on 2011-08-30
> **userub said:**
> It wasn't working before because I spelled out the folder as "~/fishbones." Why wouldn't that have worked?
because you quoted fishbones - get rid of the quotes and the dot at the end and it will work.

> **userub said:**
> 
What if I want to search in a file that's in a folder with a common name? How would grep know which folder to search in if I can't specify the folder location?
recursive means it will search all subdirectories that allow access.

> **userub said:**
> 
The output shows up in the terminal window. How do I arrange for the output to go out to a file?
2>&1 | tee filename
> **userub said:**
> 
Also, what are "regular expressions"?
[http://www.grymoire.com/Unix/Regular.html](http://www.grymoire.com/Unix/Regular.html)

---

### Post by tommpogg on 2011-08-30
> **userub said:**
> 
It wasn't working before because I spelled out the folder as "~/fishbones." Why wouldn't that have worked?

By using the quotes, the shell cannot understand the meaning of the ~ symbol, which usually denotes your home folder. Try to remove the quotes.

> 
What if I want to search in a file that's in a folder with a common name?
What do you mean by "common name"?

> 
How would grep know which folder to search in if I can't specify the folder location?
grep needs at least an input to look into (a file, a folder,...). 


> 
The output shows up in the terminal window. How do I arrange for the output to go out to a file?
Use > to redirect the output of grep into a file:
```

grep -r "banana" fishbones/ > filename
```> 
Also, what are "regular expressions"?
A regular expression is a pattern that describes a set of strings. Regular expressions are constructed by using various operators to combine smaller expressions.
This is quite a long topic to deal with. I suggest to read a book or a manual (for instance [this one]("http://tldp.org/LDP/Bash-Beginners-Guide/html/"))


PS: Sorry... I've just noticed that Lampi was faster than me

---

### Post by userub on 2011-08-30
Okay, the output works, but I've run into another problem.

I'd like to search for multiple words. For instance, if I have "one banana; bunch of bananas; banana peel; peeled banana" as phrases in a file, how would I search for "banana" and "peel" so that the search only returns the last two phrases and not the first two?

I tried looking on Google and found something about "/|" which doesn't seem to work. I also found something about "egreps" and "-E" and I don't understand either of them.

I had put the quotes in around the folder because I prefer spaces to  underscores in folder names. I rearranged the quotes to read ~/"Folder  Name" instead and it works now.

I was wondering how grep would search multiple folders that share the  same name, like if I had 5 different folders named "fishbones"; that's  what I meant by "common name." Based on the explanations provided, I  think grep just searches all of the folders that share that name.

---

### Post by nothingspecial on 2011-08-30
> **Lampi said:**
> use recursive grep:
```
grep -r "banana" fishbones/
```

Learning about regular expressions certainly would Cure the problem. Start from The Top with this cheat sheet.

[http://www.regexlib.com/CheatSheet.aspx](http://www.regexlib.com/CheatSheet.aspx)

---

### Post by tommpogg on 2011-08-30
> **userub said:**
> 
I'd like to search for multiple words. For instance, if I have "one banana; bunch of bananas; banana peel; peeled banana" as phrases in a file, how would I search for "banana" and "peel" so that the search only returns the last two phrases and not the first two?

You can use another grep on the output of the first one through a pipe (|):
```

grep -r "banana" fishbones/ | grep peel
```

I don't know if there is better way to do that

---

### Post by nothingspecial on 2011-08-30
With egrep you can use a "pipe" within a regular expression which means the match can contain either expression.

If you look at the cheat sheet | is for alternation. . is for any character (except a newline) and * is for 0 or more times so

banana.*peel|peel.*banana would match banana and peel in the same line in either order with something or nothing inbetween.
```

$ cat banana/fishbones
One banana
peeled banana
banana tree
bananapeel
banana peel
$ egrep banana.*peel\|peel.*banana banana/fishbones
[COLOR="Red"]peeled banana
bananapeel
banana peel[/COLOR]
```

*note you have to escape the | with a \ or bash will interpret it as it's own pipe

---

### Post by bodhi.zazen on 2011-08-30
You can do that with grep as well.

```
grep 'banana.*peel\|peel.*banana' banana/fishbones
peeled banana
bananapeel
banana peel
```

---

### Post by nothingspecial on 2011-08-30
> **bodhi.zazen said:**
> You can do that with grep as well.

```
grep 'banana.*peel\|peel.*banana' banana/fishbones
peeled banana
bananapeel
banana peel
```

Oh.......


Then stuff I have read is outdated or wrong. I was under the impression that grep didn't use |. Well not to worry, cheers. :)

---

### Post by sisco311 on 2011-08-30
> **nothingspecial said:**
> Oh.......


Then stuff I have read is outdated or wrong. I was under the impression that grep didn't use |. Well not to worry, cheers. :)

Or it isn't about GNU grep ;). From **man grep**:
> 
In GNU grep, there is no difference in available functionality between basic  and  extended  syntaxes. In  other implementations, basic regular expressions are less powerful.


---

### Post by nothingspecial on 2011-08-30
> **sisco311 said:**
> Or it isn't about GNU grep ;). From **man grep**:

Not both of you in the same thread!!!!!!

](*,)](*,)](*,)](*,)](*,)


O:)

---

### Post by waqas_butt0071 on 2011-08-30
you can also get help from 

> man grep

---

### Post by tommpogg on 2011-08-31
... or from
```

info grep

```

---

### Post by userub on 2011-08-31
Thank you for your help, everyone. My questions about Grep have been answered and I understand how to search with it now.

I'll mark this thread as solved.

---

