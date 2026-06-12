---
title: "# include&lt;conio.h&gt; --- c prog"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-18
i am getting error for this in gcc..

i want this for > clrscr(); and getch();

any idea ?

and why does gcc make me to type ```
int main() instead of void main()
```

---

### Post by coka on 2009-02-18
i think (not quite sure) gcc provide a facility to interact with surroundings by returning a value which is type of int .
Edit:
are u able to include conio.h i think it is not in gcc.
and also u need not to use getch() or clrscr() both are useless in gcc.

---

### Post by kaizan on 2009-02-18
Hi Kimikrishna,

conio.h is, if i recall correctly, a header file used in MS-DOS programming .. it's not something that you'll be able to use in Linux.

This seemed quite helpful for implementing a getch() equivalent:

[http://cboard.cprogramming.com/archive/index.php/t-27714.html](http://cboard.cprogramming.com/archive/index.php/t-27714.html)

I thiiiiiiiiiiink - but it's been a while - you can either do a:

system("clear");

to clear the screen in a linux terminal or maybe use the curses library?:

[http://invisible-island.net/ncurses/ncurses-intro.html](http://invisible-island.net/ncurses/ncurses-intro.html)

Hope this helps!
Cheers
kaizan

---

### Post by cmay on 2009-02-18
this function is borland specific. its way back to old turbo c++ on dos. the post above is correct and also provides a link to the standard in linux wiht the  ncurses library.

edit:
there is a progtramming talk section here on the forums which you can ask these things. good luck .)

---

### Post by albandy on 2009-02-18
conio.h is not ansi-c standard

you've to type int main() because void main() was deprecated. 

int main()
{
int state;
/* your code */



return state;
}

you can use ncurses
if you speak spanish you can read this manual: [http://ditec.um.es/~piernas/manpages-es/otros/tutorial-ncurses.html](http://ditec.um.es/~piernas/manpages-es/otros/tutorial-ncurses.html)

or you can browse for ncurses and C examples

---

