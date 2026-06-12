---
title: "line number count in terminal"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by studybuddy09 on 2009-11-08
How do i get the line number count to appear in the terminal screen at the bottom right corner?.. as it becomes really tough while compiling the codes without knowing which line the error is at..

---

### Post by stderr on 2009-11-08
Normally javac/gcc will give line numbers for any errors (which aren't always correct in terms of where the problem actually lies), and then you can just jump to that line in your text editor of choice. For example, I use the command line text editor vim, so all I need to do is open the file (vim myfile.c) and enter (:502) or whatever the line number is, and I'm right there. Or if you prefer GUI text editors, gedit shows you the current line number on the status bar on the bottom, and Ctrl+I will take you to a specific line.

Maybe I'm not quite understanding your problem correctly: what language are you coding in, and which compiler are you using? edit: and which text editor are you using?

---

### Post by studybuddy09 on 2009-11-08
Thanks for your reply, but i did not understand what u said.
What does vimmyfile.c do?I write codes in c language,using gcc compiler.Generally i write them in the terminal and not in gedit .So how do i get the line no. count to appear in the terminal??

---

### Post by Matt__ on 2009-11-08
do you mean numbering each line?
```
cat <filename> -n
```

Hope im not being obtuse but I cant think of a way or reason to list total at bottom right of terminal.

---

### Post by falconindy on 2009-11-08
> **studybuddy09 said:**
> Thanks for your reply, but i did not understand what u said.
What does vimmyfile.c do?I write codes in c language,using gcc compiler.Generally i write them in the terminal and not in gedit .So how do i get the line no. count to appear in the terminal??
Vim is a terminal based text editor (the only, as far as I'm concerned). I guess that means you're using Nano? You can use Alt-G to go to a specific line number and you can use Ctrl-C to see what your current position is.

---

### Post by stderr on 2009-11-08
Ok, but what are you using to write your source code? I.e. which of the following (or another method: and source.c in the following is just the example of a source code file you may be trying to edit):

```
$ nano source.c  #Nano text editor
$ vim source.c  #Vim text editor
$ pico source.c  #Pico text editor
$ emacs source.c  #Emacs text editor
$ cat >> source.c  #Appending text directly
  my text
  ^D

```

"vim myfile.c" was an example of opening a source file in the popular Vim terminal text editor.

I'm still trying to understand what you want to display line numbers. Are you talking about line numbers for your source code? In which case you should probably use a text editor such as in the above list. Or if you're just reading through source code and not editing it, maybe you want (cat -n source.c).

---

### Post by studybuddy09 on 2009-11-08
Yes, i use vim to write codes and i am talking about line numbers for the source code.
But i want them in the command line terminal and not in the gedit text editor(in which it already displays the line nos.). 
The cat<filename> -n cmd worked, but it prints the code along with the line nos.
I want the line nos. to appear simultaneously while typing the code.
Hope im clear!!

---

### Post by stderr on 2009-11-08
Now I see what you want: line numbering in edit mode in vim.

I'm not sure how to achieve this (but I'm sure you can). However, in the meantime, you can use these shortcuts to speed things up:

Open a file with cursor at line number 13:

```
vim +13 source.c
```

Navigate to line number 13 when inside vim (but not in edit mode; hit Escape if you are in edit mode):

```
:13
```

edit: Turns out it's pretty easy. You can set this in your ~/.vimrc file, or just enter it each time:

Enable line numbering when inside vim (but not in edit mode; hit Escape if you are in edit mode):

```
:set number
```

---

### Post by issih on 2009-11-08
Don't use vi/vim personally, but this is what google says:

[http://www.tech-recipes.com/rx/402/show-line-numbers-in-vi-or-vim/](http://www.tech-recipes.com/rx/402/show-line-numbers-in-vi-or-vim/)

Hope that helps

---

### Post by studybuddy09 on 2009-11-08
The set number command worked!!
Thanks a lot for all your help!!

---

