---
title: "irssi detach"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by norlane on 2011-03-07
Running irssi on latest ubuntu through terminal.
when i am connected to an irc channel i used to be 
able to detach using ctrl and a  then npress d.

For some reason this is not workng now.

I have changed the keyboard but still the same.

Is there a setting to resolve this so i can detach from irssi.

Thank for help.

instructions 
**Detaching**

  There are certain keystrokes that you can make inside of a screen session to control it. The commands are in the format of **Ctrl-a,*letter***, usually. This is executed by pressing the control key and the 'a' key at the same time, releasing both, and then pressing *letter*. At this point you should learn to detach from your screen session. Press **ctrl-a,d**  to do this (Press ctrl-a, release, press d). When this is done, you  should see something like "[detached]" print to your terminal. If you  see this, you're no longer in screen, but Irssi is still running in it,  in the background. For effect, feel free to disconnect from your shell  completely and then log back in before continuing to the next step.

---

### Post by MrPok on 2011-03-08
> **norlane said:**
> ..i *used to* be 
able to detach using..
Do you mean you did this in your current Ubuntu and at some time point it just *stopped* working? Or do you use irc on windows and expected similar operation in Ubuntu?

I don't use irc myself, but perhaps the key binding CTRL-A is reserved by the system for something else, or something changed in your bash commandline settings..? ;)

Good luck!
Paul

---

### Post by aeiah on 2011-03-08
> **norlane said:**
> 
  there are certain keystrokes that you can make inside of a screen session to control it. 
8-[

> **norlane said:**
> 
  there are certain keystrokes that you can make inside of a **[size="4"][screen]("http://www.gnu.org/software/screen/")[/size]** session to control it. 

---

### Post by aeiah on 2011-03-08
maybe on a previous install or whatever, you had ircii actually start inside screen using an alias or something.

---

