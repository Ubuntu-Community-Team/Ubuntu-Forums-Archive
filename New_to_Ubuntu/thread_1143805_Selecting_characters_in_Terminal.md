---
title: "Selecting characters in Terminal"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by DayvanKowboy on 2009-04-30
Good day [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)  What do you mean that emoticon was out of place?   
 Ok so I am pretty brand spankin new to Linux and I have a question about using Terminal.  I'm wanting to write a shell script that will automate and rename some mp3's for me.  Right now I'm using something like this:

 ```
 for f in *.mp2; mv &quot;$f&quot; &quot;${f.mp2}.mp3&quot;; done 
``` (On an off-note I'm really unsure what % means because I tried to find it as I just nicked this script and I couldn't find an explenation of why it is so important?  I tried removing it but got a bad substitute error) 

 Ok so that's just an example and I can't really think of any decent reason for songs having a .mp2 extension in the first place.  However I don't think this method is very efficient (actually it is very efficient it's just a pain in the tits when you misuse it) as I was messing around with scripts last night and I ended up with files ending in .mp3.mp3.mp3.mp3.mp3(etc for the next four lines).  So it was hard to fix and I ended up just removing the files and starting again.  So what I'm looking for now is to store in the variable f all the characters before .mp3?  Because I think the way terminal works is if I used something like 

 for f in *.mp3  

It would put the whole filename in f.  So basically all I want is to learn how to select all the characters before a certain point in a file name.  Cheers for any help  Peace  Jamie

---

### Post by cariboo on 2009-04-30
To make you task a lot easier, use somethin like this:

```
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 
```

to remove the spaces and replace them with an underscore. then for consistency use this:

```
for i in *.[Mm][Pp]3; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done 
``` 

to remove capital letters in file names. Linux doesn't deal well with spaces in file names, as it sees words seperated by spaces as seperate files.

---

### Post by DayvanKowboy on 2009-04-30
Cheers man that helps, but I was wondering if there was alternate code so that if I do make a mistake again and end up with multiple extensions, is there a way to select all the characters before the first period (.) in the filename?

---

### Post by DayvanKowboy on 2009-04-30
Bumpity?

---

### Post by spillin_dylan on 2009-04-30
You're going to need something along the lines of:
```
echo ${file%%.mp3*}
```
This should "echo" anything before ".mp3", IIRC.

There are some awesome **bash** tutorials on this stuff on the 'net, but I'm not sure exactly where at the moment....

---

### Post by spillin_dylan on 2009-04-30
Try this:

[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

### Post by DayvanKowboy on 2009-05-01
Thanks a lot guys, I see what I'm doing now :)

---

