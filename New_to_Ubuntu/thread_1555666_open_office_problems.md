---
title: "open office problems??????"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Where Do I Begin on 2010-08-18
I keep getting "OpenOffice.org" document recovery everytime I use openoffice writer
 
I've tried unistalled and reinstall loads of times but cannot get understand why I keep getting the message
 
Any help please?

---

### Post by lykeion on 2010-08-18
To stop the recovery process (assuming you are using OpenOffice 3), 
you can delete the file ~/.openoffice.org/3/user/registry/data/org/openoffice/Recovery.xcu```
rm ~/.openoffice.org/3/user/registry/data/org/openoffice/Recovery.xcu
```
Beware, it resets the settings for Autosave in the 
Tools > Options > Load/Save > General dialog

Hope this helps...(and if so please tag this thread as SOLVED)

---

### Post by Where Do I Begin on 2010-08-18
Hello
> **lykeion said:**
> To stop the recovery process (assuming you are using OpenOffice 3)
it says openoffice 3.2.1
 
> **lykeion said:**
> you can delete the file ~/.openoffice.org/3/user/registry/data/org/openoffice/Recovery.xcu```
rm ~/.openoffice.org/3/user/registry/data/org/openoffice/Recovery.xcu
```
how do i do that?
 
 
 
> **lykeion said:**
> Beware, it resets the settings for Autosave in the 
Tools > Options > Load/Save > General dialog
sorry but I've no idea what that means

---

### Post by Vaphell on 2010-08-18
open terminal and paste the line with middle click after you highlight it here

it means that once you delete the file, all autosave-related settings under Tools > .... are reset to default values.

---

### Post by Where Do I Begin on 2010-08-18
Hello
> **Vaphell said:**
> open terminal
what's terminal?
 
> **Vaphell said:**
> and paste the line 
 
Is this what I have to copy and paste?
 
rm ~/.openoffice.org/3/user/registry/data/org/openoffice/Recovery.xcu

---

### Post by LowSky on 2010-08-18
go to your home folder (the one where your documents, music and videos are storeds)

On the keyboard press CTRL and H at the same time. A bunch of hidden folders will then be shown

find the one named** .openoffice.org**
clcik on it then click on **3**, then click on **user**, then click on **data**, then click on **org**, then click on **openoffice**, then find the file named **Recovery.xcu** and delete it


hope that helps

---

### Post by clive littlewood on 2010-08-18
Hi

From one silver surfer to another  ;)

The terminal is located Accessories > Terminal

When you have that open copy and paste the line into it.

You will probably asked for your password.

When typing the text will not appear, this is OK

Then enter and your prob should be solved.

Clive

---

### Post by Where Do I Begin on 2010-08-18
Under hidden folders under my documents I've got as far as openoffice.org 302 (en-GB) when I click on the + some folders open 
Java
Licenses
readmes
redist
 
None of the folders above show user / data /  org etc., etc
 
Sorry for any confusion

---

### Post by Where Do I Begin on 2010-08-18
Hello Clive
 
Phew, what a nightmare, was never like this when I was at school :D
 
I done all programmes / accessories / but cannot see terminal
 
I can see hyper terminal under all programmes / accessories / accessibility

---

### Post by Vaphell on 2010-08-18
try alt+f2, gnome-terminal

---

### Post by Where Do I Begin on 2010-08-18
> **Vaphell said:**
> try alt+f2, gnome-terminal
 
Humm, nothing seems to happen

---

### Post by Vaphell on 2010-08-18
do you use standard ubuntu using gnome environment?

---

### Post by Where Do I Begin on 2010-08-18
> **Vaphell said:**
> do you use standard ubuntu using gnome environment?
 
 
I don't know what that means (sorry)
 
I have windows XP installed

---

### Post by Vaphell on 2010-08-18
lol :D forget anything you've read here, though reportedly the actual solution tailored for windows is similar - to delete 1 file
[http://www.oooforum.org/forum/viewtopic.phtml?t=65016](http://www.oooforum.org/forum/viewtopic.phtml?t=65016)

---

### Post by lykeion on 2010-08-19
> **Where Do I Begin said:**
> I don't know what that means (sorry)
 
I have windows XP installed

Oh, man. I guess everyone assumes you are using Ubuntu since you are posting in the Ubuntu Forums :-)

See this link:
[U][url=http://katana.oooninja.com/w/openoffice.org/troubleshooting#openoffice.org_is_stuck_in_an_endless_recovery_loop]
Troubleshooting OpenOffice: stuck in an endless recovery loop[/url][/U]

---

