---
title: "Scripting sound file editor Audacity?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Mariane on 2009-01-15
Please, does anyone know if audacity can be scripted? 
I need to reduce the length of several sound files, 
so I would need something like:

for all files in this directory
{
 audacity open file
 audacity resize to float seconds
 audacity save newfile
}

It needs to be a float, I want files 3 seconds long, 
2.5 seconds long, etc. 

If it cannot be done, if you know another way to do 
it I'm opened to all suggestions. 

Mariane

---

### Post by petervk on 2009-02-04
Did you look at the man file for audacity?

in a terminal:
```
man audacity
```
you can scroll up and down with the arrow keys, and hit q to exit.

---

