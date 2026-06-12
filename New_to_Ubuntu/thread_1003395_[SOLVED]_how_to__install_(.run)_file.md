---
title: "[SOLVED] how to  install (.run) file"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-06
Hi. I have downloaded Wolfenstein Enemy Territory.

My problem is the linux download is a .run file and I don't know where to begin.

Can someone help?

---

### Post by jolx on 2008-12-06
try double clicking it.
it should come up with some options, click run in terminal

---

### Post by nakama85 on 2008-12-06
> **jolx said:**
> try double clicking it.
it should come up with some options, click run in terminal

when i double click it nothing happens

_note: running 8.10_

---

### Post by jolx on 2008-12-06
ok then
try opening the terminal and cd'ing to the directory it is saved to:
```
cd /home/user/the/directory
```

then runing it:
```
./nameoffile.run
```

---

### Post by nakama85 on 2008-12-06
> **jolx said:**
> ok then
try opening the terminal and cd'ing to the directory it is saved to:
```
cd /home/user/the/directory
```

then runing it:
```
./nameoffile.run
```

I tried and this is the error message I get
> bash: et-linux-2.55.x86.run: command not found

What should I do from here?

---

### Post by 3rdalbum on 2008-12-06
> **nakama85 said:**
> when i double click it nothing happens

_note: running 8.10_

You will need to make it executable by root, and then run it as root from within the terminal. IIRC the installer for Wolfenstein Enemy Territory uses some ancient libraries that you'll need to install from Synaptic Package Manager. If the installer gives you error messages about missing libraries, then grab those libraries from Synaptic.

If you don't understand what I mean about making it executable and running it from the terminal, and if Google doesn't tell you how to do it, then post back here and we'll clarify how to do it.

---

### Post by jolx on 2008-12-06
are you sure you're changing to the right directory and putting in the ./

because it shouldn't give that error message

EDIT: doh! i forgot aboot making it executables soz

---

### Post by nakama85 on 2008-12-06
> **3rdalbum said:**
> You will need to make it executable by root, and then run it as root from within the terminal. IIRC the installer for Wolfenstein Enemy Territory uses some ancient libraries that you'll need to install from Synaptic Package Manager. If the installer gives you error messages about missing libraries, then grab those libraries from Synaptic.

If you don't understand what I mean about making it executable and running it from the terminal, and if Google doesn't tell you how to do it, then post back here and we'll clarify how to do it.

ok I made it executable by doing the following 
```
sudo chmod +x et-linux-2.55.x86.run
```

When I try to run as root I get the same error as above> sudo: et-linux-2.55.x86.run: command not found

---

### Post by 3rdalbum on 2008-12-06
> **nakama85 said:**
> ok I made it executable by doing the following 
```
sudo chmod +x et-linux-2.55.x86.run
```

When I try to run as root I get the same error as above

What directory is the terminal opened in?

Try switching the terminal to root by using this command:

```
sudo su
```

Put in your password if necessary. Then drag and drop the installer file to the terminal; this will automatically put in the command needed to run the file. Now just press enter to run it.

---

### Post by nakama85 on 2008-12-06
> **3rdalbum said:**
> What directory is the terminal opened in?

Try switching the terminal to root by using this command:

```
sudo su
```

Put in your password if necessary. Then drag and drop the installer file to the terminal; this will automatically put in the command needed to run the file. Now just press enter to run it.

Cool thanks. Like you said old dependencies looks like I will need to install them 1 by 1. Thanks for the help

---

### Post by lurnin9 on 2008-12-12
Why is it necessary to type './' before an executable in the current working directory?  Is there a way to tell bash how to figure it out without the path to the current directory, just by typing the name of the executable?  I get 'command not found'.

Thanks

---

### Post by tonymhs2009 on 2008-12-22
> **3rdalbum said:**
> You will need to make it executable by root, and then run it as root from within the terminal. IIRC the installer for Wolfenstein Enemy Territory uses some ancient libraries that you'll need to install from Synaptic Package Manager. If the installer gives you error messages about missing libraries, then grab those libraries from Synaptic.

If you don't understand what I mean about making it executable and running it from the terminal, and if Google doesn't tell you how to do it, then post back here and we'll clarify how to do it.

I would appreciate it if you could clarify that for me please.

Thanks

---

