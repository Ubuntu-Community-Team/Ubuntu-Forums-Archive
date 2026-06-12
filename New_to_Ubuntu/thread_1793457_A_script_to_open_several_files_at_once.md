---
title: "A script to open several files at once"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by spacon08 on 2011-06-29
Hi,

I'm new to Linux and Ubuntu. Hence, very new to scripting. I would like to create a script when run will open several files at once (and perhaps if possible arrange the files on different workspaces and/or in an orderly arrangement on a single workspace). I assume any such script could function on any UNIX like OS as I would like to be able to use the same script at work where I use Solaris. I've searched on the forums but my search came up empty. Thanks in advance.

---

### Post by nothingspecial on 2011-06-29
What do you mean " arrange the files on different workspaces"?

Do you mean, have different applications open on different desktops?

scripts do not run on "Desktop"

""""well, they can..... but I doubt that is what you mean"""""

Do you mean open multiple text files to open on a single workspace? arranged in a specific order?

Please elaborate. :)

---

### Post by furtypajohn on 2011-06-29
The script below will open a list of files that you can define. As for moving them to another workspace, you should look into a tool called "xdotool"

sudo apt-get install xdotool

With xdotool you can script key presses like so:

xdotool key Ctrl+Alt+Left
xdotool key Ctrl+Alt+Right

This will allow you to move to issue any key press (such as Ctrl+Alt+Left to move to the left workspace) in a script. Once you change to the workspace of your choice you can then open the file there.

(Note: be sure to make the script below executable with: chmod u+x ./scriptName )

#!/bin/bash
# Define all your files below separated by spaces
files="file1.txt file2.txt file3.txt file4.txt"

for file in $files
do
    if [ -f "$file" ]; then
        gedit $file
    else
        echo "Could not open file [$file]"
    fi
done

-fpj

---

### Post by spacon08 on 2011-06-29
> **nothingspecial said:**
> What do you mean " arrange the files on different workspaces"?

Do you mean, have different applications open on different desktops?

scripts do not run on "Desktop"

""""well, they can..... but I doubt that is what you mean"""""

Do you mean open multiple text files to open on a single workspace? arranged in a specific order?

Please elaborate. :)

Apologies, for the confusion. I used the words desktop and workspace interchangeably as particularly at work they are referred to as workspaces. With regards running the script, I meant from the command line but I could also create a launcher on the desktop to that would run the script when clicked.

In regards to your final questions, the answer are YES in certain cases that may be desirable. Thanks for your time.

---

### Post by spacon08 on 2011-06-29
> **furtypajohn said:**
> The script below will open a list of files that you can define. As for moving them to another workspace, you should look into a tool called "xdotool"

sudo apt-get install xdotool

With xdotool you can script key presses like so:

xdotool key Ctrl+Alt+Left
xdotool key Ctrl+Alt+Right

This will allow you to move to issue any key press (such as Ctrl+Alt+Left to move to the left workspace) in a script. Once you change to the workspace of your choice you can then open the file there.

(Note: be sure to make the script below executable with: chmod u+x ./scriptName )

#!/bin/bash
# Define all your files below separated by spaces
files="file1.txt file2.txt file3.txt file4.txt"

for file in $files
do
    if [ -f "$file" ]; then
        gedit $file
    else
        echo "Could not open file [$file]"
    fi
done

-fpj


Thanks for the sample script and xdotool tip. I'll try this script out and let you know if it has the desired effect. Thanks for your time.

---

### Post by nothingspecial on 2011-06-29
> **spacon08 said:**
> Apologies, for the confusion. I used the words desktop and workspace interchangeably as particularly at work they are referred to as workspaces. With regards running the script, I meant from the command line but I could also create a launcher on the desktop to that would run the script when clicked.

In regards to your final questions, the answer are YES in certain cases that may be desirable. Thanks for your time.

Ok :)

Sorry, one more question.......

graphical, or command line "apps"?

---

### Post by spacon08 on 2011-06-30
> **nothingspecial said:**
> Ok :)

Sorry, one more question.......

graphical, or command line "apps"?

I'm not sure I understand your question. Excuse my ignorance of the subject.

---

### Post by nothingspecial on 2011-06-30
> **spacon08 said:**
> I'm not sure I understand your question. Excuse my ignorance of the subject.

That's ok. Do you mean like this

[ATTACH]196402[/ATTACH]

or like this

[ATTACH]196403[/ATTACH]

---

