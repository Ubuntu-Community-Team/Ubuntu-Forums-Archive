---
title: "logging for all command actions"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by sazan on 2009-01-16
hi
i wanted to store all work that i do in CLI like all command that i run along with the output they give to be stored in a particular file.. just want to log out everything.. can anyone help me how i can achieve this ??

---

### Post by amauk on 2009-01-16
commands run are stored in the bash history

use the up/down arrows to cycle through
or ctrl+R to search the history

as for logging all output
that'd potentially take up huge amounts of storage

---

### Post by sazan on 2009-01-16
my outputs are not too big , the file size will be in KBs if stored in file.. 

there must be some way

---

### Post by stevoo on 2009-01-16
you can do 
$nohup ls 
ls will be any command you want 
and everything will be stored in that file. 
nohup.out

you can then read it with less nohup.out

---

### Post by amauk on 2009-01-16
script will log the complete actions of a terminal session

man script
> SCRIPT(1)                 BSD General Commands Manual                SCRIPT(1)

NAME
     script - make typescript of terminal session

SYNOPSIS
     script [-a] [-c COMMAND] [-f] [-q] [-t] [file]

DESCRIPTION
     Script makes a typescript of everything printed on your terminal.  It is
     useful for students who need a hardcopy record of an interactive session
     as proof of an assignment, as the typescript file can be printed out
     later with lpr(1).

     If the argument file is given, script saves all dialogue in file.  If no
     file name is given, the typescript is saved in the file typescript.

     Options:

     -a      Append the output to file or typescript, retaining the prior con&#8208;
             tents.

     -c COMMAND
             Run the COMMAND rather than an interactive shell.  This makes it
             easy for a script to capture the output of a program that behaves
             differently when its stdout is not a tty.

     -f      Flush output after each write. This is nice for telecooperation:
             One person does ‘mkfifo foo; script -f foo’ and another can
             supervise real-time what is being done using ‘cat foo’.

     -q      Be quiet.

     -t      Output timing data to standard error. This data contains two
             fields, separated by a space. The first field indicates how much
             time elapsed since the previous output. The second field indi&#8208;
             cates how many characters were output this time. This information
             can be used to replay typescripts with realistic typing and out&#8208;
             put delays.

     The script ends when the forked shell exits (a control-D to exit the
     Bourne shell (sh(1)), and exit, logout or control-d (if ignoreeof is not
     set) for the C-shell, csh(1)).

     Certain interactive commands, such as vi(1), create garbage in the type&#8208;
     script file.  Script works best with commands that do not manipulate the
     screen, the results are meant to emulate a hardcopy terminal.

ENVIRONMENT
     The following environment variable is utilized by script:

     SHELL  If the variable SHELL exists, the shell forked by script will be
            that shell. If SHELL is not set, the Bourne shell is assumed.
            (Most shells set this variable automatically).

SEE ALSO
     csh(1) (for the history mechanism), scriptreplay(1).

HISTORY
     The script command appeared in 3.0BSD.

BUGS
     Script places everything in the log file, including linefeeds and
     backspaces.  This is not what the naive user expects.

AVAILABILITY
     The script command is part of the util-linux-ng package and is available
     from [ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/](ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/).

Linux                            July 30, 2000                           Linux

---

### Post by amauk on 2009-01-16
ps.
see this as well
[http://www.builderau.com.au/program/linux/soa/Using-script-to-record-terminal-sessions/0,339028299,339273932,00.htm]("http://www.builderau.com.au/program/linux/soa/Using-script-to-record-terminal-sessions/0,339028299,339273932,00.htm")

---

### Post by sazan on 2009-01-16
thanks for the answer... but tat will require me to use nohup everytime.. 

i was looking for something like this that i create a file somewhere and use some command to open it for logging and it starts storing my actions in it until i say so to stop it.. 

thanks in advance

---

### Post by sazan on 2009-01-16
Thank you guyz ... Script was what i was exactly looking for.. 

thanks a ton :P:P

---

