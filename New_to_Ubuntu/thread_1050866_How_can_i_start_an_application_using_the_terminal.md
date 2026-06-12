---
title: "How can i start an application using the terminal?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by harrkou on 2009-01-26
I m trying to start applications (for example the calculator) using the terminal but i must be doing something wrong... I type "./calculator" or simply "calculator" but terminal shows syntax error.Can some1 help me plz ?

---

### Post by meho_r on 2009-01-26
Try entering **gcalctool**. Some apps have different names from what is expected (calculator is an example). But many are started just as it's expected. I.e. Pidgin is started with **pidgin**, Gimp with **gimp** etc.

---

### Post by Joeb454 on 2009-01-26
the ./ tells the terminal to look for the program in your current directory, which I'm assuming the calculator isn't ;)

You have to know the correct program name to run things from the terminal.

---

### Post by mcduck on 2009-01-26
Just enter the name of the program.

The hard thing is that the name of the program isn't always what you see in Gnome's menu, for example Gnome's calculator is "gnome-calculator". If you don't know the name of a program you can search for with the "apropos"-command; for example "apropos calculator" will list a couple of available calculator applications.

---

### Post by harrkou on 2009-01-26
Oh now i get it! Thx a lot!!!!

---

### Post by meho_r on 2009-01-26
And you can even use Alt+F2 and then start entering a guessed name of the program and after first two-three letters entered you'll get some associations in the lower part of the window. Just click the program you intended and you'll see its name appears ;) Try it with "calculator": when you start typing, you'll notice in the lower part something like "Calculator", "OpenOffice Spreadsheet" or more. Click on "Calculator" and you'll get its name.

---

### Post by blueridgedog on 2009-01-26
You can also append an & at the end of the command so that it spawns it as a new process, leaving the terminal free to be closed or to do other things.
```

 gcalctool &
```

---

