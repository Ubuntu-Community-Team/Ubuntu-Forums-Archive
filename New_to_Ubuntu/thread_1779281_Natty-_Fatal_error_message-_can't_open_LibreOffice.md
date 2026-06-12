---
title: "Natty- Fatal error message- can't open LibreOffice Calc"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by sewbiz on 2011-06-10
When I try to open a document or spreadsheet in a folder I get a Fatal error message.

[B]"The application cannot be started. A general error occurred while accessing your central configuration."
[/B]
I am now reinstalling all of my Office packages via Synaptic Package Manager.
Is there something else I should be doing. I did the sudo apt-get update and sudo apt-get upgrade at the start of my session.

I am going to reboot and try again.
Any advice is appreciated!  Thank you!

---

### Post by ChipOManiac on 2011-06-10
Please start the program through the terminal... and then try to open a spreadsheet.

Relay the terminal output... it might help us understand what the problem is...

---

### Post by sewbiz on 2011-06-10
> **ChipOManiac said:**
> Please start the program through the terminal... and then try to open a spreadsheet.

Relay the terminal output... it might help us understand what the problem is...

I can start the program.....I can open a folder......I get the error when I want to open a document or spreadsheet within the "folder".

I went to the terminal and started the program and doing it that way I had no problems opening the .doc or .xls.

This was helpful in that, I will know another way to open something, but it is an extra step. It is easier to just click on an icon, open program and etc.

Thank you for your help!!! Not resolved but helpful.

---

### Post by ChipOManiac on 2011-06-10
Did the terminal output any messages that seemed to be of any importance?

As a temporary resolution... just add a new launcher with the following

```
gnome-terminal -e <calc executable>
```

replace <calc executable> with the appropriate (Sorry, I don't use LO)... This launcher will lanch the app through the terminal with one click.... until we resolve the problem ;)

---

### Post by jre6 on 2011-06-10
the command will be "gnome terminal -e libreoffice -calc"

---

### Post by sewbiz on 2011-06-10
> **jre6 said:**
> the command will be "gnome terminal -e libreoffice -calc"

I got command not found....no command gnome found

No command 'gnome' found, did you mean:
 Command 'gnote' from package 'gnote' (universe)
gnome: command not found

---

### Post by sewbiz on 2011-06-10
> **sewbiz said:**
> I got command not found....no command gnome found

No command 'gnome' found, did you mean:
 Command 'gnote' from package 'gnote' (universe)
gnome: command not found


Failed to parse arguments: Unknown option -calc

Still something not right with command.....I am grateful for the help though.;)

---

### Post by sewbiz on 2011-06-10
> **sewbiz said:**
> Failed to parse arguments: Unknown option -calc

Still something not right with command.....I am grateful for the help though.;)

I typed this and it opened the program without a hitch...now how do i make it my new launcher button?
The problem has not been opening the program at all......it is the items inside the folders....unless i use the terminal way of doing things.

[SIZE=3]**gnome-terminal -e libreoffice**[/SIZE]

---

### Post by sewbiz on 2011-06-10
> **ChipOManiac said:**
> Did the terminal output any messages that seemed to be of any importance?

As a temporary resolution... just add a new launcher with the following

```
gnome-terminal -e <calc executable>
```replace <calc executable> with the appropriate (Sorry, I don't use LO)... This launcher will lanch the app through the terminal with one click.... until we resolve the problem ;)


Thank you...I got this happening with 'gnome-terminal -e libreoffice'  command.  But your help is appreciated!!!   :D

---

### Post by Gonzalo_VC on 2011-07-23
I don't see how this thread is considered "solved"!?!?!?
Libreoffice must work properly, without having to type something in the terminal.:(

I have the same error in 10.04 LTS (updated up to this day). Libreoffice works when calling it as root, but not as user. I thought it was something related to folders permission, since I have copied out and back in my files and some of them were accessible only to the root user, but after changing that, re-installing Ubuntu, re-installing (the 3rd time) Libreoffice 3.3, the problem persists.
I also removed some language packs, what got me suspicious about, but -again- after purging and re-installing all of it (LO3.3), it doesn't work, either!

Go figure :confused:

---

