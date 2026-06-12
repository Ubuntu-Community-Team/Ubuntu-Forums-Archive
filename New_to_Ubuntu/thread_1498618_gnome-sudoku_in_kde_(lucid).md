---
title: "gnome-sudoku in kde (lucid)"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-06-01
Recently converted ubuntu (lucid) into kubuntu. Also removed the gnome related packages. However, I love gnome-sudoku. Installed it via apt-get
```
sudo apt-get install gnome-sudoku
```which also installed some gnome related packages. Now typing "gnome-sudoku" in konsole it gives the following error and exits.
```

Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 67, in <module>
    start_game()
  File "/usr/lib/python2.6/dist-packages/gnome_sudoku/gnome_sudoku.py", line 21, in start_game
    import main
  File "/usr/lib/python2.6/dist-packages/gnome_sudoku/main.py", line 19, in <module>
    import printing
  File "/usr/lib/python2.6/dist-packages/gnome_sudoku/printing.py", line 5, in <module>
    from gtk_goodies import gconf_wrapper
  File "/usr/lib/python2.6/dist-packages/gnome_sudoku/gtk_goodies/gconf_wrapper.py", line 6, in <module>
    import gconf
ImportError: No module named gconf

```I know kde already has a package ksudoku. But I love the gnome version of sudoku more than the kde version. Is there any way gnome-sudoku can be run in kde4?

---

### Post by a.sarkar on 2010-06-01
Solved it. python-gconf package was missing.

```
sudo apt-get install gconf2 python-gconf
```Shouldn't "python-gconf" package be a dependent package of gnome-sudoku?

---

