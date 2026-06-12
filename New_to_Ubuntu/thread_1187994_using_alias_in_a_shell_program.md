---
title: "using alias in a shell program"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Markstar on 2009-06-15
Hi,
I'm trying to learn about the **alias** command and I got it to work from the bash, e.g. *alias ll='ls -l'* works. However, I have now created a file ('myenv'), made it executable and entered the above line. 
```
echo "start setting up environment"
alias ll2='ls -l'
echo "finished setting up the environment"

```

Now I execute the file, the echos show up, but the alias command did not take! :(

What am I doing wrong?

---

### Post by hayden92 on 2009-06-15
If you only want it to execute the "ls -l" command once (when you run the script):

```

echo "start setting up environment"
ls -l
echo "finished setting up the environment"

```

But I'm assuming that you want to be able to use this command after you have run the script... I would recommend adding the alias to your /home/$USER/bashrc file.

If fact there are already some aliases in that file that do what you want, but they are commented out by default

Also, if you add aliases to this file, you can run them any time... without running a script first!

---

### Post by kpkeerthi on 2009-06-15
That was because, when you ran the shell script, it ran within a subshell that your main shell (the shell that is prompting you for commands - an interactive shell) spawned. Variables & aliases created by a subshell die with it and are not visible to the parent shell.

The recommended place to put your aliases is ~/.bashrc which bash reads everytime it is launched.

---

### Post by Markstar on 2009-06-15
@hayden92 & kpkeerthi: Alright, I'll put it in bashrc if I want it to load automatically. 

But actually this was just for educational purposes for now. Since I'm still new at Ubuntu (gave up the last time and now have just accepted the fact that I will not run Ubuntu on my desktop for now), I am reading this book (Ubuntu Unleashed), which says that my method above would work: >                                                                           One way to run your shell program is to execute the file myenv from the command line as if it were a Linux command:
 $ ./myenv
 So if I understand you two correctly, the book is simply wrong and there is no way to get this to work without editing the bashrc file?

---

### Post by Mornedhel on 2009-06-15
Does the book's example specifically mention alias ?

As far as I know, the other posters are correct. Calling your script via sh myenv.sh or ./myenv.sh has the same result : a sh subshell is started which executes myenv.sh. This new shell is affected by the alias command and thus the alias will work briefly, within the subshell only, and will stop working once the subshell exits (immediately after myscript.sh exits).

---

### Post by Markstar on 2009-06-15
> **Mornedhel said:**
> Does the book's example specifically mention alias ?

As far as I know, the other posters are correct. Calling your script via sh myenv.sh or ./myenv.sh has the same result : a sh subshell is started which executes myenv.sh. This new shell is affected by the alias command and thus the alias will work briefly, within the subshell only, and will stop working once the subshell exits (immediately after myscript.sh exits).Yes, the section is called "Writing and Executing a Shell Script" and *alias* is used as the example:> In this section, you learn how to write a simple shell script to set up a number of aliases (command synonyms) whenever you log on. Instead of typing all the aliases every time you log on, you can put them in a file by using a text editor, such as vi, and then execute the file. Normally these changes are saved in systemwide shell configuration files under the /etc directory to make the changes active for all users or in your .bashrc, .cshrc (if you use tcsh), or .bash_profile files in your home directory.
Here is what is contained in myenv, a sample shell script created for this purpose (for bash):

#!/bin/sh
alias ll=’ls -l’
alias ldir=’ls -aF’
alias copy=’cp’

This simple script creates command aliases, or convenient shorthand forms of commands, for the ls and cp commands. ...


---

### Post by leandromartinez98 on 2009-06-15
> **Markstar said:**
> @hayden92 & kpkeerthi: Alright, I'll put it in bashrc if I want it to load automatically. 

But actually this was just for educational purposes for now. Since I'm still new at Ubuntu (gave up the last time and now have just accepted the fact that I will not run Ubuntu on my desktop for now), I am reading this book (Ubuntu Unleashed), which says that my method above would work:  So if I understand you two correctly, the book is simply wrong and there is no way to get this to work without editing the bashrc file?

The book seems correct. The "shell program" is not the "program of your shell" if that is the confusion here. A shell program is a program (in scripting language) to do things. For instance, you could use it to convert files from jpg to png:

```

#!/bin/bash
for file in `ls *.jpg`; do
  convert $file ${file/jpg/png}
done

```

If you set an alias within this program, it will be valid within the "shell created to run your program only". That means:

```

#!/bin/bash
alias convert=xxx
for file in `ls *.jpg`; do
  xxx $file ${file/jpg/png}
done

```

But back to "your shell", the xxx command will not be defined (thanks god, if that was the case running scripts done by other people would be disastrous).

The .bashrc file is the file that defines the behaviour of your default shell and yes, you need to edit it to create a permanent alias. But note, if you need specific environment variables to run a specific program, you should create a script that defines the variables and launches the program:

```

alias= what you want
export what you want
run_your_program_that_needs_the_above_environment

```

This is reasonable, since you don't want the environment to be defined all the time for all other programs.


EDIT: The book actually specifies that the file to modified is the .bashrc in that case but yes, I agree that it is confuse the way it is written.

---

### Post by Markstar on 2009-06-15
Thanks guys, I think I got it and they way you explained it does make sense. I'll just accept it as such and move on. But just for the record...

...the book said:> After you execute the command myenv, you should be able to use ldir from the command line to get a list of files under the current directory and ll to get a list of files with attributes displayed.That is pretty clearly contrary to what you told me. :p

---

### Post by kpkeerthi on 2009-06-15
> **Markstar said:**
> @hayden92 & kpkeerthi: Alright, I'll put it in bashrc if I want it to load automatically. 

...

 I am reading this book (Ubuntu Unleashed), which says that my method above would work:  So if I understand you two correctly, the book is simply wrong and there is no way to get this to work without editing the bashrc file?

I haven't read the book. From what you asked, it won't work for the reason I explained above. 

When you run a shell script like this:
```
./myenv
```, a subshell is spawned. It is the subshell that would setup the alias. The parent shell will have no idea of the 'things' that the subshell created.

```
source ./myenv
``` will cause the commands from ./myenv run as part of the shell invoking the 'source ....' line. This is probably what you want. Try this and see.

---

### Post by Markstar on 2009-06-16
> **kpkeerthi said:**
> ```
source ./myenv
``` will cause the commands from ./myenv run as part of the shell invoking the 'source ....' line. This is probably what you want. Try this and see.Yeah, that worked - so it is possible after all. Thank you! :p

---

