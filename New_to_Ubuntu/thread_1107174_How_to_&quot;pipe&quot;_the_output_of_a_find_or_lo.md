---
title: "How to &quot;pipe&quot; the output of a find or locate comand to rm -vi"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by hovzio on 2009-03-26
Hi, some background. I just recently put an old hard drive from my first pc into my current box, the drive is about 6 years old and has xp installed on it. The old pc is long broken and I just put it in my pc to access old pics and especially music. (I havent looked at the drive in 5 years, lots of goodies) I copied the old files over to new hds and removed the old hd.To the point.. There were over 150 gig pics and music copied. Umongst these thare are literaly hundreds of "Thumbs.db" files left over from my old xp drive. I don't like them and I'm to lazy to erase them all manualy.

I use the locate or find command to find them all. There they all are, absolute pathnames and seperated by Newlines. (I think??) I would like to send all these files to rm. Piping doesn't work, rm doesnt seem to accept input from a pipe.(am I wrong?) The other problem being that the pathnames seem to be seperated by newlines. I have used command substitution..
```

rm -iv "$(locate Thumbs.db)"
rm -iv "`locate Thumbs.db`"
```

Of course this does not work. For one,  the Newlines, I can eventually fix this with a temp file and sed, but don't this this is a good approach. I think a little script with a for in loop may do the trick. [-o< Does anybody have a oneliner for this or any advice. Thank you, Hovzio

---

### Post by Nepherte on 2009-03-26
something in the nature of:
```
locate Thumbs.db | xargs rm
```
should work

---

### Post by enatiello on 2009-03-26
you can try find:

find /path -name "Thumbs.db" -print0 | xargs -0 /bin/rm

---

### Post by soxs on 2009-03-26
what about paths with spaces. this could endup bad...

---

### Post by aeiah on 2009-03-26
```

find . -type f -name "[Tt]humbs.db" -exec rm -i {} \;

```


the -i flag is there mostly so you can test it and not blindly wade in. you'll probably want to replace -i with -f when you set it going unless you enjoy pressing the 'y' key repeatedly :P

---

### Post by hovzio on 2009-03-26
hello to everyone. A big thank you to all that have answered.;) One of the reasons for posting this question was just to learn. I have not tried any of the above commands but I most definatly intend to. These are some very cool replies, I have some questions.

```
locate Thumbs.db | xargs rm
```

What is this xargs command doing, how is it making rm accept data? I checked the man page and it sais "build and exec. comm. lines from stdin". Is it correct to say that this makes it possible to pipe info to another prog. that normally doesn't accept standard input?

```
find /path -name "Thumbs.db" -print0 | xargs -0 /bin/rm
``` 

I looked at the man pages, It seems <xargs -0> takes care of spaces and co. in the paths.(is this right?)The xargs manpage then makes reference to <find -print0>. Looked at -print0 option in man pages but I need a little help I guess. What exactly are these two options doing? Are they takeing care of special characters in the pathnames?

```
find . -type f -name "[Tt]humbs.db" -exec rm -i {} \;
```

What does the < {} \; > after the rm command? What does this do? What is the <exec> command doing in there? Does it enable me to pass stdin to rm?? or is the {} \; somhow doing this. I use exec at the end of shell scripts or in a test statement. What is happening here. 


Thank you so much for your replies, a quick explanation would be greatly appreciated. Thanks, Hovzio

---

### Post by Rolcol on 2009-03-26
> **hovzio said:**
> ...
```
find . -type f -name "[Tt]humbs.db" -exec rm -i {} \;
```

What does the < {} \; > after the rm command? What does this do? What is the <exec> command doing in there? Does it enable me to pass stdin to rm?? or is the {} \; somhow doing this. I use exec at the end of shell scripts or in a test statement. What is happening here. 


Thank you so much for your replies, a quick explanation would be greatly appreciated. Thanks, Hovzio
The find command will execute whatever command is after -exec and it will replace {} with the file location.  \; tells find that it is the end of the command that will be executed with each found file.

---

### Post by hovzio on 2009-03-26
> **Rolcol said:**
> The find command will execute whatever command is after -exec and it will replace {} with the file location.  \; tells find that it is the end of the command that will be executed with each found file.

```
find . -type f -name "[Tt]humbs.db" -exec rm -i {} \;
```

Thank you Rolcol! This works. I set up a test directory with all sorts of wierd sub-directories and files. Spaces, (), it all worked. Why is this working? I don't see anything being commented out or any "". How does this work, or does the find command just automatically process this correctly? 



```
find /path -name "Thumbs.db" -print0 | xargs -0 /bin/rm

```
I couldn't quite get the above to work:

```
:~/practice/Practice_for_find_thumbs$ find /path -name "Thumbs.db" -print0 | xargs -0 /bin/rm
find: `/path': No such file or directory
/bin/rm: missing operand
Try `/bin/rm --help' for more information.
```

Just thought I'd mention it. Thanks everybody for the help and thanks Rolcol for the solution.:P

---

