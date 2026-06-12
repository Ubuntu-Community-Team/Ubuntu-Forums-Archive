---
title: "symbolic links"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by beew on 2010-08-03
Sometimes you can run a program in the terminal by just typing the name of the program, sometimes you have to enter the whole path. Not knowing much about Unix I guess it maybe because when the program is installed a symbolic link is created like
```
ln -s 'full path to bin file' progname
```So when you type progname in the terminal the actual program is invoked as if the full path is entered.  I can be wrong as this is just a guess.


However, there are other programs which apparently cannot be just invoked by entering the path in the terminal, you have to precede the actual program with things like sh, ./ or special commands like perl (if it is a .pl program) or python (if it is a .py program) 

Is there a way to make short hands for running these kind of programs, where an extra command is needed in addition to the program file's full path.

Sometimes it seems that you have to cd into the directory where the program is before you apply one of these special commands to run a program.  Is it the same if you don't cd into the directory but specify the full path to the program ? In other words, I am not sure if 
```
$ python  /path/prog.py 
``` would have the same effect as```
$ cd /path/
$ python prog.py
```

---

### Post by jtarin on 2010-08-03
Applications are normally installed to certain directories.The [PATH]("http://www.cyberciti.biz/faq/howto-print-path-variable/") command can give you some insight. Often after installing some applications you will need to update your database so PATH can find your files. Once this is done its not usually necessary to enter the complete path to an executable. If you have one in a non-standard location you can update your PATH.

---

### Post by beew on 2010-08-03
I know the path command. I want to know if it is possible to make command line short hands (using symbolic links?) for running those programs which have to be run with other commands _in addition_ to typing the path of the executable (like invoking sh, ./ , python, or perl in my example, or maybe(?) having to cd into the proper directory first)

---

### Post by Sanjeevtrip on 2010-08-03
you can add the shebang line,
type 
```

which perl

```

will give you full path of perl, it its entry is in PATH environment variable

or if you know the full path of perl, say /bin/perl, then add shebang line
```

#!/bin/perl

```

this should be the first line of your perl program, then set the executable bit
```

chmod +x myprog.pl

```

and you can run your program by
./myprog.pl

you can link your programs in your $HOME/bin
and export it to the PATH

```

export PATH=$PATH:$HOME/bin

```

and your programs is ready
$myprog.pl

similar for the python or any shell programs.

---

### Post by ankspo71 on 2010-08-03
Hi,
I think one way to do this is to create a symlink to the file, but create it in a root directory such as the /usr/bin directory. I found that this doesn't always work for every application that I tried though.

```
sudo ln -s /path/to/file /usr/bin/name-of-file
```

By the way, I can open firefox with the bash command "bash firefox" instead of "bash /usr/bin/firefox". So I think it is possible for python scripts too.

Hope this works.

---

### Post by beew on 2010-08-03
Thanks, Sanjeevtrip

 That is very informative. What about programs that you have to run by doing "./"  ?

---

### Post by beew on 2010-08-03
Hi,Ankspo71

So do you then invoke a command on the symbolic name? So basically you create a shortcut for the program file and then run it by (say if it is .py) ```
$ python symname
```?

---

### Post by jtarin on 2010-08-03
_**Aliases**_
We use certain commands over and over again, or we have preferred combinations of options which we always give to certain commands. We can create shortcuts to these commands by giving them an alias in our ~/.bashrc file. The format is:

alias new_name='command -options'
Some example aliases are:

alias ls='ls --color -CF'
alias rmkpid='rm /home/mike/.kde/share/apps/kppp/kppp.pid'
alias greps='ps -aux | grep $1'

---

### Post by beew on 2010-08-04
Thanks, jtarin.  That may be what I am looking for.

---

### Post by ankspo71 on 2010-08-04
> **beew said:**
> Hi,Ankspo71

So do you then invoke a command on the symbolic name? So basically you create a shortcut for the program file and then run it by (say if it is .py) ```
$ python symname
```?

"python symname" 
Yes, I am assuming this will work just as easily for python as it would launching applications by symlinks. If it doesn't work, the symlink can easily be removed if necessary. I don't have any python scripts to experiment though. Other people in this thread gave some other good advice too.

---

### Post by beew on 2010-08-04
Here is a question that may be related. 

I have installed a program called Rcmdr from the repository. It created a launcher in the drop down menu Applications > Science. I opened System > Main Menu to find R commander to check its properties. The launching command is ```
sh -c 'R_DEFAULT_PACKAGES="$R_DEFAULT_PACKAGES Rcmdr" R "$@"'
```What does this mean? 

When I click the launcher the terminal opens up and R starts in the terminal to load Rcmdr (R is a  statistical package and Rcmdr is its gui front end)

However, when I  do alt+F2 and paste the command into the box and run, nothing happens! I thought the icon launcher is just a front end to the launching command so if you can launch by clicking the launcher you certainly should be able to by simply running the command!

P.S. It is not a question about R, but about short hands for commands and maybe Nautilus. In R onec can launch R commander by simply typing library(Rcmdr), but that is irrelevant to my question. I just happen to have this as an example.

---

### Post by ankspo71 on 2010-08-04
Hi,
For some reason, the run dialog doesn't automatically launch the terminal for applications that need to be run from the terminal first, even though the start menu does. I have noticed this in the KDE desktop too.

If you would like to launch that command by Alt+F2, you need to include "gnome-terminal -x" before the command like this:
```
gnome-terminal -x sh -c 'R_DEFAULT_PACKAGES="$R_DEFAULT_PACKAGES Rcmdr" R "$@"'
```
On my kubuntu system it is "konsole -e" instead of "gnome-terminal -x" because I use a different terminal.

Hope this helps.

---

### Post by David Andersson on 2010-08-04
My two cents about bin and PATH:

If you are experimenting with scripts or developing a program, accept that you have to start the program using a full or relative path, like **./programname**

If you have made a useful script for personal use, save it in ~/bin (that is /home/yourname/bin). If ~/bin exists, Ubuntu will automatically add ~/bin to PATH, and you can start the program by simply typing **programname**

It is possible to copy or symlink your useful but personal scripts and even your experimental stuff into /bin or /usr/bin, but I **don't** think that is good advice. You must be root (sudo) to do it. You will lose it if you reinstall the system and only keep /home. A symlink from / to a less important partition will be broke during boot (not a real problem, just looks bad from a principal point of view). Upgrades of the system might pause and ask you what to do with it. Other users might run it (not a bad thing if it is useful and not personal). If you must use a common bin for local stuff, i think /usr/local/bin is better than /bin and /usr/bin.

(And as others have mentioned, wherever you put them, chmod +x and shebang your scripts)

---

