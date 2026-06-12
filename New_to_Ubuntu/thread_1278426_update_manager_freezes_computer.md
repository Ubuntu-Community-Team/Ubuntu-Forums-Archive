---
title: "update manager freezes computer"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by mikeprosceo on 2009-09-29
My update manager freezes my computer and packet manager doesn't work.  I am using ubuntu 8.4 and have 19 updates waiting to download.  Can someone please help?  Thank you - Mike Prosceo

---

### Post by drs305 on 2009-09-29
Can you run it from terminal:
```

sudo apt-get update && sudo apt-get upgrade

```
If not, post the error messages.

---

### Post by mikeprosceo on 2009-09-30
Thank you so much.  That solved getting the updates but my Synaptic Package Manager, Software Sources, Windows Wireless Drivers, Update Manager and my Hardware Drivers menue will not start.  I click on them and see the little wheel spin but then the wheel just disappears and nothing happens. The Update Manager still seems to freeze my computer also. Any Ideas?  Thank You

---

### Post by rajeev1204 on 2009-09-30
> **mikeprosceo said:**
> Thank you so much.  That solved getting the updates but my Synaptic Package Manager, Software Sources, Windows Wireless Drivers, Update Manager and my Hardware Drivers menue will not start.  I click on them and see the little wheel spin but then the wheel just disappears and nothing happens. The Update Manager still seems to freeze my computer also. Any Ideas?  Thank You

When update manager starts, leave the system idle and dont keep clicking.It will be back to normal in a few seconds.

---

### Post by mikeprosceo on 2009-09-30
Unfortunately that is not the case.  The time wheel keeps spinning and I can't close the update manager box.  I have left it for a half hour and came back to find it still stuck.  Besides that my packet manager and other things I stated in a previous post do not work.  Is there a bug or virus?  Please help.

---

### Post by drs305 on 2009-09-30
Try opening Synaptic in a terminal. It probably won't work but you may get an error message which will provide information on what the problem is:
```

gksu synaptic
gksu update-manager

```

You can also try the following. If the message says the package was held back, you can try to manually add the name of the package (but don't "force" it yet).
```

sudo apt-get upgrade
*if you see packages that it wants to install but won't:*
sudo apt-get install *packagename*

```
Again, provide us with any error messages you get.

---

### Post by mikeprosceo on 2009-10-01
Thank you so much.  That seemed to work.  It took me quite a number of tries to get the 23 updates, but it finally finished.  I downloaded the ubuntu virus programs from the packet manager, which finally worked, to install on the computer in case this might have been a virus.  Everything seems to work now.  Thank you again.  I was a windows person for many years but now really enjoy working in ubuntu and hope someday to be able to master it.  This forum and all the help it gives is great.  Do you have any idea what the problem was?  Thanks again - Mike Prosceo

---

### Post by drs305 on 2009-10-01
Mike, 

Glad you got everything installed. Linux and Ubuntu don't suffer from viruses, which doesn't mean things don't get messed up from time to time without any external help.  ;-)

If you run into a problem with a GUI app it is often helpful to try to start it in a terminal with it's run command. The generated errors are often self-explanatory and may tell you what command to run to try to fix it. If not, posting the error messages here will generally prompt someone to respond with a possible solution.

Finally, when you don't desire any further response to the original problem, would you please mark the thread SOLVED. You can do this via the "Thread Tools" link at the top right of the original post (it's also reversible if necessary). Marking a thread solved helps others looking for solutions and lets others focus on unresolved issues.

Happy Ubuntu-ing.

---

