---
title: "sh files"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by navaneethan on 2009-09-09
I need to know that "How to open the terminal using sh file?" and also How to execute the sh file by clicking the button? 

Example:

         **how to execute the command "wvdial" by clicking the button only **

---

### Post by credobyte on 2009-09-09
terminal-open.sh
```
gnome-terminal &
```wvdial-execute.sh
```
wvdial &
```

I don't really understand what you mean with "by clicking the button only", but you can create a launcher and in the command field, add the path to your sh script ( or enter your command .. depends on what you need it to do ).

---

### Post by navaneethan on 2009-09-09
> **credobyte said:**
> terminal-open.sh
```
gnome-terminal &
```wvdial-execute.sh
```
wvdial &
```

I don't really understand what you mean with "by clicking the button only", but you can create a launcher and in the command field, add the path to your sh script ( or enter your command .. depends on what you need it to do ).

friend

i am going to create a button in gui

I want to execute "wvdial" command when i pressing the button only

what i have to do?
how i can use this .sh file for my operation?

---

### Post by credobyte on 2009-09-09
A button in GUI ? What that means ? You need to be more specific, what language and API you are using ?

---

### Post by zhanglini on 2009-09-09
maybe he meant having a launcher in the panel which has the command to open the terminal?
Maybe you can just drag the terminal from "Apps" menu to the panel....

---

### Post by navaneethan on 2009-09-09
> **credobyte said:**
> A button in GUI ? What that means ? You need to be more specific, what language and API you are using ?


I am going to use java just like that gppp when we provide the username and password 

it calls wvdial

similar that i want to execute the wvdial by providing my username and password for my modem

Is it possible to perform this operation using sh file only?

that means,

step1: our application starts

step2: provide the username and password and dialer number

step3: click the "Connect" button"

step 4: here i want to execute the command "wvdial" in terminal(note: i don't open terminal,it responses automatically)..

---

### Post by navaneethan on 2009-09-09
> **credobyte said:**
> A button in GUI ? What that means ? You need to be more specific, what language and API you are using ?


I am going to use java just like that gppp when we provide the username and password 

it calls wvdial

similar that i want to execute the wvdial by providing my username and password for my modem

Is it possible to perform this operation using sh file only?

that means,

step1: our application starts

step2: provide the username and password and dialer number

step3: click the "Connect" button"

step 4: here i want to execute the command "wvdial" in terminal(note: i don't open terminal,it responses automatically)..

---

### Post by credobyte on 2009-09-09
I don't think that it's possible, however, you should check wvdial man pages. There might be a way to connect via command line ( in that way, you could just execute it as a command, not launch it, try to click on buttons, etc. ).

---

### Post by stumbleUpon on 2009-09-09
Suppose you define a button and in the actionListener method for that button, run a system command (as credobyte mentioned) to launch the program you want. So that when the button is clicked, the program is launched.

Does this help? I haven't tried this myself.

---

### Post by dearingj on 2009-09-09
try putting this in your script:
```
gnome-terminal --command="wvdial"
```

---

### Post by credobyte on 2009-09-09
> **dearingj said:**
> try putting this in your script:
```
gnome-terminal --command="wvdial"
```

And how would he simulate a button click & username/password input ? :) Also, there's no need to use gnome-terminal in [COLOR=Gray]Java system calls[/COLOR].

---

### Post by navaneethan on 2009-09-09
> **dearingj said:**
> try putting this in your script:
```
gnome-terminal --command="wvdial"
```

thanks i ll try

---

