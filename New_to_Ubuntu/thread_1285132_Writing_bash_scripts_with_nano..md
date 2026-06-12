---
title: "Writing bash scripts with nano."
date: 2009-10-07
forum: New to Ubuntu
---

### Post by furialis on 2009-10-07
I'm trying to teach myself bash scripting and I've run into a problem. I would like to do everything from the command line to write the script, which doesn't seem to be a problem.

I use nano to write something like

```

#!/bin/bash

echo 'My first bash script'
sleep 5

```

And name it first.sh

Then I do

```

chmod +x 755 first.sh

```

From the command line with

```

./first.sh

```

the script runs, and does what's expected.

However I cannot run the script by double clicking the icon on the desktop.

How can I make it double-clickable?

Thanks.

---

### Post by renkinjutsu on 2009-10-07
How did you make the icon?
make a folder in your home directory named 'bin' if there isn't one already there
```
mkdir ~/bin
```
then move first.sh into that folder

now go to the desktop and make a launcher, in the dropdown menu, select 'Application in terminal' and for command just enter first.sh or whatever it was called

putting it in your bin folder should've added your script into your PATH, so typing out the path to first.sh wouldn't be needed

---

### Post by furialis on 2009-10-07
I'm sorry for the confusion.

I'm actually using KDE. When I write out the file from nano, the icon was automagically created.

Do I have to move the file (icon) to get it to run?

---

### Post by renkinjutsu on 2009-10-07
i'm not sure how KDE works, but it's still a good idea to move your script into a bin folder

can you right click and modify the icon on your desktop?
change it to execute your script by typing 'first.sh' without the quotes.. because once put into your bin folder, it becomes a command in the terminal

---

### Post by wojox on 2009-10-07
Drop the .sh and try it so rename it to just first.

---

### Post by eeperson on 2009-10-07
Your script is probably already double-clickable you just can't see the output.  The output is being printed to the virtual terminal you are on but you can't see it because X is running. Your script  will have to open a terminal emulator such as konsole if you want to see the output.

---

### Post by furialis on 2009-10-07
I really hate to ask to be spoonfed, but what line would I add to the script to make it open a Konsole/terminal?

---

### Post by eeperson on 2009-10-08
Off the top of my head I think it would be something like (I'm not at a linux machine at the moment):
```
konsole -e echo 'My first bash script'
```
Although that might might pop up a Konsole window that closes immediately after the  echo command runs (meaning almost immediately).

---

