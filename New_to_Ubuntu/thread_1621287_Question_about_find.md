---
title: "Question about find"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Iecur on 2010-11-14
So I'm new to the world of Ubuntu as you may have guessed barely been using it for about two months now.

My computer:
I'm running Ubuntu 10.10 via WUBI.

What I know so far:
I've been trying to learn the basics of the terminal. So I have been reading man files and whatnot.  I'm currently looking at *find* almost done.  And I'm trying to figure out this one example within there that has me confused to hell.  

Some help would be greatly appreciated in understanding it:

```
cd /source-dir
find . -name .snapshot -prune -o \( \! -name *~ -print0 \)|
cpio -pmd0 /dest-dir

```I changed the source-dir and the dest-dir, and tried using single quotes and dual quotes.  And read the description of this example and felt like I understood what was going on but I get a message:

find: paths must precede expression: (\! -name *~ )

Do I have to enter in all of that code into the command line is one of the things I'd like to know.  
Or is it just fine to skip the first line and do the last two lines.  And I thought if you were running multiple commands at once you were required to have the " ; " character in there or did I misinterpret something ?  I would assume they were different lines but I would expect something like " ~$ " in front of them.  And I thought " | " was used in one command and " \ " was used in case you were going to use a second line for one long command.

If I try something like:

$ find . -name sad -prune -o '(\! -name *~ -print0 )' | cpio -pmd0 ~/dir

I get the same exact message.  So I think of not omitting files hmm..same results..well earlier I did something else ah yes..

$ find . f* | cpio -pmd0 ~/dir

This finds and lists all files/directories with an f in them and then I get:

: Cannot stat: No such file or directory
0 blocks

Please someone help me understand this ?

Show me a real world example of this or whatnot if at all possible.  Damn and I have to run thanks to anyone that can help sorry if I missed something I'll get to it as soon as possible.

---

### Post by gmargo on 2010-11-14
Can you please specify the post number within that thread?  I don't want to read 11 pages of gudge just to find that example.

---

### Post by Iecur on 2010-11-14
Oh no..hmm..I guess in my rush to leave I worded things in a weird way.  The example was in the "man find" pages.

cd /source-dir
find . -name .snapshot -prune -o \( \! -name *~ -print0 \)|
cpio -pmd0 /dest-dir

This  command  copies  the contents of /source-dir to /dest-dir, but omits files and directories named .snapshot (and anything in them).  It also omits files or directories whose name ends in ~, but not their contents.  The construct -prune -o \( ... -print0 \) is quite  common.   The  idea here  is that the expression before -prune matches things which are to be pruned.  However, the -prune action itself returns true, so the following -o ensures that the right hand side is evaluated only for those directories which didn't get pruned (the contents of the  pruned  directories are not even visited, so their contents are irrelevant).  The expression on the right hand side of the -o is in parentheses only for clarity.  It
emphasises that the -print0 action takes place only for things that didn't have -prune applied to them.   Because  the  default  `and'  condition between tests binds more tightly than -o, this is the default anyway, but the parentheses help to show what is going on.

That was the example with it's explanation which I could follow but when I tried plugging in real values I guess I got really confused so I was wondering if someone could make up some files/directories that I could reproduce and try to replicate this example.  I normally would just move on and hope that I would eventually understand what was said but for some reason this particular example has just been irking me and I felt I had to figure out what it was.  But if it's too much trouble I think I've calmed enough that if no one feels like answering it I won't lose sleep over it..heh.

Although I almost made this computer a paper weight trying to follow one of the tutorials...Maybe I should ask about that instead of confusing everyone with this lol.

---

### Post by benson444 on 2010-11-14
> Do I have to enter in all of that code into the command line is one of the things I'd like to know. 
Or is it just fine to skip the first line and do the last two lines.

It is actually 2 commands. You need to cd to the source-dir if you run the exact same find command as it searches in . (which means the current directory). If you don't cd to the directory first then you must use an absolute, or relative path to the source-dir, e.g.

```
find /home/username/source-dir # absolute path from / (root dir)
find source-dir # relative (source-dir in current dir)
find ../source-dir # relative (source-dir in parent dir)
```

> And I thought if you were running multiple commands at once you were required to have the " ; " character in there or did I misinterpret something ? I would assume they were different lines but I would expect something like " ~$ " in front of them. And I thought " | " was used in one command and " \ " was used in case you were going to use a second line for one long command.

Yeah, they probably should have the $ prompt in there. It would make it clearer. However, when I entered that find command the prompt changed to a > character, meaning that it was waiting for more input. I did get the same error when I tried using quotes though, so I think that is where you are going wrong. Just type it in exactly as written, but changing the source-dir and dest-dir as needed.

The | is called a pipe. It's used to send the output of one program to the input of another program. So, you're running find and pruning the results, then piping the output of that to the cpio program. Here's a simple example of piping (cd on its own takes you to your home directory, and grep is a program for searching for patterns):

```
cd
ls -la | grep Do
```

Once you know about pipes you realize that it can't be three commands and the second line has to run into the third one. I think that whenever you end a line with | bash will sit there waiting for you to tell it where to pipe the output to.

The \ is called the 'escape character'. In bash some characters have special meanings. To stop bash interpreting these characters they have to be 'escaped'.

It's used to split a long command into multiple lines because the newline character is special. Bash interprets it as 'this-is-the-end-of-the-command', so using \ escapes the newline.

I came up with this example:

```
cd
mkdir source-dir dest-dir
cd source-dir
mkdir One Two
touch One/one.txt One/one.txt~
touch Two/two.txt Two/two.txt~
ls
ls One
ls Two
pwd
find . -name One -prune -o \( \! -name *~ -print0 \) | cpio -pmd0 ~/dest-dir
cd ~/dest-dir
ls
ls Two
```

I ended up with just ~/dest-dir/Two/two.txt, so the entire One directory was skipped, as was the file wasn't in One, but ended with ~

---

### Post by Iecur on 2010-11-14
Yeah I just realized that it put the > character my bad on that oversight.  Hah, grep another thing I'm having a hard time understanding..I technically get it but I guess I just can't seem to put together in my head so that I can logically think it should be like this and end up doing things the wrong way.  Yeah sorry I knew a little about pipes I just said the previous thing because I thought the two commands were one which in my head got interpreted as two being three. x'D

Okay the escape character is where I get totally lost.  I got that ( ) were special characters and then I got a bit confused with \(...\) and '( )' in the manpages.  

OPERATORS
  Listed in order of decreasing precedence:

  ( expr )
    Force precedence.  Since parentheses are special to the shell, you will normally need to quote them.  Many of the examples in  this  manual page use backslashes for this purpose: `\(...\)' instead of `(...)'.


Hmm..I thought that meant that I was required to use ' ' in \(...\) but it's just that without quotes.

Not sure how much of that I am following though.  The code is then technically seen as:
find . -name .snapshot -prune -o (followed by \ which will be seen as a new line so I'll hit return now and have a second line)
( \! -name *~ -print0 \) | cpio -pmd0 /dest-dir
Or does each \ make a new line ?

Okay I tried out your example.  And it worked!  Thank you so very much for that.  I couldn't help but notice that after I hit enter I get a line that says, "0 blocks" could you help explain that to me ?  

I got the same message a few times before when I was attempting it but I could never locate any backed up files/folders.  I guess that doesn't really matter now that I finally got it to work.  Thank you so much!  I feel like such a fool still not getting so much of this.  But I'll keep trying!

I forget did they get rid of the thanks button on here ?  I remember hearing about that on some forum I used to visit not sure if it's this one or not.  And I'll leave this unsolved for tonight in case you could possibly clarify a bit further on those few things I was still confused about.  If not I'll be sure to change the prefix tomorrow morning but for now I should be heading off to bed.  Again thanks I really appreciate it.  Have a good day.  Good night.

---

### Post by benson444 on 2010-11-14
Man, don't feel stupid if you don't pick up all this stuff straight away. Just play around and try stuff out. And try not to destroy your install. Been there, done that...

I've never used cpio before, but reading the info page (info cpio), it seems that it prints out the number of blocks that were copied. I guess with a couple of empty text files no full blocks are written. You can turn it off with the --quiet option.

/ doesn't make a new line, it stops bash from interpreting the newline character that is input if you press Enter. You can list a directory with

ls<Enter>

or

l\<Enter>
s<Enter>

In the second case the first newline char is not interpreted by bash. It effectively ignores it and carries on reading directly after l. So it reads ls<Enter>

You need to escape the ( char so that bash doesn't interpret it and just passes it as a literal ( to the find command, which then interprets it in its own way. Same thing with ! and )

Like the find man page says, you can also use quotes to do the same thing, but it's not entirely clear. You have to quote each char:

find . -name .snapshot -prune -o '(' '!' -name *~ -print0 ')' | ...

Hope this makes some sense.

---

