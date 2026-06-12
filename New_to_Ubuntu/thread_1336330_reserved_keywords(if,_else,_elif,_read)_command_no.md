---
title: "reserved keywords(if, else, elif, read) :command not found"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by sushrutha on 2009-11-24
Hi,

I'm an new UBUNTU user.
Whenever I try to run a script, i get an error as
if: command not found
elif: command not found
else: command not found
read: command not found

I don't get this message for commands like chmod, -d, cp etc...

I tried to find out the path of these reserved  keywords. But, it doesn't even show the path.
If it shows the path, then the instruction would be working properly itself.

Please help.

Regards
Sushrutha.

---

### Post by mobilediesel on 2009-11-24
> **sushrutha said:**
> Hi,

I'm an new UBUNTU user.
Whenever I try to run a script, i get an error as
if: command not found
elif: command not found
else: command not found
read: command not found

I don't get this message for commands like chmod, -d, cp etc...

I tried to find out the path of these reserved  keywords. But, it doesn't even show the path.
If it shows the path, then the instruction would be working properly itself.

Please help.

Regards
Sushrutha.

Show us the script you're trying to run using the [code] tag. The button at the top that looks like "**#**"

---

### Post by sushrutha on 2009-11-25
i am unable to run a program written in VIM editor version 7.2.79 by Bram Moolenaar et al. i m using ubuntu 9.04 desktop edition., mine is bash shell.
 
my program is as below :

echo "enter the file/directory"
Read $df
If [ -d $df ]
   Then
   Echo "it is a directory"
Elif [ -f $df ]
    Then
     Echo "it is a file"
 Else 
     Echo "it is not a file & not a directory"
fi

To execute, i m using the command as 

chmod +x filename.sh
./filename.sh

or

sh filename.sh

but its giving the error as,
 
Read : command not found
If:command not found
Else:command not found
Thencommand not found
Elif:command not found
.
.
.

if i ask whereis If or Else or Then it shows like "If : " .
 but if i ask whereis echo it shows echo: /bin/echo /usr/share/man/man1/echo.1.gz.

so can u please tell me how to execute this program.
and also can u tell me how to install matlab r.2007a in ubuntu9.04 desktop edition.
 or can u give some references where  i can find the commands..

---

### Post by jacobs444 on 2009-11-25
the first letters should not be capitalized in the commands.

---

### Post by jacobs444 on 2009-11-25
that is your problem, If should be if Elif should be elif Echo should be echo, linux command line is case sensitive, and most commands if not all are lowercase only!

---

### Post by jacobs444 on 2009-11-25
take away all caps other than what gets printeed to the user and it will work i promise.

---

### Post by mobilediesel on 2009-11-25
jacobs444 answered it. linux and unix-like systems are case-sensitive. Commands are all lower-case.

---

### Post by sushrutha on 2009-11-25
Thank you very much.. The errors are gone though it didn't execute completely.. :)
In the script, now. whatever input i give, it gives the output as "It is a directory"..

---

### Post by pbrane on 2009-11-25
this script works for me.

```

#!/bin/bash

pattern="$1"
if [ -d $pattern ]; then
	echo $pattern 'is a directory'
elif [ -f $pattern ]; then
	echo $pattern 'is a file'
else
        echo $pattern 'is not a file or a directory'
fi

```

this allows you to enter the file or directory as an argument to the script, like
**$ ./test.sh /home**

---

