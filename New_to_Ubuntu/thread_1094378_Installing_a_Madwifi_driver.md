---
title: "Installing a Madwifi driver"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Amani.S on 2009-03-12
Hello ,
I have a problem with my wireless , and I was installing a madwifi driver
I searched for what to do and found this :

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

All this is good , but when I reach compiling package and type "make"(without quotes) in terminal it shows :
make: *** No targets specified and no makefile found.  Stop.
Any help ??

---

### Post by avtolle on 2009-03-12
Did you change directories to the one containing the extracted file?

---

### Post by Amani.S on 2009-03-12
I didn't do any thing but those mentioned in the page.
And if I have to do what you mentioned , could you please tell me what to do exactly , or what to type in terminal.

Thank You :)

---

### Post by avtolle on 2009-03-12
What I am asking is whether you did the command beginning ```
cd madwifi.......
```as set out in the how-to you are following. If you did everything that was in the how-to, you did it.

---

### Post by Amani.S on 2009-03-12
Actually I didn't notice that when I type :

cd madwifi-hal-0.10.5.6-r3879-20081204

it shows :
No such file or directory .

---

### Post by avtolle on 2009-03-12
What happens in the terminal when you type ```
cd madwifi
```then use the TAB key to autocomplete? I'm wondering if there has been some change in the name of the files within the tarball which makes the text in the how-to obsolete.

---

### Post by avtolle on 2009-03-12
To try to be a bit more clear; the tarball dowloaded has the name *****current; thus, the directory created when extracting from the tarball could well have a different name from that given in the how-to. Using the autocomplete feature in the terminal by pressing the TAB key will get you the correct directory, even though the name has (likely) changed.

---

