---
title: "Advice on website collaboration for Kubuntu users"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-12-02
Hi, all:

I have a question on tools for website design collaboration I need to "forum source".  

I am designing a site with one other person.  He and I both use Kubuntu (he's a bit more new to *Buntu than me).  

I am the frontend and he's the back.  I speak HTML and a smidge of CSS.  He speaks PHP.  I'm doing all the graphic design, copy, and essentially everything you "see".  He's doing the scripting and DB design/hookup.  

I use Kompozer (so I can do about 1/3 source, 1/3 tags, 1/3 WYSIWYG); he writes his PHP hard core.  We've already had one accident where I downloaded a page with the extension .php; converted it to html, did some more design stuff on it, changed it back to php and re-upped it to the server.  Unfortunately, just before I did that, he'd upped the same page with lots of php changes, and we lost his code.  

Kompozer isn't a WYSIWYG php editor.  Even if it was, we'd still have the problem of overwriting each other's code.  

Does anyone have any suggestions?  It's a big site, I'm typically doing design work on 5-6 pages at once, and it's impractical for us to be constantly updating each other on which pages we're working on.  In addition, I lose his PHP updates when I convert to HTML to work on the design aspect in Kompozer.  

We're both using Kubuntu; does anyone have any suggestions on how we can work more efficiently?  Ideas, *ware, whatever.  (comments about how I need to learn php are stipulated ;-) )

Thanks, all!
Tarah

---

### Post by Achetar on 2008-12-02
I use Mercurial (like Bazaar or Subversion) to handle this. Then again I have physical access to the server and can install anything I want on there. But Merc (or Bzr, or SVN) will keep the differences between file uploads to prevent such accidents as you described. That's the main reason I use it.

---

### Post by kernelhaxor on 2008-12-02
SVN (subversion), a version control system .. I too was a part of a large team working on a single website .. SVN worked like a charm .. It offers other advantages too

---

