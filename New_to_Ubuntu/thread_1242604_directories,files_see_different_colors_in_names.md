---
title: "directories,files see different colors in names"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by chris1950 on 2009-08-17
when I did the command ( ls) I have seen directory names in different colors - Red, Green, Blue. Can someone tell me what they mean or where can I find out what these colors mean?

---

### Post by tarps87 on 2009-08-17
They relate the file type, buy default the colours are blue = directory, black = file cyran = link.
They also relate to permissions and can very between themes.

Try using ls -l

You will see something like this:

[COLOR="Red"]l[/COLOR][COLOR="Blue"]rwxrwxrwx[/COLOR]   1 root root    30 2009-04-28 14:40 vmlinuz

[COLOR="Red"]l[/COLOR] = type (l = link, d = directory, - = file)

[COLOR="Blue"]rwxrwxrwx[/COLOR] = permssions

1st three = user/ owner
2nd three = group
3rd three = other

r = read
w = write
x = execute

Edit:

some more info
[http://wiki.linuxquestions.org/wiki/Ls](http://wiki.linuxquestions.org/wiki/Ls)

---

### Post by Paddy Landau on 2009-08-17
I have an answer, but sorry, it's not straightforward.

Enter the command [COLOR=DarkRed]man ls[/COLOR] to see the instructions. Search for 'color'. You'll find that it refers to [COLOR=DarkRed]dircolor[/COLOR].

Enter the command [COLOR=DarkRed]man dircolor[/COLOR] to see the instructions for [COLOR=DarkRed]dircolor[/COLOR]. You'll see that it refers to the [COLOR=DarkRed]--print-database[/COLOR] option.

Enter the command [COLOR=DarkRed]dircolor --print-database[/COLOR] to see the list of colours.

All you need now is to decode the codes for the ANSI colour scheme (e.g. [COLOR=DarkRed]01;35[/COLOR] means magenta).

[http://rrbrandt.comli.com/docs/tut/redes/ansi.php](http://rrbrandt.comli.com/docs/tut/redes/ansi.php)
[http://www.termsys.demon.co.uk/vtansi.htm](http://www.termsys.demon.co.uk/vtansi.htm)
[http://en.wikipedia.org/wiki/ANSI_escape_code](http://en.wikipedia.org/wiki/ANSI_escape_code)

Good luck!

---

### Post by chris1950 on 2009-08-18
I am refering to the Directory name colors - I had problems accessing one and when I changed permissions the color changed. What I wanted to know was what each color means/stands for. Where can I get this information.

---

### Post by lloyd_b on 2009-08-18
> **chris1950 said:**
> I am refering to the Directory name colors - I had problems accessing one and when I changed permissions the color changed. What I wanted to know was what each color means/stands for. Where can I get this information.

Take a look [here]("http://blog.alexrybicki.com/2009/03/bash-ls-color-meaning.html").  If you run the script from that page, it will show you the color setup for every type of file that "ls" recognizes and displays in color.

Lloyd B.

---

### Post by chris1950 on 2009-08-18
Thanks, just what I was looking for.

---

