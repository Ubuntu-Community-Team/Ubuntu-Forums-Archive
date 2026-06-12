---
title: "How do I print the command line output into a gedit file?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by unapendeza on 2011-05-10
Hi, I'm a new Ubuntu user and pretty much a noob although I've taught myself a lot so far and I've become accustomed to using the terminal. So could some kind soul explain to me how I print the command line output into a gedit file and then have it automatically open the file right after I execute the command? I can't figure out what commands to type into the terminal to do this.

---

### Post by Xanthomryr on 2011-05-10
```
ls > foo && gedit foo
```

The > redirects the terminal output into the foo file (>> would append) and the && executes the following command if "ls > foo" ended without error.

Maybe someone knows a better way.

---

### Post by unapendeza on 2011-05-10
I tried ```
 ls -l | gedit 
``` immediately after a command and all it did was open a blank file in gedit. I'm not sure of what I'm doing wrong.

---

### Post by unapendeza on 2011-05-10
> **Xanthomryr said:**
> ```
ls > foo && gedit foo
```The > redirects the terminal output into the foo file (>> would append) and the && executes the following command if "ls > foo" ended without error.

Maybe someone knows a better way.

This isn't what I'm looking for. It didn't print the output to a file, it just opened up blank files.

---

### Post by Xanthomryr on 2011-05-10
Then there are no files and folders where you ran it.

When I run this in my home folder it prints the result of ls to the file foo and shows it in gedit.

---

### Post by unapendeza on 2011-05-10
> **Xanthomryr said:**
> Then there are no files and folders where you ran it.

When I run this in my home folder it shows me the result of ls in gedit.

This isn't what I'm looking for though. I want to see the command line output in a text file, this just opened up new files that didn't have the command line output in them. They just displayed the contents of my home folder.

---

### Post by Xanthomryr on 2011-05-10
Yeah, and the contents of your home folder is the command output of ls.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)

---

### Post by yetiman64 on 2011-05-10
> **unapendeza said:**
> This isn't what I'm looking for. It didn't print the output to a file, it just opened up blank files.

It listed the contents of my home folder here, outputted it to a text file "foo" and then opened it in gedit. It works.

If you are at the standard command prompt you are in your home folder, did you copy and paste the command given or type it out? Copy and paste is better, more accurate.

> explain to me how I print the **command line output** into a gedit file **What is the command you are working with you need to redirect the output of?** 

Xanthomryr has shown you what you want, and it works, you may need to adjust the command Xanthomryr gave to suit your situation.

---

### Post by dFlyer on 2011-05-10
> **unapendeza said:**
> Hi, I'm a new Ubuntu user and pretty much a noob although I've taught myself a lot so far and I've become accustomed to using the terminal. So could some kind soul explain to me how I print the command line output into a gedit file and then have it automatically open the file right after I execute the command? I can't figure out what commands to type into the terminal to do this.

If I understand you correctly, you want to get the output of a command you ran in the form of a text file. to do that just run:

command-name >file.output

command-name is the program you want to run and file.output is the name you want the file to be. Example

sudo apt-get update >ubuntu.foo

will produce a file ubuntu.foo with the web pages searched for update.

---

### Post by philinux on 2011-05-10
> **unapendeza said:**
> Hi, I'm a new Ubuntu user and pretty much a noob although I've taught myself a lot so far and I've become accustomed to using the terminal. So could some kind soul explain to me how I print the command line output into a gedit file and then have it automatically open the file right after I execute the command? I can't figure out what commands to type into the terminal to do this.

Might help us if you tell us what the command is you're executing.

---

### Post by dFlyer on 2011-05-10
> **dFlyer said:**
> If I understand you correctly, you want to get the output of a command you ran in the form of a text file. to do that just run:

command-name >file.output

command-name is the program you want to run and file.output is the name you want the file to be. Example

sudo apt-get update >ubuntu.foo

will produce a file ubuntu.foo with the web pages searched for update.

I just noticed you want it to also open in gedit so just add

command-name >file.output && gedit file.output

just so you know the sudo above is just for root use programs, which is not needed for regular program.

---

### Post by The Cog on 2011-05-10
If you want to capture the entire command-line session to a file rather than just capture the output of one command, try this:
```
script foo.txt && gedit foo.txt
```
Finish the command-line session with the command **exit**, and then gedit will open the saved conversation.

---

### Post by Xanthomryr on 2011-05-10
> **The Cog said:**
> If you want to capture the entire command-line session to a file rather than just capture the output of one command, try this:
```
script foo.txt && gedit foo.txt
```
Finish the command-line session with the command **exit**, and then gedit will open the saved conversation.
That's a new and good one for me.
Thanks for that. :)

---

### Post by unapendeza on 2011-05-10
> **dFlyer said:**
> If I understand you correctly, you want to get the output of a command you ran in the form of a text file. to do that just run:

command-name >file.output

command-name is the program you want to run and file.output is the name you want the file to be. Example

sudo apt-get update >ubuntu.foo

will produce a file ubuntu.foo with the web pages searched for update.

yes, this helps! thank you.

---

