---
title: "bash question"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by mzdrojowy on 2009-11-03
Just trying some simple commands and was wondering perhaps the community could tell me where I went wrong here with this 

who : date | gedit log1

It was just something simple to begin to experiment with bash commands and piping, but well it didnt work.

---

### Post by SeanHodges on 2009-11-03
What is it you're trying to do?

gedit will not accept a pipe like that. It cannot read from a stream.

You probably want something like this:

who : date | tee log1

---

### Post by akelsall on 2009-11-03
I'm pretty familiar with Unix, but I've never seen the ":" symbol used like that. It's used in scripts alot. 

Getting back to your command. I'm not sure what you're trying to accomplish. You're sending the output of the first two commands (who and date) into an editor, which really doesn't make sense. The command "gedit log1" is just going to open the file named log1. I'd recommend picking up a beginners book on Unix and start from there. Start small and build up your skills. 

who : date | gedit log1

---

### Post by mzdrojowy on 2009-11-03
thank you both for your help . 


who : date | tee log1

this makes sense but what might the command "tee" be ? 
is it just gedit or all text editors that wont accept a stream ? 
like i said not really trying to do anything but take that output of the 2 commands and write them to a text file for later veiwing. Sure not very functional but just experimenting with the basics ....

---

### Post by diesch on 2009-11-03
The ":" doesn't have any special meaning here. The OP is just calling "who" with the two parameters ":" and "date". That's the same as calling "who am I" or "who wants coffee" - who doesn't care about what two parameters you use.

---

### Post by ukripper on 2009-11-03
You need >

example:
date > log1.txt
it will save date in log1 text file

---

### Post by mzdrojowy on 2009-11-03
cool I get it now ... did some experimenting and figured some things out 
the "tee" command worked good in this and I could view the file with the "cat" cmd so this is cool . 
 I swear I read somewhere" : "was used to combine commands together, I now know Im wrong in that . Problem is Im reading like three linux books all at the same time lol and i seem to lose what was said where .. damn A.D.D . 

again thanks to all

---

### Post by mzdrojowy on 2009-11-03
example:
date > log1.txt
it will save date in log1 text file


lol thats what I LOVE about UNIX/LINUX 
SOOOOOO many ways to skin a cat :p

---

### Post by Penguin Guy on 2009-11-03
Saving the output of who : date to a file is a trivial task, editing it with gedit can be slightly more complicated. Here are the two solutions below:

Save output of [COLOR="Green"]who : date[/COLOR]:
```
who : date > log1
```

Edit output of [COLOR="green"]who : date[/COLOR] with gedit:
```

file=`mktemp`            # Make a temporary file, we will refer to this file as $file
who : date > ${file}     # Store the results of 'who : date' in $file
gedit ${file}            # Open $file with gedit
rm ${file}               # Remove $file
unset file               # Make $file no longer refer to the temporary file

```

---

### Post by SeanHodges on 2009-11-03
> **diesch said:**
> The ":" doesn't have any special meaning here. The OP is just calling "who" with the two parameters ":" and "date". That's the same as calling "who am I" or "who wants coffee" - who doesn't care about what two parameters you use.

It does when you're the one who wants coffee.

---

