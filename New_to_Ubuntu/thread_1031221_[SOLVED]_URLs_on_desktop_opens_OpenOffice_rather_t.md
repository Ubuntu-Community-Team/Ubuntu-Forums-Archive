---
title: "[SOLVED] URLs on desktop opens OpenOffice rather than FireFox"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by cwmoser on 2009-01-05
I have some URL's that I put on the desktop by dragging from FireFox. Until yesterday, I was able to just double click on them and FireFox would launch.

Now, when I double click on them, Open Office Writer starts up.  There is no "Open With" file association for URL links.  Is there a work around?

Carl

---

### Post by RomeReactor on 2009-01-05
Hi. If these are text files, right-click on one, select "Properties", go to the "Open With" tab, and make sure Firefox is selected.

---

### Post by cwmoser on 2009-01-05
Its kinda hard to see unless you actually try it.

Start FireFox and go to some site - say [www.yahoo.com](www.yahoo.com).  Highlight the URL in the address field and drag and drop it to the desktop.  Then right click on it and you will see that there are no Open With tabs.

If you double click on what you dragged to the desktop, yours might utilize FireFox.  In my case, Open Office Writer starts up instead.

Carl

---

### Post by RomeReactor on 2009-01-05
In my case, dragging a url from the address bar results in a .txt file in the desktop; however, dragging links *inside* a web page does result in a "Link to www.blah.com" file, which does open in Firefox and doesn't have an "Open With" tab in its properties. So I'm guessing the latter is the problem for you.

Have you tried deleting or moving the **.mozilla** folder in your home directory to see if it works then? Note that you'll likely have to install Flash again if you do so.

---

### Post by cwmoser on 2009-01-06
I found the solution to this problem.  

I located two files - one with a .htm extension and the other with a .html extension.  For each, I right clicked and selected **Open With -> Open with Other Application**.  Then selected **Firefox Web Browser** and pressed **Open**

Then when I double click on a URL-based Icon on the desktop Firefox rather than Open Office cranks up.

Carl

---

