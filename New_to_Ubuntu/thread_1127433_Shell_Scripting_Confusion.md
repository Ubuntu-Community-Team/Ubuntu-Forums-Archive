---
title: "Shell Scripting Confusion"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by SuperMiguel on 2009-04-16
A script containing the df and du commands displays nothing (not even an error message) when executed. Why might that happen? :(

---

### Post by DGortze380 on 2009-04-16
> **SuperMiguel said:**
> A script containing the df and du commands displays nothing (not even an error message) when executed. Why might that happen? :(

Works fine for me, can you post the script please?
Is it running in cron?

---

### Post by hovzio on 2009-04-16
Can you show some examples of what you are trying to do? Try echoing output with command substitution:

```
echo "$(du -sh *)"
```

This will work, if you don't mind pasting your sample script please do so. It would be easier to explain.. what you described should work :)

---

### Post by SuperMiguel on 2009-04-16
ya thats actually my questions.. In which case it will not show anything not even an error?

---

### Post by Bachstelze on 2009-04-16
> **SuperMiguel said:**
> ya thats actually my questions.. In which case it will not show anything not even an error?

In a lot of cases. Show us your script.

---

### Post by SuperMiguel on 2009-04-16
> **HymnToLife said:**
> In a lot of cases. Show us your script.

i dont have the script i want to make them two scripts containing the df and du commands displays nothing (not even an error message) when executed

---

### Post by hovzio on 2009-04-16
Here is a sample:

```
#!/bin/sh

df
du
exit
```


Make it executable and launch it

```
chmod 750 script.sh
./script.sh
```

This will work.

EDIT: are you executing these from a terminal or from nautilus? Try doing it from a terminal emulator, otherwise you will also have to invoke xterm or gnome terminal etc..

---

### Post by SuperMiguel on 2009-04-16
basically what im traying to find out 2 reason "WHY" a script containing the df and du commands displays nothing (not even an error message) when executed

So just the 2 reasons :)

Kind of looking for the instance where it doesnt work, or it doesnt display anything not even errors.

thanks

---

### Post by hovzio on 2009-04-16
> **SuperMiguel said:**
> basically what im traying to find out 2 reason "WHY" a script containing the df and du commands displays nothing (not even an error message) when executed

So just the 2 reasons :)

thanks

try what I posted above or show exactly what it is you are trying to do because.. the df and du command within a script will indeed write to standard output.

---

### Post by SuperMiguel on 2009-04-16
what im trying to do is an script that has the df and du command on it and when u run it it doesnt do anything. not even an errors

---

### Post by hovzio on 2009-04-16
> **SuperMiguel said:**
> what im trying to do is an script that has the df and du command on it and when u run it it doesnt do anything. not even an errors

so your saying that this doesnt work when you execute it??

```
#!/bin/sh

df
du
exit
```

This is how your script should look, or somthing similar to this.

OR are you trying to make it so that no output is give, redirect standard output and error to /dev /null.

---

### Post by northern lights on 2009-04-16
Your script does nothing and you want it to give some (sensible) output?
Start from the example given.

You want a script that does nothing?
Leave it blank. Won't do jack sh*t.

On a more serious note: Please explain in detail what you're trying to accomplish. I doubt I'm the only one who can't make sense of what you want to do.

---

### Post by SuperMiguel on 2009-04-16
> **hovzio said:**
> so your saying that this doesnt work when you execute it??

```
#!/bin/sh

df
du
exit
```

This is how your script should look, or somthing similar to this.

hehe... that does work... The script that im traying to make is one that has df and du on it but when you execute it does nothing (doesnt give any output) neither an error.

---

### Post by jenkinbr on 2009-04-16
> **northern lights said:**
> Your script does nothing and you want it to give some (sensible) output?
Start from the example given.

You want a script that does nothing?
Leave it blank. Won't do jack sh*t.

On a more serious note: Please explain in detail what you're trying to accomplish. I doubt I'm the only one who can't make sense of what you want to do.
You're not.

I can look at the examples given, and know they will produce output, but without a copy of the script the OP is using, or a clear explanation of what is supposed to happen/what is happening, we can't help much...

---

### Post by jenkinbr on 2009-04-16
> **SuperMiguel said:**
> hehe... that does work... The script that im traying to make is one that has df and du on it but when you execute it does nothing (doesnt give any output) neither an error.
As stated before, could you post a copy of the broken script?

---

### Post by northern lights on 2009-04-16
Mkey. So it is supposed to give no output when run in the shell. Understood.

Still, you do want some sort of output, right? Otherwise I'd still advocate a blank file, or better, not executing anything at all.

Have you looked into [piping]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-4.html") your output to a textfile?

---

### Post by hovzio on 2009-04-16
> **SuperMiguel said:**
> hehe... that does work... The script that im traying to make is one that has df and du on it but when you execute it does nothing (doesnt give any output) neither an error.


This should tell you that their may be a mistake in "the script your trying to make". rewrite it and use the example as a template if that helps.


If what you want is "no output" then do this

echo "hello world" 2> /dev/null 1&>2

This will send all output (stdin and stder) to your "bit bucket". This is used for testing the exit status of a command.. Like has been stated, I too am not sure what your looking for..

---

### Post by SuperMiguel on 2009-04-16
> **northern lights said:**
> Mkey. So it is supposed to give no output when run in the shell. Understood.

Still, you do want some sort of output, right? Otherwise I'd still advocate a blank file, or better, not executing anything at all.

Have you looked into [piping]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-4.html") your output to a textfile?

So it is supposed to give no output when run in the shell. Understood. GOOD :)

Still, you do want some sort of output, right? Otherwise I'd still advocate a blank file, or better, not executing anything at all. NO! i dont want any output.. but i want the script to still have these 2 commands and not have an empty script not a comment out script..

So i want to run the script and that nothing happens..

---

### Post by SuperMiguel on 2009-04-16
> **hovzio said:**
> This should tell you that their may be a mistake in "the script your trying to make". rewrite it and use the example as a template if that helps.


If what you want is "no output" then do this

echo "hello world" 2> /dev/null 1&>2

This will send all output (stdin and stder) to your "bit bucket". This is used for testing the exit status of a command.. Like has been stated, I too am not sure what your looking for..

ya ya i think thats almost what i want... :)

so the first reason why the script will not display anything is because it redirects the output to a file... I need another reason any ideas?

---

### Post by northern lights on 2009-04-16
> **SuperMiguel said:**
> So i want to run the script and that nothing happens..

> **SuperMiguel said:**
> so when i run it nothing is display it has no visual output..?

"Nothing happening" and "no visual output" are not even remotely the same.
When I supposed that you would want some sort of output (outside the shell), I was doing so, cause you're not scripting for nothing. So while you might not want no output of any sort, your script does have a purpose, right?

Let me paraphrase my question: What is the final purpose of this script of yours?

---

### Post by hovzio on 2009-04-16
> **SuperMiguel said:**
> ya ya i think thats almost what i want... :)

so the first reason why the script will not display anything is because it redirects the output to a file... I need another reason any ideas?

You need to redirect your "output" seperatly for every command you give. Each starts its own process and runs seperatly..



EDIT: what is it you are trying to do, are you in trying to test an exit status??

Why don't you take a look at this for a solid start..

[http://tldp.org/LDP/abs/html/sha-bang.html](http://tldp.org/LDP/abs/html/sha-bang.html)

---

### Post by SuperMiguel on 2009-04-16
> **hovzio said:**
> You need to redirect your "output" seperatly for every command you give. Each starts its own process and runs seperatly..


EDIT: what is it you are trying to do, are you in trying to test an exit status??

yep

---

### Post by ibuclaw on 2009-04-16
You use **$?**, one of the shell special strings to test the exit status.

ie:
```

df >/dev/null 2>&1
echo $?

```
and exit status of 0 means successful. Any other number means unsuccessful.

Regards
Iain

---

### Post by Alekz_ on 2009-04-16
OK! Even if I can't figure out WHY you want a script that do nothing, there are some tips :)

You can out put to /dev/null
You can out put to a file
You can out put to a pipe
You can out put to the screen
You can out put to a printer

Which of them do you want? :D

---

