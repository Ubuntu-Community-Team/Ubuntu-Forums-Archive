---
title: "Emacs question"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-15
Hi I am using EMacs 23 on ubuntu 10.04. Is there any way to open any text file in emacs in the READ ONLY mode through the terminal. 

I know that after opening a text file in emacs I can use the key combination C-x C-q to put it in read only mode. But I want the read only mode to be 'on' the moment my emacs window opens. Is there any terminal command for that?

---

### Post by Zorgoth on 2010-08-16
emacs --funcall toggle-read-only

---

### Post by gaurish108 on 2010-08-16
That works thanks....but it is too long a command....could there be any shorter command.... This is the lazy side of me speaking :)

---

### Post by rtlustyo on 2010-08-16
You can make your own command. In your root directory, open a file called .bashrc in an editor. Below is an example for a command called "emacsread", simply add this line to your bashrc


alias emacsread="emacs --funcall toggle-read-only" 

save it, and restart your terminal. You should be good to go. Now you can just type emacsread and it will automatically enter the full command for you.

---

### Post by gaurish108 on 2010-08-16
Oh thats nice! But I had a small difficulty

Say I have a file named foo.txt and I want to open it in read only mode.

Then I found I need to sandwich the name 'foo.txt' between **emacs** and

**--funcall toggle-read-only** for the command to work. 

Note that placing foo.txt at the end of the string emacs **--funcall toggle-read-only** does not work and opens foo.txt in normal mode. 

How should I modify what you just posted and put it in my .bashrc file?

---

### Post by Zorgoth on 2010-08-16
I was bored, so I solved your "problem." :D

Make a file called emacs-ro, make it executable (chmod +x path/to/emacs-ro), and put it somewhere in your $PATH, e.g. /usr/bin


The file should have these contents:
```

#!/bin/bash
argnumber=$BASH_ARGC
arglist=''
while [[ $argnumber > 0 ]] 
do
    argnumber=$(( argnumber - 1 ))
    arglist=$arglist\ `echo ${BASH_ARGV[argnumber]} | sed 's/ /\\ /g'`
done
arglist="$arglist --funcall toggle-read-only"
emacs$arglist

```


All this script does is take the list of arguments it receives and call emacs with that list of arguments followed by --funcall toggle-read-only.  It does *not* treat arguments with spaces in them correctly, for reasons that I cannot fathom.  Has something to do with the inconsistent way bash passes arguments when doing parameter expansions.

But for example, "emacs-ro -nw" should work fine.

Hope that works for you!

---

### Post by gaurish108 on 2010-08-16
Hats off bro!!!, this worked perfectly! Thanks a lot!

---

### Post by Zorgoth on 2010-08-16
A better and just slightly shorter script:

#!/bin/bash
emacs "$@" --funcall toggle-read-only

:lolflag:

Courtesy of Programming Talk post about arguments with spaces.  This one will handle those correctly, and is obviously shorter.

---

