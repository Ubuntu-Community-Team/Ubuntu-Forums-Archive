---
title: "Terminal help"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by orrymr on 2011-03-24
Suppose I navigate around the terminal quite a bit using the "cd" command. After a while the terminal has filled up quite a bit - for example each line will say username@ubuntu:~/Documents/ExampleFolder1/ExampleFolder2/ExampleFolder3$ before I can issue another command. Is there any way to shorten this?

---

### Post by Bucky Ball on 2011-03-24
.

That's it.

Takes you /home.

---

### Post by sisco311 on 2011-03-24
Edit your ~/.bashrc file. Search for the line(s) where PS1 is initialized and replace the lowercase w with an uppercase W:
```
 if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\[color=red]W[/color]\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[color=red]W[/color]\$ '
fi

```

Then run:
```
. ~/.bashrc
```

For details check out:
```
man bash | less +/"^PROMPTING"
```

---

### Post by Bucky Ball on 2011-03-24
> **sisco311 said:**
> Edit your ~/.bashrc file. Search for the line(s) where PS1 is initialized and replace the lowercase w with an uppercase W:
```
 if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\[COLOR=red]W[/COLOR]\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR=red]W[/COLOR]\$ '
fi

```Then run:
```
. ~/.bashrc
```For details check out:
```
man bash | less +/"^PROMPTING"
```

? OP wants to get from:

username@ubuntu:~/Documents/ExampleFolder1/ExampleFolder2/ExampleFolder3$

to:

username@ubuntu:$

That's all.

---

### Post by vanadium on 2011-03-24
The environment variable PS1 determines how the prompt looks. By default, it is:
```

vanadium@vanadium:~/Documents/Projects$ echo $PS1
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$

```
The last fragment says \u@\h:\w\$, which stands for "user@host:working_directory$ ". If you remove the \w, you get a prompt without working dir:
```

vanadium@vanadium:~/Documents/Projects$ export PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h \$ '
vanadium@vanadium $ 

```

To keep displaying a path, but limit its length, some programming is required. Here is an article on how you can do this. This is an article for Mac users. But do not worry: that proprietary operating system has exact the same gnu terminal as you are using on your ubuntu system.

The article also explains how you can make a change permanent: you need to include the command in the hidden configuration file .bash_profile in your user home directory.

The article shows you how to edit that configuration file using the command line editor vi. You may prefer to use the graphical editor gedit, which will be much more familiar. Instead of "vi .bash_profile", use the command
```

gedit .bash_profile

```
to load the bash configuration file in gedit.

---

### Post by nothingspecial on 2011-03-24
> **Bucky Ball said:**
> ? OP wants to get from:

username@ubuntu:~/Documents/ExampleFolder1/ExampleFolder2/ExampleFolder3$

to:

username@ubuntu:$

That's all.

Read the OP again, Sisco has it right .....

.....as usual :rolleyes:

---

### Post by orrymr on 2011-03-24
Tried that, then this happens:

```

orry@ubuntu:~/Desktop/Wireless Setup Ubu$ .
bash: .: filename argument required
.: usage: . filename [arguments]

```

---

### Post by seawolf167 on 2011-03-24
> **Bucky Ball said:**
> .

That's it.

Takes you /home.

How do you use that?

I've always used 

```
cd ~
```

to go to /home.

. is the current directory, and as such

```
cd .
```

wouldn't do anything (it'd just stay in the current directory)

---

### Post by nothingspecial on 2011-03-24
Try this 

```
nano .bashrc
```

go to the very bottom of the file and paste this in

```
alias short="export PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h \$ '"
```

Press Ctrl+O to save it then Ctrl+X to exit.

Then type ```
. ~/.bashrc
```

Now next time the full path to your working directory gets to long just type ```
short
```

When you want the full path back, type

```
. ~/.bashrc
```

again.

When in "short" mode you forget where you are, type ```
pwd
```

---

### Post by vanadium on 2011-03-24
The brilliant solution was already posted by sisco311 indeed. This forum does not give a warning when other replies are posted in the mean time, and I was posting my replying, unaware that a much better approach was posted already.

The \W instead of \w gives only the name of the current directory instead of the full path. Thus, you always have a hint of your current directory, yet the prompt stays small.

---

### Post by orrymr on 2011-03-25
> **sisco311 said:**
> Edit your ~/.bashrc file. Search for the line(s) where PS1 is initialized and replace the lowercase w with an uppercase W:
```
 if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\[COLOR=red]W[/COLOR]\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR=red]W[/COLOR]\$ '
fi

```Then run:
```
. ~/.bashrc
```For details check out:
```
man bash | less +/"^PROMPTING"
```

Awesome, thanks for the help (marking thread as solved). Just not sure about that last line: 
```
man bash | less +/"^PROMPTING"
```
What exactly is that doing? I understand that it's bringing up a help file, but what do all the individual commands do?

Also, in file it brings up the first line is:
```

When executing interactively, bash displays the primary prompt PS1 when it is ready to read a command, and the secondary prompt PS2 when it needs more input
       to complete a command.

```
Is the primary prompt the thing that's "waiting" for me to type when I open up the terminal. Would that make PS2 the prompt that comes up, say, when I sudo <do something> and need to type in my password?

---

### Post by sisco311 on 2011-03-25
> **orrymr said:**
> Awesome, thanks for the help (marking thread as solved). Just not sure about that last line: 
```
man bash | less +/"^PROMPTING"
```
What exactly is that doing? I understand that it's bringing up a help file, but what do all the individual commands do?


In short it opens up the bash manual page at the "PROMPTING" section.

man bash - opens the manual page;

[| (pipe)]("http://mywiki.wooledge.org/BashGuide/InputAndOutput#Pipes") - connects the output of one application directly to the input of another;

less - is a [terminal pager]("http://en.wikipedia.org/wiki/Terminal_pager") or file viewer  with searching capability;

less +/"PATTERN" file - opens "file" and searches for PATTERN, where PATTERN is a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression");

In a regular expression ^ matches the starting position of a line, so ^PROMPTING matches the first line which begins with PROMPTING.

**man bash | less +/"^PROMPTING"** - opens the output of **man bash** (the content of the manual page) in less and less performs a search for the line which begins with "PROMPTING".

> **orrymr said:**
> 
Also, in file it brings up the first line is:
```

When executing interactively, bash displays the primary prompt PS1 when it is ready to read a command, and the secondary prompt PS2 when it needs more input
       to complete a command.

```
Is the primary prompt the thing that's "waiting" for me to type when I open up the terminal. 


Yes.

> **orrymr said:**
> 
Would that make PS2 the prompt that comes up, say, when I sudo <do something> and need to type in my password?

No.  The secondary prompt: by default `> ' (without the quotes) , is used when continuing commands on multiple lines; and the result of executing the command is expected on following lines.

Some examples:
```
[sisco@acme ~]$ echo "mouse
> cat
> dog" | less +/"cat"

```

```
[sisco@acme ~]$ PS2="secondary prompt > "
[sisco@acme ~]$ for i in {1..3}
secondary prompt > do
secondary prompt >   echo "$i"
secondary prompt > done
1
2
3
[sisco@acme ~]$ PS2="> "

```

```
[sisco@acme ~]$ if [[ -f ./file ]]
> then
>   echo "./file is a regular file"
> else
>   echo "./file is not a regular file"
> fi
./file is not a regular file

```

---

### Post by nothingspecial on 2011-03-25
Since man pages are opened with less (by default).......

..... you could type

```
man less
```

then hit the / key....

and type ^PROMPTING

Does the same thing...... might be easier to remember.

Pressing N takes you to the next instance, pressing Shift-N takes you back one.

And typing PROMPTING without the ^ will bring up any line with PROMPTING anywhere in it.

+/ executes the / (if you see what I mean)

---

### Post by sisco311 on 2011-03-25
> **nothingspecial said:**
> Since man pages are opened with less (by default).......


If man uses less as its output pager, one could pass the search command via the LESS environment variable:
```
env LESS="$LESS +/PATTERN" man command
```

:P

> **nothingspecial said:**
> 
..... you could type

```
man less
```

then hit the / key....

and type ^PROMPTING

Does the same thing...... might be easier to remember.

Pressing N takes you to the next instance, pressing Shift-N takes you back one.

And typing PROMPTING without the ^ will bring up any line with PROMPTING anywhere in it.

+/ executes the / (if you see what I mean)

and h or H displays the help page of less.

---

