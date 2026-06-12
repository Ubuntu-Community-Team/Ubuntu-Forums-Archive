---
title: "vi Editor in Terminal Mode"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by J-Logger on 2011-01-31
Hello,

I am relatively new to Ubuntu.  I have had it installed for a few years but only now find the time to actually try to use it fully.

In the early 90's, I was doing some engineering work on IBM RS6000 devices.  At that time, I learned some rudimentary editor commands that one could use on the command line in the terminal window.  For instance, if you were entering several similar commands at once that varied only by a couple keystrokes, you could use these editor commands (that worked a lot like the vi editor) to manipulate the command line.  

I have searched this forum in various ways and could not find it.

Can anyone point to a reference that might show me how to do something similar in the ubuntu terminal window?

Thanks

Jim

---

### Post by freak42 on 2011-01-31
I am not sure I understand your request correctly, maybe you can elaborate your problem or make an example?

Anyhow one thing that comes to mind is the wildcard operators that allow for one type of command to be used for multiple files, e.g.

cp *.avi somewhere/else/

will copy all files that end in .avi to the new destination...

I guess it's not what you wanted (as I don't see the relation to vi), however I thought why not give it a try.

hth

---

### Post by Nickjpost on 2011-01-31
Type 
 
**vimtutor**
 
in your terminal, though you may have to install vim-runtime via command   
 
**sudo apt-get install vim-runtime**
 
Then retype
 
**vimtutorial**
 
This command will bring a nifty learning experience on using the vi-editor

---

### Post by nothingspecial on 2011-01-31
Type ```
set -o vi
```

Then to get into vi mode press escape

here is a cheat sheet

[http://www.scribd.com/doc/985243/Bash-VI-Editing-Mode-readline-Cheat-Sheet](http://www.scribd.com/doc/985243/Bash-VI-Editing-Mode-readline-Cheat-Sheet)

---

