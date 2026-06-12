---
title: "Environment Variable explained..."
date: 2010-08-14
forum: New to Ubuntu
---

### Post by adharwood on 2010-08-14
Hi folks

I think I need abit of help with environment variables
Basically I have a command (ncmpcpp) that I type into the terminal to load a program.

Im looking for a way to create an Alias, for example:
instead of typing "ncmpcpp", I could just type "music" 

Following this, is there a way of typing a command that carries out a multiplicity of other commands?
Say, if I typed "new_directory", it would run the following
"cd /home/ad" and then "mkdir cookies"


Any help would be greatly appreciated!

---

### Post by pastalavista on 2010-08-14
You could write a [bash script]("http://www.linuxconfig.org/Bash_scripting_Tutorial") and the name of the script would be the command.

By the way, welcome to the forums.

---

### Post by SoFl W on 2010-08-14
alias music='ncmpcpp'

You can add that to your ".bashrc" file.  It is case sensitive.

---

### Post by SoFl W on 2010-08-14
Open a terminal window and type 
```
nano .bashrc
```
scroll down until you get to the alias section.  (It can go anywhere, but to keep it organized)

---

### Post by adharwood on 2010-08-14
> **SoFl W said:**
> alias music='ncmpcpp'

You can add that to your ".bashrc" file.  It is case sensitive.

Ah! thankyou so much! 
Yeah I had been oblivious to the alias function!
So, to add multiple coammands, are these comma separated?

---

### Post by sandyd on 2010-08-14
> **adharwood said:**
> Ah! thankyou so much! 
Yeah I had been oblivious to the alias function!
So, to add multiple coammands, are these comma separated?
naw. their either seperated by the "&" character (with spaces between the command and the character, or by the ";" character

---

### Post by mbsullivan on 2010-08-14
> naw. their either seperated by the "&" character (with spaces between the command and the character, or by the ";" character

You can also use TWO "&&" characters between the commands. Each approach has subtle differences, though.

(1) Using & characters will execute all commands IN PARALLEL, so if you want the commands to execute one after another, use some other method.

(2) Using the && character will execute subsequent commands only if all previous commands have returned a ZERO EXIT CODE (which normally indicates "success"). Therefore, if one command errors out, all of the subsequent commands will NOT execute.

(3) Using ; will execute all commands one after another, regardless of error codes.

Mike

---

### Post by SoFl W on 2010-08-14
Would defining a function work for you? Define your function inside the .bashrc file as with the alias command.

Example:
```
function mycommand
   {
    cd /var/log
    ls -la
    cd /home/username/
    ls -la
    cd /etc/
    ls -la
    }

```

---

