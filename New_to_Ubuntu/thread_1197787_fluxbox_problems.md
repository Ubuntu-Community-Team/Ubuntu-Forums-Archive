---
title: "fluxbox problems"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2009-06-26
I just installed fluxbox on a clean install of ubuntu mini on a virtual machine. However once the machine boots up and i log in it boots into the gui, but when i right click and try to start an application, the application wont start! any ideas?

---

### Post by Temposs on 2009-06-26
If you can open a terminal somehow, try to start a program from a command line. Then see what error it gives you.

---

### Post by m_duck on 2009-06-26
It may sound silly, but make sure the application is installed. I can't remember what the default fluxbox menu looks like, but in openbox the default menu has a lot of apps in it, very few of which are installed by default, only xterm etc.

---

### Post by Indian_Guy101 on 2009-06-27
> **Temposs said:**
> If you can open a terminal somehow, try to start a program from a command line. Then see what error it gives you.

That is the whole problem, I can't open a terminal. When I try ctrl + alt + F7 it doesn't open a terminal in the virtual machine, it opens one in my actual os. If i can't open a terminal or any app except run program (which won't run any programs) i don't know what to do. I really don't know how I could even check if the programs are really installed. All i did on the ubuntu mini install was

sudo aptitude install fluxbox

and

sudo aptitude install gdm

That is it. I have no clue at all why nothing works.

---

### Post by snowpine on 2009-06-27
If all you have installed is fluxbox and gdm, then you don't really have any applications to run, now do you? 

Start by installing a terminal (xterm is a good one) and take it from there. You can get to a failsafe terminal in GDM's session menu.

---

### Post by Indian_Guy101 on 2009-06-28
That is the thing, how do i install a terminal?

---

### Post by snowpine on 2009-06-29
> **Indian_Guy101 said:**
> That is the thing, how do i install a terminal?

Log in to failsafe terminal, then 'sudo apt-get install xterm'

---

### Post by Indian_Guy101 on 2009-06-29
And umm... how do i go into failsafe terminal. There is a reason i posted this on Absolute Beginner Talk. I'm still kind of new to ubuntu.

---

### Post by Anzan on 2009-06-29
You can log into failsafe terminal at the gdm login manager: the page presented for logging in.

Does CTL+ALT+F1 not shift to a terminal though? The GUI is just running in tty 7. CTL+ALT+F1 up until 6 should start a terminal.

---

### Post by Indian_Guy101 on 2009-07-06
> **Anzan said:**
> You can log into failsafe terminal at the gdm login manager: the page presented for logging in.

Does CTL+ALT+F1 not shift to a terminal though? The GUI is just running in tty 7. CTL+ALT+F1 up until 6 should start a terminal.

Thanks . ctrl + Alt + f1 does not open a terminal because i have fluxbox installed in a virtual machine. Ctrl-Alt-F1 opens it up outside the virtual machine because i have the virtual machine installed on jaunty.

Also I get an error message when i try to log on to failsafe terminal.

---

