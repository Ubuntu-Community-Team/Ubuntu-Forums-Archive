---
title: "Learning programing - Need Help!"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by falkTX on 2009-01-06
Hello guys from the best OS in the Earth!
I need to know how I automate something.


I have:

XX:XX:XX:XX:XX Name1 [whatever#1]
XX:XX:XX:XX:X2 Name2 [whatever#2]

as terminal output.
But I only need the first "XX:XX:XX:XX" stuff.
How do I made the rest disappear? (like in 'cmd | grep blah blah')



So far I do:

cmd > /location/to/a/file
gedit /location/to/a/file 
#I have to edit it manually
.--------------------.

How do I automate this step?
It is possible to make it like this?:
  XX:XX:XX:XX [all]
  XX:XX:XX:X2 [all]

(when XX is the first value reported by 'cmd')



Thank you

---

### Post by Locke_99GS on 2009-01-06
You can use a bash script and just send the output of grep to a file. 

*cmd | grep blah blah > myFile.txt*

With other languages, you could parse the line, and using " " as a delimiter, write the output of the first token to a file. Methods vary from one language to the next.

---

### Post by decoherence on 2009-01-06
```
cmd | awk '{print $1 " [all]"}'

```
prints the first field, where fields are delimited by space or tab

---

### Post by falkTX on 2009-01-06
I don't need grep, just to parse the lines (delete everything after 'space')

That's what I'm asking, and I don't know how to do it

---

### Post by efexD on 2009-01-06
Also, scroll down and check out the programming section.

---

### Post by falkTX on 2009-01-06
> **decoherence said:**
> ```
cmd | awk '{print $1 " [all]"}'

```
prints the first field, where fields are delimited by space or tab

Thank you so much!!!

It was kind of simple, (LOL)
that just prove I need to learn a lot.

---

### Post by falkTX on 2009-01-06
> **decoherence said:**
> ```
cmd | awk '{print $1 " [all]"}'

```
prints the first field, where fields are delimited by space or tab

Thank you so much!!!

It was kind of simple, (LOL)
that just prove I need to learn a lot...

---

### Post by falkTX on 2009-01-06
Oops..
The server was down for a sec,
looks like I posted twice.

---

### Post by The Cog on 2009-01-06
Another way to skin that cat is 
<command> | cut -f 1 -d ' '

---

### Post by decoherence on 2009-01-07
I *always* forget about cut! Such a handy thing.

---

