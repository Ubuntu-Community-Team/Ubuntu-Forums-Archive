---
title: "Beginner - Listing only n results with ls"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by RakeshSugirtharaj on 2009-12-10
Hi,

I am new to linux and ubuntu. Can anyone pls tell me how to list only 'n' results using ls command?

---

### Post by freesitebuilder on 2009-12-10
Here's the man page for ls, but I can't see the option you want. 

[http://linuxcommand.org/man_pages/ls1.html](http://linuxcommand.org/man_pages/ls1.html)

You could list items using width, so they go across the screen, if the problem is the first items disappearing off the top of the terminal.

---

### Post by DGortze380 on 2009-12-10
> **RakeshSugirtharaj said:**
> Hi,

I am new to linux and ubuntu. Can anyone pls tell me how to list only 'n' results using ls command?

What do you mean by 'n' results?

results that start with the letter?
results that contain the letter 'n'?
n number of results?

you'll need, grep, awk, sed, or a loop.

---

### Post by SuperSonic4 on 2009-12-10
> **RakeshSugirtharaj said:**
> Hi,

I am new to linux and ubuntu. Can anyone pls tell me how to list only 'n' results using ls command?

I'd use head from the top down

```
ls <whatever> | head -n1
```

and tail from the bottom up

```
ls <whatever> | tail -n1
```

where 1 is the number of lines (change as appropriate)

---

### Post by ymra on 2009-12-10
You could use wildcards.

[http://uw714doc.sco.com/en/SHL_automate/wildcard_characterss.html](http://uw714doc.sco.com/en/SHL_automate/wildcard_characterss.html)

---

### Post by weavertech89 on 2009-12-10
go to torrent downloads of the web like btjunkie.org, or others and download ubuntu book after download view it with PDF viewer and tells you everything you want to know. email me at [EMAIL="weavertech89@gmail.com"]weavertech89@gmail.com[/EMAIL] and I will send you a copy of the book through email. but LS-1 and LS-a and LS -1a does everything you wanted. type them in the terminal one at a time and test it to see.

---

### Post by RakeshSugirtharaj on 2009-12-10
> **DGortze380 said:**
> What do you mean by 'n' results?

results that start with the letter?
results that contain the letter 'n'?
n number of results?


Yes I meant 'n' number of results. Thanks for all the replies. Supersonic's reply was very helpful.

Is there a way to see the results in batches. For ex, if there are 100 results, can i see them in batches of 10?

---

