---
title: "space character seperates string in container"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by per_plex on 2011-08-27
Hi everyone,

I try to use the terminal for multiple renaming. For this I got a script from someone and it goes like this:

for F in $(find *.pdf); do mv ${F} $(echo ${F} | sed s/pdf/txt/); done 

it searches for all pdf files and changes them to txt files.
However, it does not work for files containing a space character. Here the container F (is this called a container btw.??) separates the input from the find command into single words. The foldername "hello world" would be separated in "hello" and "world". 
My question is: how can this be inhibit? 

Thanks in advance
Jakob

---

### Post by The Cog on 2011-08-27
I think putting this command in front should work:
```
export IFS=$'\n'
```
It says the inter-field-separator is newline, rather than the normal newline-or-tab-or-space.

---

### Post by nothingspecial on 2011-08-27
Also, always quote your variables.

[http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)

---

### Post by sisco311 on 2011-08-27
Check out the first (probably the most common pitfall) from the link posted by nothingspecial. 

Oh, and [http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)

Also, instead of *echo text | sed whatever* you can use [parameter expansion]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion").   

```
while IFS= read -d '' file
do
    mv -b -- "$file" "${file%.pdf}.txt"
done < <(find ./ \*.pdf -print0)
```

---

### Post by per_plex on 2011-08-29
hey, thanks a lot for your replies, I made it with your help :)

however, its still a bit fishing in the dark with those variables. Sometimes it has to be in " ", sometimes the spaces have to be preceded with a /, sometimes not. And some more stuff which confuses me - I think I need to follow an introduction to shell programming. I found this site [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/) or does anyone have a tip?

greets
Jakob

---

### Post by sisco311 on 2011-08-29
That's a very outdated guide. Check out the BashGuide, BashFAQ and BashPitfalls at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

---

