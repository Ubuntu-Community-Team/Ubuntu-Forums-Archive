---
title: "share me to do this."
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Come TO love on 2011-05-20
I found this book ood book for learn
and i try solve this Qu in page 28

---

### Post by matt_symes on 2011-05-20
Hi

Is this homework ? 

We are not allowed to help with homework (it's against the code of conduct) unless you have had a good stab at it yourself and even then we can only offer suggestions and pointers not solutions. 

Do you have a link for the book ? That would help verify it's not homework.

Post any attempt you have tried yourself.

Kind regards

---

### Post by Come TO love on 2011-05-20
> **matt_symes said:**
> Hi

Is this homework ? 

We are not allowed to help with homework (it's against the code of conduct) unless you have had a good stab at it yourself and even then we can only offer suggestions and pointers not solutions. 

Do you have a link for the book ? That would help verify it's not homework.

Post any attempt you have tried yourself.

Kind regards

no is not homework and  i AM NOT STUDENT JUST study by myself
and you can found this book in internet


[http://moodle.epfl.ch/file.php/3711/Manuals/Bash-Beginners-Guide.pdf](http://moodle.epfl.ch/file.php/3711/Manuals/Bash-Beginners-Guide.pdf)

[http://www.iro.umontreal.ca/~mignotte/IFT1215/Documents/Bash-Beginners-Guide.pdf]("http://www.iro.umontreal.ca/%7Emignotte/IFT1215/Documents/Bash-Beginners-Guide.pdf")


are you want more links for  this book?

---

### Post by nothingspecial on 2011-05-20
How far have you got?

What have you tried?

you may want to read up on if, test ([), echo, ls and head amongst other things.

If it gets written for you, there's no point in doing it really.

---

### Post by matt_symes on 2011-05-20
Hi

> no is not homework and  i AM NOT STUDENT JUST study by myself
and you can found this book in internetRelax. :) 

I am just trying to make sure neither you or i (or anybody else) gets into trouble.

Have you had a go yourself ? As nothingspecial said, what have you tried ? Can you post any attempt you have made ?

Kind regards

---

### Post by matt_symes on 2011-05-20
Hi

> 2. Write a script that takes exactly one argument, a directory name. If the number of arguments is more
or less than one, print a usage message. If the argument is not a directory, print another message. For
the given directory, print the five biggest files and the five files that were most recently modified.Here are some pointers

To check for a directory.

[[ ! -d <directory_name> ]] && { echo "No dir"; return 1; }

$# is the number of arguments, not including $0, so check $# is equal to 1 at the start of the script.

"$1" is the first argument to the script.

You can use the find command to get files. The sort command can sort them if required and head can limit numbers.

Use pipes.

Have a stab at it and post back your script. We can then help you more.

Kind regards

---

### Post by Petrolea on 2011-05-20
There's no need to duplicate threads, we already helped you in this one: [http://ubuntuforums.org/showthread.php?p=10840612](http://ubuntuforums.org/showthread.php?p=10840612)

---

### Post by Come TO love on 2011-05-20
> **matt_symes said:**
> Hi

Here are some pointers

To check for a directory.

[[ ! -d <directory_name> ]] && { echo "No dir"; return 1; }

$# is the number of arguments, not including $0, so check $# is equal to 1 at the start of the script.

"$1" is the first argument to the script.

You can use the find command to get files. The sort command can sort them if required and head can limit numbers.

Use pipes.

Kind regards

you mean frist step will be



[[ ! -d <home> ]] && { echo "No dir"; return 1; }

---

### Post by Come TO love on 2011-05-20
> **Petrolea said:**
> There's no need to duplicate threads, we already helped you in this one: [http://ubuntuforums.org/showthread.php?p=10840612](http://ubuntuforums.org/showthread.php?p=10840612)

this was another Qu:)

---

### Post by matt_symes on 2011-05-20
Hi

> 
[[ ! -d <home> ]] && { echo "No dir"; return 1; }Not quite. <home> would be the name of the directory you a looking for. As it's a parameter to the script the parameter would be "$1". It will check to see if the directory exists or not.

These are the steps i would perform.

1. Check the number of parameters is 1 by checking the value of $#.
2. Check the directory exists by checking the value "$1" in the above code snippet.
3. Using pipes i would then pipeline a find command into sort (if required) and then into head to limit the number of items to 5.

ls <arguments> | sort <based on requirements> | head <the number of items> and display it on the stdout. I am not sure if the sort is needed or not.

This will get you moving.

EDIT: After reading the man pages for the find command,  the ls command might be the better bet for you.

Kind regards

---

### Post by matt_symes on 2011-05-20
Hi

I think the ls command might be easier for you, but...

If you are interested, here a way to sort on the file size using find.

```
find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
```

You can modify it for file modification time as well.

Kind regards

---

### Post by matt_symes on 2011-05-20
Hi

Make sure it is executable.  chmod 755 <file_name>

```

#!/bin/bash

: <<"COMMENT"

2. Write a script that takes exactly one argument, a directory name. If the number of arguments is more
or less than one, print a usage message. If the argument is not a directory, print another message. For
the given directory, print the five biggest files and the five files that were most recently modified.

COMMENT

# First check the number of parameters passed to the script is 1.
[[ $# -eq 1 ]] || { echo "Number of parameters is not equal to one"; exit 1; }

# Check to see if the directory exists.
[[ ! -d "$1" ]] && { echo "The directory $1 does not exist"; exit 1; }

find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5 
``````
matthew@matthew-laptop:~$ ./test.sh 
Number of parameters is not equal to one
matthew@matthew-laptop:~$ ./test.sh /home/matthe
The directory /home/matthe does not exist
matthew@matthew-laptop:~$ ./test.sh /home/matthew /home
Number of parameters is not equal to one
matthew@matthew-laptop:~$ ./test.sh /home/matthew
udev_usb
test.sh
there
here
matthew@matthew-laptop:~$
```You just need to extend this for the modified time and you are there. Read through it. If you have any questions post back.

Kind regards

---

### Post by Come TO love on 2011-05-20
> **matt_symes said:**
> Hi


# First check the number of parameters passed to the script is 1.
[[ $# -eq 1 ]] || { echo "Number of parameters is not equal to one"; exit 1; }

# Check to see if the directory exists.
[[ ! -d "$1" ]] && { echo "The directory $1 does not exist"; exit 1; }

find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5 [/CODE]```
matthew@matthew-laptop:~$ ./test.sh 
Number of parameters is not equal to one
matthew@matthew-laptop:~$ ./test.sh /home/matthe
The directory /home/matthe does not exist
matthew@matthew-laptop:~$ ./test.sh /home/matthew /home
Number of parameters is not equal to one
matthew@matthew-laptop:~$ ./test.sh /home/matthew
udev_usb
test.sh
there
here
matthew@matthew-laptop:~$
```You just need to extend this for the modified time and you are there. Read through it. If you have any questions post back.

Kind regards
  i do this but i get 
home@ubuntu:~$ sh test
test: 1: [[: not found
Number of parameters is not equal to one



!! what is problem?

---

### Post by matt_symes on 2011-05-20
Hi
> 
i do this but i get 
home@ubuntu:~$ sh test
test: 1: [[: not found
Number of parameters is not equal to one'[[' is a bash keyword.

You are using _sh_ to run the command. _sh_ is a symbolic link to the _dash_ shell.

```
matthew@matthew-laptop:~/my_documents$ ls -l $(which sh)
lrwxrwxrwx 1 root root 4 2011-05-08 22:35 /bin/sh -> dash
matthew@matthew-laptop:~/my_documents$
```Therefore typing, _sh test_ will run _dash test_.

```
matthew@matthew-laptop:~/my_documents$ sh test.sh 
test.sh: 12: [[: not found
Number of parameters is not equal to one
matthew@matthew-laptop:~/my_documents$ dash test.sh 
test.sh: 12: [[: not found
Number of parameters is not equal to one
matthew@matthew-laptop:~/my_documents$ 
```To run the script you need to run it with the _bash_ shell.

```
bash test.sh
```

```
matthew@matthew-laptop:~/my_documents$ bash test.sh 
Number of parameters is not equal to one
matthew@matthew-laptop:~/my_documents$ 
```

Kind regards

---

### Post by Come TO love on 2011-05-20
> **matt_symes said:**
> Hi

Number of parameters is not equal to one
matthew@matthew-laptop:~/my_documents$ [/CODE]Kind regards


is shell code will be like this?


```
> if [[ $# -eq 1 ]] || { echo "Number of parameters is not equal to one"; exit 1; }
else [[ ! -d "$1" ]] && { echo "The directory $1 does not exist"; exit 1; }
find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
fi
```

---

### Post by matt_symes on 2011-05-20
Hi

Writing

```
bash test
```

wil run the bash shell with the parameter test. So bash will execute test.

The other way to call a shell script is using this method.

```
/path/to/script/test
```

of if the current working directory is the same as the script

```
./test
```

If run this way, Linux will look inside the file and find the line (it must be the first line)

```
#!/bin/bash
```

It will then know to use the bash shell to run the script.

Kind regards

---

### Post by Come TO love on 2011-05-20
if [[ $# -eq 1 ]] || { echo "Number of parameters is not equal to one"; exit 1; }
 else [[ ! -d "$1" ]] && { echo "The directory $1 does not exist"; exit 1; }
 find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5



is rigth like this ?

---

### Post by matt_symes on 2011-05-20
Hi

```
if [[ $# -eq 1 ]] || { echo "Number of parameters is not equal to one"; exit 1; }

else [[ ! -d "$1" ]] && { echo "The directory $1 does not exist"; exit 1; }

find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
fi                      
```Not exactly, no.

What you are trying to do is...

```
if [[ $# -ne 1 ]]
then
      echo "Number of parameters is not equal to one"; exit 1;
elif [[ ! -d "$1" ]]
then
     echo "The directory $1 does not exist"; exit 1;
fi

find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
```I will talk you through it.
```

if [[ $# -ne 1 ]]
then
      echo "Number of parameters is not equal to one"; exit 1;
```$# is the number of parameters passed to the script. ie _bash test hello there_ has 2 parameters. _bash test hello_ has 1.

if [[ $# -ne 1 ]]. This is saying if the number of parameters passed to the script is not equal (-ne) to 1 then display the message "Number of parameters is not equal to one" and exit the script.

After that check it then runs this check

```
elif [[ ! -d "$1" ]]
then
     echo "The directory $1 does not exist"; exit 1;
fi
```$1 is the first parameter passed to the script. _bash test /home/d_. $1 = /home/d.

[[ ! -d "$1" ]] This is checking if the directory does not exist. The -d flag checks for the directory.

ie

[[ -d /home/d ]] This would return true if the directory exist. 

However [[ _**!**_ -d /home/d ]] will return true if the directory _does not exist_ (_**!**_) and if the directory does not exist it will print the message "The directory $1 does not exist" and exit the script.

After it has performed these two tests it can then get the required files and display them to the screen.

This does that

```
find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
```Kind regards

---

### Post by Come TO love on 2011-05-20
> **matt_symes said:**
> Hi

```
find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
```Kind regards
   yor are smart man:)

ok can you explan this script above
 and  how can sort by recently modified files?

---

### Post by matt_symes on 2011-05-20
Hi
[FONT=monospace]
[/FONT]```
find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
```

First things first. The above commands are pipelined. This means that the output of one command is used as the input for the next command. In Linux the | (pipe) is used to achieve this.

Therefore the output of the _find_ command is fed into the _sort_ command. This is then fed into the _cut_ command and, finally, into the _head_ command.

```
find * -maxdepth 0 -type f -printf "%s %f\n"
```

This command finds all the files in the current directory (-type -f are for files and will ignore directories). -maxdepth 0 is used to ensure that only the current directory is searched. -printf "%s %f\n" This prints the size of the file (%s) and the filename (%f).
```

matthew@matthew-laptop:~/my_documents$ find * -maxdepth 0 -type f -printf "%s %f\n"
179 examples.desktop
77492 Linux_Timeline_gldt1104.tar.bz2
6010 podcast urls.txt
38 tel_call
247 test2.sh
867 test.sh
10152 udev_usb
matthew@matthew-laptop:~/my_documents$ 
```

The first column is the file size and the second column is the filename. This is then used as the input for the sort command.

```
sort -nr
```

This sort the list based on items in the first column (the file size). The -nr switches sort numerically and reverses the order (the biggest files are displayed at the top)

```

matthew@matthew-laptop:~/my_documents$ find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr
77492 Linux_Timeline_gldt1104.tar.bz2
10152 udev_usb
6010 podcast urls.txt
867 test.sh
247 test2.sh
179 examples.desktop
38 tel_call
matthew@matthew-laptop:~/my_documents$ 
```

```
cut -d' ' -f 2 
```

This command chops up the output. What it does is looks for spaces -d' ' and removes any characters that are not part of the second field.
```

matthew@matthew-laptop:~/my_documents$ find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2
Linux_Timeline_gldt1104.tar.bz2
udev_usb
podcast
test.sh
test2.sh
examples.desktop
tel_call
matthew@matthew-laptop:~/my_documents$ 
```

 ```
head -n5
```

Finally this command will remove all but the first 5 items (-n5)
```

matthew@matthew-laptop:~/my_documents$ find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
Linux_Timeline_gldt1104.tar.bz2
udev_usb
podcast
test.sh
test2.sh
matthew@matthew-laptop:~/my_documents$
```

Incedently, there is an issue with the cut command as used above. It will only display the first part of the filename if the filename has spaces.

```
matthew@matthew-laptop:~/my_documents$ ls "a b"
a b
matthew@matthew-laptop:~/my_documents$ find "a b" -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5
a
matthew@matthew-laptop:~/my_documents$ 
```

I will leave you to figure out how to fix that one ;)

As for the last modified files, have a read of the man pages for ls or find. Have an attempt at it and post back how you get on.

That is the best way to learn :D

Kind regards

---

### Post by Come TO love on 2011-05-20
ok thanks you :P

---

### Post by sisco311 on 2011-05-20
> **matt_symes said:**
> Hi

Make sure it is executable.  chmod 755 <file_name>

```

#!/bin/bash

: <<"COMMENT"

2. Write a script that takes exactly one argument, a directory name. If the number of arguments is more
or less than one, print a usage message. If the argument is not a directory, print another message. For
the given directory, print the five biggest files and the five files that were most recently modified.

COMMENT

# First check the number of parameters passed to the script is 1.
[[ $# -eq 1 ]] || { echo "Number of parameters is not equal to one"; exit 1; }

# Check to see if the directory exists.
[[ ! -d "$1" ]] && { echo "The directory $1 does not exist"; exit 1; }

find * -maxdepth 0 -type f -printf "%s %f\n" | sort -nr | cut -d' ' -f 2 | head -n5 
```

The here-document comment is pretty cool. I never saw it before. Of course, one should avoid it for many reasons, you know, compatibility, portability, etc... But still, it is cool!

Oh, and, warnings and errors should be redirected to stderr
```

false || { echo nay; } >&2
```

---

### Post by matt_symes on 2011-05-20
Hi

> **sisco311 said:**
> The here-document comment is pretty cool. I never saw it before. Of course, one should avoid it for many reasons, you know, compatibility, portability, etc... But still, it is cool!

Oh, and, warnings and errors should be redirected to stderr
```

false || { echo nay; } >&2
```

You have raised some good points Sisco, especially the compatibility and portability issues, hence (as you know) the issues the OP was having when using sh and not bash.

It was written for newer versions of bash and specifically Ubuntu.

A note to the OP. As you learn more shell scripting you will discover what is portable and what is not portable. As you are learning on Ubuntu it does not matter so much at the moment, but it is something to keep in mind.

Kind regards

---

### Post by Sohar-uni on 2011-05-24
> **Come TO love said:**
> I found this book ood book for learn
and i try solve this Qu in page 28
 
 
hi dear i want as about this book .What is the name of book
 
and when i try to solve this quastion i have error can any one help me pleas??

---

### Post by Sohar-uni on 2011-05-24
please can eny one help my i dont understan this quastion

---

### Post by Sohar-uni on 2011-05-25
:ks:ks:ks

---

### Post by matt_symes on 2011-05-25
Hi

> **Sohar-uni said:**
> hi dear i want as about this book .What is the name of book

The book was linked in post #2
 
> and when i try to solve this quastion i have error can any one help me pleas??

What errors are you getting ? Post the back here.

Kind regards

---

