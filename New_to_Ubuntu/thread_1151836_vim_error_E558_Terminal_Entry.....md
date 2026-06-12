---
title: "vim error: E558 Terminal Entry...."
date: 2009-05-07
forum: New to Ubuntu
---

### Post by thegeezer3 on 2009-05-07
When i first started using vim on the terminal all was fine. then i went and tried installing a plugin and it started spitting out all sorts of errors
E558: Terminal entry not found in terminfo
'gnome-256color' not known. Available builtin terminals are:
    builtin_gui
    builtin_riscos
    builtin_amiga
    builtin_beos-ansi
    builtin_ansi
    builtin_pcansi
    builtin_win32
    builtin_vt320
    builtin_vt52
    builtin_xterm
    builtin_iris-ansi
    builtin_debug
    builtin_dumb
defaulting to 'ansi'

i tried sudo apt-get remove vim and then sudo apt-get install vim
but the errors still come up.

How do i completely uninstall vim and any other files that its associated with in order to get a fresh install. After a while I also tinkered around in the .vim directory, manually deleting files in there in frustration - bad move probably. 

Can anyone help?

---

### Post by thegeezer3 on 2009-05-08
actually i didnt just delete a few files from the .vim directory i actually deleted the whole directory. Ive tried uninstalling and reinstalling but i cant seem to get that directory back. How do i get it back?

---

### Post by radirk on 2009-11-01
You might try

sudo apt-get install ncurses-term

See here for more info: [http://www.vim.org/scripts/script.php?script_id=2175](http://www.vim.org/scripts/script.php?script_id=2175)

---

