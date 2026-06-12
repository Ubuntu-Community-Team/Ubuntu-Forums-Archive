---
title: "side pane vanished on ubuntu karmic"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by lemured on 2011-04-02
Hello.

My side pane vanished now for the 2nd time, karmic, and different from the 1st time when it eventually re-appeared, it doesn't do so now and I won't trust this kind of waiting.
I did view postings to help with similar problems, but none of it worked. 
Going on 'view' and turning side pane off and then on again doesn't work, neither does trying f9.
We're talking about the side pane when using documents, etc., nothing on the desktop, and I do not want cairo. 
The side pane is not only of great usefulness for me but also need. 
Anyone knows anything, any idea?

Thank you in advance, and a lot....

   lemured

---

### Post by fooman on 2011-04-02
hi,  try pressing the alt + f2 keys.  that should open a run dialog box,  in the space, type: gconf-editor

and click on the "run" button.

when the editor opens,  click: apps > nautilus > preferences

scroll down the list on the right,  and make sure there is a check next to "start with sidebar"

if it is already checked,  then take a look at "sidebar width" (in the same directory) and make sure it is not set to "0"...if it is,  change it to something like 120 or 140.  close nautilus if it is open,  then reopen it after making the changes and see if that helps.

hope it does.  :)

---

### Post by lemured on 2011-04-03
fooman, you are a star!!!
it worked wonderfully, an avalanche fell from my heart!
Thank you so much :) :) :)
And have a lovely Sunday!

---

