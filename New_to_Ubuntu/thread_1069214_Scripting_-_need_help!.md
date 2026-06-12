---
title: "Scripting - need help!"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Fizwidget on 2009-02-13
Complete noob here. I have a very basic understanding of the terminal, and I've only just started messing around with scripts. Here's what I'm trying to do: create a script that will open a terminal window, say "UNIX time", and then display the UNIX time (in seconds) updating once per second. Here's what I have so far:

```
#!/bin/bash
echo UNIX time
watch -n 1 date +%s
```

The last line works correctly, but the middle line does not work, and I don't know why! If I type "echo UNIX time" into the terminal, it echoes "UNIX time". When I put this exact same command into a script though, it seems to be ignored.

Also, this script doesn't appear to do anything if it is executed from the GUI. How can I make it so that when I double-click it in nautilus, a terminal window will open that executes the script?

Thanks!

---

### Post by bodhi.zazen on 2009-02-13
It is the space.

echo "UNIX time"

See also :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by Fizwidget on 2009-02-13
Sorry, I'm not quite sure what you mean. Which space? I have now tried...

echo UNIX time
echo UNIXtime
echo "UNIX time"

None of them work when executing the script, but all of them work when I enter them into the terminal.

---

### Post by geirha on 2009-02-13
The problem is the watch command. It clears the terminal window every second, so you'll need watch to display that string. Try:
```
watch -n 1 "echo UNIX time; date +%s"
```

---

### Post by Fizwidget on 2009-02-13
Thanks geirha, that got it working :)

So, what exactly was happening with my origional script? The echo was displaying for a split-second, then being wiped by the watch command? I assume scripts are executed from top to bottom...?

Also, does anyone know how to make a terminal window popup and run the script when I open the script from the GUI?

Thanks!

---

### Post by mrbiggbrain on 2009-02-13
> **Fizwidget said:**
> Thanks geirha, that got it working :)

So, what exactly was happening with my origional script? The echo was displaying for a split-second, then being wiped by the watch command? I assume scripts are executed from top to bottom...?

Also, does anyone know how to make a terminal window popup and run the script when I open the script from the GUI?

Thanks!

yes similar to in c++

while(1)
{
    cout << "hello world"
    SYSTEM("cls")
}

the screen is imidiatly cleared of all text. depending on the speed of the system, the amount of text, ect ect, then it can be either seen for a slipt second or not at all. if you ran it on a slow anough pc (I MEAN a calulator) then youd see it, but not on a regualr pc

---

### Post by mc4man on 2009-02-13
> Also, does anyone know how to make a terminal window popup and run the script when I open the script from the GUI?

I would be curious if one could do that( might help me see how to have a nautilus script open a visible terminal and then run a command

Otherwise just make a desktop launcher where the command is the location of your script (using 'Type:' 'Application in Terminal'

If the script was in your home folder then the command would be ./scriptname

If you drag the launcher to top or bottom panel it just becomes a little icon. You could use a little clock icon or something

---

### Post by geirha on 2009-02-14
> **mc4man said:**
> I would be curious if one could do that( might help me see how to have a nautilus script open a visible terminal and then run a command

If you put a line like this in such a nautilus script, it should open a gnome-terminal and start bash inside it with the two commands date and read. The terminal will close as soon as the commands have completed, so you'll need something like a read at the end. read will wait for the user to hit enter. 
```

gnome-terminal -x bash -c "date;read" &

```

---

