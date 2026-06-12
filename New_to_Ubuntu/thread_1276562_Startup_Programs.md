---
title: "Startup Programs"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by TiredBird on 2009-09-27
Every time I start 9.04 (with Gnome desktop) I get a terminal window on my desktop. I would like to eliminate this. I have searched high and low and cannot find out how to do it. Will someone please tell me how to stop this.

---

### Post by mikeyphi on 2009-09-27
Have you checked under Systems-Preferences-Sessions
to see if it's included as a start-up program?

---

### Post by blackened on 2009-09-27
> **mikeyphi said:**
> Have you checked under Systems-Preferences-Sessions
to see if it's included as a start-up program?

Which, in 9.04, is now System -> Preferences -> Startup Applications. Also remember to uncheck "Automatically remember running applications when logging out" in the Options tab, which might also be the culprit.

---

### Post by mikeyphi on 2009-09-27
> **blackened said:**
> Which, in 9.04, is now System -> Preferences -> Startup Applications. Also remember to uncheck "Automatically remember running applications when logging out" in the Options tab, which might also be the culprit.

Good catch!!

---

### Post by Ratscallion on 2009-09-27
> **blackened said:**
> which, in 9.04, is now system -> preferences -> startup applications. Also remember to uncheck "automatically remember running applications when logging out" in the options tab, which might also be the culprit.
+1

---

### Post by TiredBird on 2009-09-27
I appreciate everyone's help but no joy!

I have even gone so far as to uncheck all the boxes in the startup list, (system->preferences->startupApplication). I have also checked to next tab, (options), and the 'Automatically...' box is unchecked. 

I have been pulling my hair out over this one for a couple of months now. I have done google searches and searched this forum and can't find the solution. I hope someone knows what is causing it.

P.S. I have 9.04 installed on another machine and I don't have the problem there. That was a clean install but this machine was originally running Kubuntu 9.04. Could there be something left over from that install that is causing the problem?

---

### Post by TiredBird on 2009-10-06
> **TiredBird said:**
> I appreciate everyone's help but no joy! ... I have been pulling my hair out over this one for a couple of months now...this machine was originally running Kubuntu 9.04. Could there be something left over from that install that is causing the problem?

Any suggestions?

---

### Post by Sir Jasper on 2009-10-06
Hi,

I do not hold out any great hopes, but if you could load System Monitor find it under Processes and  click on it and then click End Process (bottom RH corner).

My regards

---

### Post by TiredBird on 2009-10-11
> **Sir Jasper said:**
> ...I do not hold out any great hopes...

I did as you suggested and I could end the process, but that is not the problem. I have always been able to end it easily enough. The problem is how do I keep it from starting up every time I reboot my computer.

In spite of the fact that your suggestion did not solve my problem, it did lead me to some information that I did not previously have.

As a result of running the system monitor, I now know that it was started by 'x-session-manager' and that it was started with a command line of 'gnome-terminal --sm-client-id (long hex number) --sm-client-state-file /home/myUserId/.config/session-state/gnome-terminal-1242061555.desktop'.

I am about to investigate the file identified as the '--sm-client-state-file' and see if that offers any clues.

Thanks for your help.

---

### Post by Mr. Picklesworth on 2009-10-11
Ah, what happened is that you had, at some point, checked the box or pressed the button to save your session when you log out in the Startup Applications preferences. In a rather incredible fit of shortsightedness, there is no button to revert this. (Don't worry; bug is filed).

Two things you should do: If you don't want session saving, head back to Startup Applications, go to the Session tab, uncheck the box to remember running apps. (To be honest, that feature doesn't work well at the moment. Haven't tried it in Karmic, though. It used to, so we just have to wait for the dust to settle around the big changes from a while ago).
Now, go to ~/.config and delete the session-state directory.

---

### Post by TiredBird on 2009-10-11
> **Sir Jasper said:**
> ...I do not hold out any great hopes...
Thanks to you Sir Jasper I can put a SOLVED on this thread and to a problem that has plagued me for several months.

To explain what I found - 

The path ~/.config/gnome-session/saved-session/ contained a number of files that had apparently been saved at some time or other when I wanted it to start up from the last session. It would seem that they did not get removed when I cleared that option. 

I eliminated the problem by removing all the files in that directory. 

Thanks again for your suggestion and thanks to all others who tried to help.

---

### Post by TiredBird on 2009-10-11
> **Mr. Picklesworth said:**
> Ah, what happened is that you had, at some point, checked the box or pressed the button to save your session when you log out in the Startup Applications preferences. ... Now, go to ~/.config and delete the session-state directory.

Where have you been all these months?

At the same time you were posting this I was offline discovering the same things. (See my last post.) I only realized that you had made your post when I checked to be sure the 'SOLVED' had been added to the thread. 

Anyway thanks. Your post would have been my salvation had I not just found it by accident.
Hopefully you'll be around next time I have a problem.

---

