---
title: "Firefox's URL/address bar does'nt recognize the plus sign [+]"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by hanzj on 2010-02-21
Hello,
I sometimes have to put a plus sign in my Firefox URL/address bar.

For example, I have a "keyword search' for google. And I make use of Google's built-in calculator.

So in my firefox bar, I type in 
```
g 8+2
``` and then hit enter.
What I get is turned into this URL
> [http://www.google.com/search?hl=en&q=8+2](http://www.google.com/search?hl=en&q=8+2)
and Google interprets my entry as
> 8 2

This is puzzling. 

I noticed that my Chromium Browser the same input into this URL
```
http://www.google.com/search?hl=en&q=8%2B2
```
This correctly is interpreted by Google as
> 8+2


So based on this little experiment, I've concluded that ```
+
``` can't be understood by Google unless it's changed into ```
%2B
```.

How can I make Firefox do this change?


P.S.  In Firefox, if I go to google.com first and then enter
> 8+2 Google understands the plus sign.

P.P.S. This isn't a Google problem. My "keyword search" with WolframAlpha.com also gives the same problem.

P.P.S. In Firefox, the other mathematical symbols, for example:
minus sign **-**
 times sign **x **or** ***
divided by sign **/**
are interpreted correctly.

---

### Post by ankspo71 on 2010-02-21
Hi,
I haven't noticed this before, but I see it isn't working now. The search bar using the Google search engine works for me  though.

---

### Post by hanzj on 2010-02-25
bump.

---

### Post by johngreth on 2010-02-25
This is because google interperets the + in the address bar as a space. Google chrome is smart enough to know that you want the search to include a + symbol and changes it. Firefox may have a plugin/addon that will change it automatically like chrome does, but I've never seen one.

---

### Post by hanzj on 2010-02-25
johngreth,
thank you for the reply. hope to get this to the attention of mozilla/firefox developers

---

### Post by Sir Jasper on 2010-02-25
Hi,

Can you not do as pointed to by the red arrow in the picture below?

[[img]http://f.imagehost.org/t/0741/FF_calc.jpg[/img]](http://f.imagehost.org/view/0741/FF_calc)

I seem to recall reading that it is also possible to calculate using the terminal, as well as other tricks such as  typing  cal 2010 as I have not seen a ´buntu year-at-view calendar program.

My regards

PS Try using the Firefox shortcut Ctrl+k  then type your calculaion.  The final result (and intermediate results, if any) should appear under the box so there is no need to even press Return.

---

### Post by hanzj on 2010-02-26
sir jasper,

Thanks for your comment.

The plus sign works in the Search engine bar (as your red arrow points to). But I:
1. have removed/hidden the search engine bar from view
2. expect the main location bar to work just as well as the search engine bar. 


Calculations can be done in terminal. But:
1. I prefer to do my calculations in the browser
2. i also have WolframAlpha.com (hereafter W|A) as a keyword search and W|A is more comfortable for me to use than terminal.

---

### Post by Sir Jasper on 2010-02-26
Hi,

[COLOR="White"]I am using the facilities available[/COLOR], but you have chosen not to.
That is fine, but[COLOR="White"] do not then complain[/COLOR].

My regards

---

### Post by hanzj on 2010-03-06
bump. this must be a bug, mustn't it?

---

### Post by johngreth on 2010-03-06
I would call it a lack of functionality rather than a bug. You could try going to Help->Report a problem. I don't know if that's the right place to report it, but I don't know of anywhere else.

---

### Post by gvoima on 2010-03-06
Firefox does not contain an Omnibox like feature that Chrome does, therefore the g-letter before the query you put there, it gets interpreted as a search for "g 8+2".
If you put just 8+2 in the address bar, it works.

i.e. use an add-on to get such Chrome like features (I don't know any atm.) or use Chrome :)

Hope that helps.

---

### Post by Sir Jasper on 2010-03-06
Hi,

My comment above is written in black and white.

You choose not to use the simple answer and you think
things should be re-written to suit your personal needs.

Fine, but tell the developer, not us.

My regards

---

### Post by hanzj on 2010-03-06
gvoima,
Nice! I didn't know that I didn't have to put a "g" before the equation. But still my Wolfram|Alpha keyword search is still not functional. Is there a way to make a keyword-**less** search use WolframAlpha, and not google?

---

### Post by gvoima on 2010-03-10
I'm not sure about that, sorry :-(

---

### Post by minsookim1398 on 2011-03-28
Updated Firefox 4.0 seems to have addressed this issue. Case closed. :popcorn:

---

