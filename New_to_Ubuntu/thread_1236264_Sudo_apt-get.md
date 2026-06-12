---
title: "Sudo apt-get"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by JustMegawatt on 2009-08-10
Frustrating, I've installed Ruby on Rails using the sudo apt-get command in the terminal, yet I don't know where the file went. Any help?

---

### Post by Soul-Sing on 2009-08-10
Is this offic. documentation helpful? : [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by JustMegawatt on 2009-08-10
Thank you, you also solved my problem on apache.

For others with the same problem, here is the solution:

To run something, simply type in the file name in the terminal.
Such as 
```
Firefox
```And that would run firefox

For ruby, it was rails, so I had to type in ```
rails
``` to run it.

To run a specific file using a program, use the program name as first, then the file location/name of file. Such as

```
Firefox ~/desktop/website/index.html
```You can use ~ as a shortcut instead of typing in File System/home/username/desktop/website/index.html

Also, the most helpful thing was just to drag the file into the terminal instead of typing it all up. Like if I wanted to use Firefox to open the file ~/desktop/longfilenamesuperverylongfilename/evenlongerfilename/superlonger/whatever/random.html , I could type in 

```
firefox '~/desktop/longfilenamesuperverylongfilename/evenlongerfilename/superlonger/whatever/random.html'
```or I could just open the file in the desktop, then drag it into the terminal. It would do the same thing, but I would have to do less typing.

Edit: I cannot believe that took more than 50 minutes to figure out.

---

