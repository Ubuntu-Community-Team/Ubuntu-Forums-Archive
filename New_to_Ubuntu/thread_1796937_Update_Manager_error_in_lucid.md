---
title: "Update Manager error in lucid"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by tinkles on 2011-07-04
I get this error message when I try to open update manager in lucid:

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'le/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list, E:The list of sources could not be read.' "

Can anyone help me with this.  I am a newbie.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by drs305 on 2011-07-04
tinkles,

Welcome to the Ubuntu forums.

You have an incorrect line in one of the files used to retrieve the list of available packages. Specifically, the file is */etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list*

You can edit the file as root (since it's a system file) with the following. Open a terminal or (ALT-F2) and:
```
gksu gedit /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list
```
If you don't recognize the error on the first line, post the contents and we can help you.

If you aren't using Lucid, you can open Synaptic, then go to Settings > Repositories > Other Software tab and untick the setting for "mozillateam..." to get rid of the offending file.

---

### Post by tinkles on 2011-07-04
Something is wrong with my computer this what my terminal reads:

hamfreth@hamfreth-laptop:~$ gksu gedit /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.listhamfreth@hamfreth-laptop:~$

---

### Post by drs305 on 2011-07-04
Can you just run:
```
gksu gedit
```
and then navigate to the folder?

If you were trying ALT-F2, try opening the terminal via Applications, Accessories, Terminal.

If you have problems you might try rebooting to see if that clears things in the terminal.

---

### Post by tinkles on 2011-07-17
This what I get :

hamfreth@hamfreth-laptop:~$ gksu gedit
hamfreth@hamfreth-laptop:~$

---

### Post by ercferret18 on 2011-07-17
Try typing Alt+F2 then typing in 'gksu gedit' (without the quotes)

---

### Post by tinkles on 2011-07-17
I tried doing that but got this in the terminal:

hamfreth@hamfreth-laptop:~$ gedit
The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
hamfreth@hamfreth-laptop:~$ sudo apt-get install gedit
E: Type 'le/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list
E: The list of sources could not be read.
hamfreth@hamfreth-laptop:~$ 


I still have the problem

---

### Post by ercferret18 on 2011-07-17
Try this:
```
sudo nano /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list
```

---

### Post by tinkles on 2011-07-17
This is what I get now:


 GNU nano 2.2.2 File: ...ist.d/mozillateam-firefox-stable-lucid.list           

le/ubuntu lucid main


















                                [ Read 1 line ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by ercferret18 on 2011-07-17
Try deleting that line from the file and saving it. Then see if you can run "sudo apt-get update" in a terminal.

---

### Post by tinkles on 2011-07-17
I really new.  How does ones delete the line from the file in the terminal.  Or how does one get to delete the line from the file. I tried backspacing the words at the bottom of the terminal.but that didn't work.

---

### Post by ercferret18 on 2011-07-17
Here's a simple command:

"sudo echo -n > /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list"

Run this after you exit from nano

---

### Post by tinkles on 2011-07-17
What is nautilus?

---

### Post by ercferret18 on 2011-07-17
I meant nano

---

### Post by tinkles on 2011-07-17
Sorry .  How does one exit from nano?

---

### Post by ercferret18 on 2011-07-17
Press Crtl+X and then press n

---

### Post by tinkles on 2011-07-17
Now I get this :

hamfreth@hamfreth-laptop:~$ sudo echo -n > /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list
bash: /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list: Permission denied
hamfreth@hamfreth-laptop:~$

---

### Post by ercferret18 on 2011-07-17
Oops:confused: I meant this:

echo -n | sudo tee /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list

---

### Post by tinkles on 2011-07-17
Now this what I get:

hamfreth@hamfreth-laptop:~$ echo -n | sudo tee /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list
[sudo] password for hamfreth: 
hamfreth@hamfreth-laptop:~$

---

### Post by ercferret18 on 2011-07-17
Ok, it worked. Now try "sudo apt-get update" and see what happens...

---

### Post by tinkles on 2011-07-18
It worked![IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]  Thank you very much, ercferret18.  I really appreciate your help.  I could not get back to the forum last because the power went off.  Where do you go to learn this ubuntu terminal language?

Tinkles

---

### Post by ercferret18 on 2011-07-18
> **tinkles said:**
> It worked![IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]  Thank you very much, ercferret18.  I really appreciate your help.  I could not get back to the forum last because the power went off.  Where do you go to learn this ubuntu terminal language?

Tinkles

Here's a good link:
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

---

