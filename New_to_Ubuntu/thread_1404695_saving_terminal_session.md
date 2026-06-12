---
title: "saving terminal session"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-11
I remember once using a command that would save all output of a bash session to a file and it would keep doing so until you ask it to stop.I completely forgot what it was. Thanks for any reminder.

---

### Post by sisco311 on 2010-02-11
I think, you are looking for the **script** command.

---

### Post by Mustard on 2010-02-11
are we talking about piping the output to a file?  
or something like bash_history?

```
ls -alh > somefile
```

??

---

### Post by Mustard on 2010-02-11
> **sisco311 said:**
> I think, you are looking for the **script** command.

Ooo..yeah..that looks like just the thing. :)

> NAME
     script &#8212; make typescript of terminal session

SYNOPSIS
     script [-a] [-c COMMAND] [-f] [-q] [-t] [file]

DESCRIPTION
     Script makes a typescript of everything printed on your terminal.  It is
     useful for students who need a hardcopy record of an interactive session
     as proof of an assignment, as the typescript file can be printed out
     later with lpr(1).


---

### Post by rcayea on 2010-02-11
This may or may not help.

If you want all your terminal info, just type in "history" without quotes , of course. I believe man history will tell you what you want, too.

---

### Post by blur xc on 2010-02-11
> **Mustard said:**
> are we talking about piping the output to a file?  
or something like bash_history?

```
ls -alh > somefile
```??

Not to argue semantics- but that's redirecting output.  Piping is when you use this guy - |


```
ls -lha | grep foo* > bar.txt
```
[SIZE=1]*lame example*[/SIZE]

A redirect sends the output of a command somewhere else, a pipe sends it to the input of another command.

BM

---

### Post by Mustard on 2010-02-11
> **blur xc said:**
> Not to argue semantics- but that's redirecting output.  Piping is when you use this guy - |


```
ls -lha | grep foo* > bar.txt
```
[SIZE=1]*lame example*[/SIZE]

A redirect sends the output of a command somewhere else, a pipe sends it to the input of another command.

BM

I appreciate the correction. :)

I've been reading some bash scripting tutorials and a little knowledge has made me dangerous. :P

---

### Post by SteelCore on 2010-02-11
I think it might be redirection. This thing would put any command I type into the terminal plus its output into a file and it keeps doing this until I ask it to stop. The end result is a file containing everything that was typed and output on that terminal session.

---

### Post by Mustard on 2010-02-11
> **SteelCore said:**
> I think it might be redirection. This thing would put any command I type into the terminal plus its output into a file and it keeps doing this until I ask it to stop. The end result is a file containing everything that was typed and output on that terminal session.

The **script** command mentioned in the second post sounds closer to the description than redirection does.

---

### Post by SteelCore on 2010-02-11
Yes. It is the script command indeed. Thank you all.

---

### Post by PGTips91 on 2010-02-11
> **rcayea said:**
> This may or may not help.

If you want all your terminal info, just type in "history" without quotes , of course. I believe man history will tell you what you want, too.

I'm using Konsole, Version 2.2.3, Using KDE 4.2.4 (KDE 4.2.4) and all I need to do is click on 'Scrollback > Save Output' and a dialog opens to allow me to name the file and specify which directory to save it in.

Older versions allow selecting and copying the output to the terminal but that is a bit more cumbersome and slow.

A quick way to record work done, in the current directory, is to create an empty text file then open it with Gedit or the like. Saving the text file is then already located in the desired location and saves having to navigate through multiple layers.
```
touch myfile.txt && gedit myfile.txt
```

```
man script
``` gives a run-down on this command. Script runs until you send a 'Control +d' to stop it. A useful command to know about.

Paul

---

### Post by SteelCore on 2010-02-11
One more thing please. There is the issue of these strange looking symbols that end up in the new file after using 'script'. It's actually even worse when you try to open it with OpenOffice although when you cat the file contents back in the terminal things look normal again. Is there a solution for this? 
Thanks again.

---

### Post by DaithiF on 2010-02-12
Hi, can you post a screenshot showing the symbols, and maybe an excerpt from the file, copy/pasted from the terminal where it looks ok, so we can compare the two?

---

### Post by SteelCore on 2010-02-12
> **DaithiF said:**
> Hi, can you post a screenshot showing the symbols, and maybe an excerpt from the file, copy/pasted from the terminal where it looks ok, so we can compare the two?

sure

---

### Post by PGTips91 on 2010-02-12
Those strange characters are formatting information. You can eliminate them by displaying the file in a console with the 'cat' command. However, to get rid of them in a text file you will need to either select the newly displayed text and copy and save to a text file or use the 'scrollback > Save Output' function.

I tried using ```
cat testfile > testfile.txt
``` but it simply transferred all the formatting characters, so you are left with only a manual transformation as far as I can tell.

```
 [01;35m100_9053-Roses.jpg[00m
``` corresponds to purple display
```
[00mSetup-GRUB.txt[00m
``` corresponds to white [or normal] display, in my configuration of Konsole.

You will notice that, when saving in asci only text, the highlighting of the current day in the calendar is lost, so some information will be lost if you omit those special formatting characters. They are not too intrusive once you know what they represent any way.

Paul

---

### Post by PGTips91 on 2010-02-12
By the way, I have found some useful information on charcter sets in another application that I am looking into, [Zoph]("http://www.zoph.org/concrete/"), here : --

[What is UTF-8?]("http://en.wikibooks.org/wiki/Zoph/Upgrading/Changing_your_database_to_UTF-8#What_is_UTF-8.3F")

Paul

---

