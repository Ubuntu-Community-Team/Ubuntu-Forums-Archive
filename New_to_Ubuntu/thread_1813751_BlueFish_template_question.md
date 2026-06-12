---
title: "BlueFish template question"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by kompotas on 2011-07-28
Hey guys, 
Maybe some of you are Blue fish editor veterans/experts and could answer one question for me. Well I've looked at the html editor comparison charts found at wikipedia [http://en.wikipedia.org/wiki/Comparison_of_HTML_editors](http://en.wikipedia.org/wiki/Comparison_of_HTML_editors) And noticed that just like Only a couple of editors have function "Templates Update Sync" (Dreamweaver, Bluefish and two more). Well I have spent a lot of time working with DW and it was pretty simple and usefull thing. When You start a new project, you build your self a template with all the dropdown menus and side bars and add editable areas. And when you write a new story you just use "new page from template" function and fill the editable area. But the most usefull thing was after some time when you want to edit lets say the drop down menu , add some more links and so on, you do it in template and when you save it, it automatically updates all the pages that were made from it. 

Now here is the question, does BlueFish really have such a function ? If I understand what wikipedia charts say correctly "Templates Update Sync[[IMG]http://bits.wikimedia.org/skins-1.17/common/images/sort_none.gif[/IMG]]("http://en.wikipedia.org/wiki/Comparison_of_HTML_editors#")" is exactly it.

So if it does can someone please explain it in a decent detail.

Thank you for any reply.
Arnas.

---

### Post by kompotas on 2011-07-29
anyone ? :) please people :)

---

### Post by kompotas on 2011-08-02
Okay, just for the last time :) Maybe someone who knows is around right now :)

---

### Post by bodhi.zazen on 2011-08-02
Sorry no one knows the answer, perhaps ask on the bluefish mailing list ?

Personally I use php to include such things.

So write a menu (navigation) in a separate file and include it with php.

Example:

<nav>
        <?php include ('menu.html'); ?>

</nav>

Easier to maintain a separate menu.html then re-writing a menu on each and every web page. Editing a single file -> updates all web pages.

You can use other tools (other then php) as well.

---

### Post by kompotas on 2011-08-04
Thanks man, I guess I'll try to learn php. never used it before.

---

### Post by bodhi.zazen on 2011-08-04
> **kompotas said:**
> Thanks man, I guess I'll try to learn php. never used it before.

I think you will find the "one liner" I showed you is very handy.

It greatly simplifies management of common content across your web pages.

Another tool worth learning (perhaps), at least a little is javascript / ajax.

---

