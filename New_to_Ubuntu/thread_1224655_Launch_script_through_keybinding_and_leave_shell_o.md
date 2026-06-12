---
title: "Launch script through keybinding and leave shell open"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by worldsayshi on 2009-07-27
I've added a keybinding through the use of gconf-editor wich executes a shell script. But I don't know how to get the script (or the keycommand) to leave open (or launch in the first place) a shell so that I can read the output.
I do this to be able to test a python script while I am working on it and to be able to read the error messages.  
I write something like this in a script:
```

python /home/myname/pyfolder/pyscript.py
read

```

and bind ```
bash script/path/script.sh
``` to a keybinding.

How can I make the keybound script to launch in a shell so that I can get the error messages?

---

### Post by worldsayshi on 2009-07-28
Solved it!

the shell script:
```
python /home/myname/pyfolder/pyscript.py
read
```

Then, in gconf-editor, I added a keycommand executing:
```
gnome-terminal --command="bash /home/myname/somescriptfolder/myscript.sh"
```

On hitting the key combination it gives me a terminal that executes the python script and then stays open after the python program is closed, to allow me to read error messages. All I have to do to close the window is to hit return. Perfect for python development without using an IDE?

I also tryed to surpass the need for a script by just binding the keys to:
```
gnome-terminal --command="python /home/myname/pyfolder/pyscript.py;read"

```
This wouldn't work though, anyone know why?

---

### Post by llamabr on 2009-07-28
well done.

---

