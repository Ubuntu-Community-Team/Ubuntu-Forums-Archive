---
title: "Bash Scripting - How do I search a file?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by roololing on 2011-06-28
I'm trying to write a bash script which reads a value from a file. I want it to take that value and search another file for the same value, and tell me what line it's on.

All I need to know is how to search a file and print a line number.

So if the input was 4, and the file that was being searched contained
```
1
3
4
6
8
9
```Then it would return
```
line 3
```Any help would be appreciated.

---

### Post by sisco311 on 2011-06-28
I would use awk instead of bash. Is this your homework?

---

### Post by roololing on 2011-06-28
Nah, it's for an internship. I edited it just now, by the way.

---

### Post by sisco311 on 2011-06-28
> **roololing said:**
> Nah, it's for an internship. I edited it just now, by the way.

Hmmm, I think the same rules apply... From the [CoC]("http://ubuntuforums.org/index.php?page=policy"):
> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

> **roololing said:**
> 
All I need to know is how to search a file and print a line number.


I'm in a good mood, so here are some hints (I didn't test them):

BASH:
```

i=0
read -r number < file1
while read -r line
do
    (( i++ ))
    if [[ "$line" == "$number" ]]
    then
        echo "$i"
    fi
done < file2

```

GREP:
```
grep -n number file2
```

AWK:
```
awk '/number/ {print NR}' file2
```

AWK v2:
```
awk 'NR==FNR{_=$0; next} {if ($0 == _) print NR-1}' file1 file2
```

Once again, I would do it in awk.

---

### Post by lisati on 2011-06-28
> **roololing said:**
> Nah, it's for an internship. I edited it just now, by the way.

Hmmm, still a bit like homework. We don't mind helping if you get stuck.....

---

### Post by DaithiF on 2011-06-29
@lisati, you must be my long lost cousin from NZ :)

---

### Post by nothingspecial on 2011-06-29
Now I'm confused????? 

:-?:rolleyes:

---

### Post by DaithiF on 2011-06-29
i've just noticed sisco's new profile pic, and now yours too nothingspecial, hmm, did i miss out on a recent cat-in-clothes meme?  :)

---

### Post by nothingspecial on 2011-06-29
> **DaithiF said:**
> i've just noticed sisco's new profile pic, and now yours too nothingspecial, hmm, did i miss out on a recent cat-in-clothes meme?  :)

Here you go

[http://ubuntuforums.org/showthread.php?t=1792019](http://ubuntuforums.org/showthread.php?t=1792019)

As far as I can see, you have nothing to do :P

---

### Post by roololing on 2011-06-29
Thank you for your help!

As for the rule, I think it's okay, because this is only for a portion of the code I was stuck on, not the whole thing. I'm getting a date from one file and then comparing it to the same date in another file, retrieving a list of numbers in the second file that come after the date. If the date isn't in the second file, it takes the numbers from the dates before and after it and uses their numbers to figure out which numbers correspond with the input date. It's for temperatures and wind direction and stuff like that. I think this is the only thing I needed help on, I just have to finish putting things together.

Again, thanks.:)

---

### Post by nothingspecial on 2011-06-29
Are you working in the Mauna Loa Observatory?

---

### Post by roololing on 2011-06-29
Most of the observatories are on Mauna Kea. I'm working at the Canada-France-Hawaii Telescope. Not actually on the mountain though, they have offices in Waimea, a small (biggish by the standards of this island) town a few miles south of the mountain. Their [website]("http://www.cfht.hawaii.edu/") is pretty interesting. Or so I'm told. I've never really looked at it.:lolflag:

---

### Post by nothingspecial on 2011-06-30
> **roololing said:**
> Most of the observatories are on Mauna Kea. I'm working at the Canada-France-Hawaii Telescope. Not actually on the mountain though, they have offices in Waimea, a small (biggish by the standards of this island) town a few miles south of the mountain. Their [website]("http://www.cfht.hawaii.edu/") is pretty interesting. Or so I'm told. I've never really looked at it.:lolflag:

Cool, I am jealous :D

---

