---
title: "vim &amp; independent tab sizes"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by noorez on 2009-11-13
I found a website that describes a way to make code so that the coder can use the tab stop that he likes but when anyone else looks at this code, they can use the tab stop they prefer and still see the same code formatting.

[http://www.cebix.net/indentation.html](http://www.cebix.net/indentation.html)

Using this websites idea, how do we accomplish this in vim?

---

### Post by MadHatHost on 2009-11-13
Technically, it's already implemented in vim as long as you follow the standard and use the tab key in some places and the spacebar in others and don't have expandtab set in your vimrc. 

I, personally, have ```
set tabstop=4
``` in my .vimrc file and a co-worker has his at the default 8 character tab stops. So, when I open a file that he's been working on, I only get 4 spaces for the tab stop where he will get 8. 

However, I'm not a big fan of the tab character (some win progs seem to be tab unfriendly) so I also have ```
set expandtab
``` in my .vimrc so that tabs are expanded to spaces. That little bit counters the idea of the article, but it works for me. :-)

---

### Post by noorez on 2009-11-13
Not what I was quite going for I guess....

I tried putting tabstop=4 which is my preferences, but I was also looking for a setting which would help me get close to the article:

Tab characters are used exclusively for indentation;

class person
{
<TAB>string name;<spaces>//comment
<TAB>int i;<spaces......>//comment
}

So hitting the tab key for "alignment" purposes (ie comments) will insert spaces.

The reason is so that when someone 'cat's or 'less' my code, they see what I see. Or when i hand in an assignment for a class, I don't get dinged for having a messy style.

If there is another way to achieve the same effect then I'd be happy to hear it....

---

### Post by falconindy on 2009-11-13
I think you want 'set shiftwidth'.

---

### Post by noorez on 2009-11-14
Hmm...shiftwidth change the indentation size......

Thats still not quite what I was looking for.

According to that article, tabs should be used strictly for indentation.
For example in the following c++ code:

```

for(;;)
{
  int i;   //integer i
  int j;   //integer j
}

```

A tab should only be used to indent the lines inside the for loop, but spaces should be used for anything else in the line (i.e aligning the comments). Hitting the tab key after declaring the int will align to the proper column using only spaces.

Its described better in the link that I gave.

---

