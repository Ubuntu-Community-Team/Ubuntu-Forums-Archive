---
title: "Start the network tool"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by andlinux on 2006-07-25
Hi

I have accidentaly removed the network button in System > Management (?) > Network (?)

Is there a command to start that tool, so that I can configure my wireless card ?

---

### Post by philippe_carlo on 2006-07-25
```
gksu network-admin
```

You can re-create the launcher with this command.

---

### Post by andlinux on 2006-07-25
> **philippe_carlo said:**
> ```
gksu network-admin
```

You can re-create the launcher with this command.
I did that but I can't see a thing to start it ?

---

### Post by andlinux on 2006-07-26
What can I do now ?

---

### Post by tturrisi on 2006-07-26
how did you "accidentally delete" it from the menu?  Is is available to be put back using the Alacarte Menu editor? (put a check next to it & restart gnome panel.)

---

### Post by andlinux on 2006-07-27
I think I accedentially did that because it was gone on one day. :confused:

But if I somebody can give me the command to start it in the console is also good.

---

### Post by tturrisi on 2006-07-27
andlinux already gave you the command.

---

### Post by andlinux on 2006-07-27
I'm andlinux and that command didn't worked, it doesn't bring the netwerk button back.

---

### Post by jrjr on 2006-07-27
This works

gksu network-admin

---

### Post by andlinux on 2006-07-27
That command works, but I see no "network" (or something like that) in the system > management menu. The only thing I see is Network tools.

---

### Post by jrjr on 2006-07-27
Right click a blank area of the desktop and choose 'Create Launcher' from the menu.

For the name call it anything you like... network something or other.

In the Command box place the same code you put in the terminal. 

You now have a custom launcher on your desktop. 

You can do the same thing in the menu. Start the Alacarte menu editor. Click Administration once to select it. Click the file menu and choose new entry. Fill that out the same as you did for the desktop launcher. 

:mrgreen:

---

### Post by andlinux on 2006-07-27
> **jrjr said:**
> Right click a blank area of the desktop and choose 'Create Launcher' from the menu.

For the name call it anything you like... network something or other.

In the Command box place the same code you put in the terminal. 

You now have a custom launcher on your desktop. 

You can do the same thing in the menu. Start the Alacarte menu editor. Click Administration once to select it. Click the file menu and choose new entry. Fill that out the same as you did for the desktop launcher. 

:mrgreen:
When I click on the icon I get a screen to give the administrator password but then after that, nothing happens :s

---

### Post by jrjr on 2006-07-27
It is asking for your password. Put yours in and try it again.

---

### Post by andlinux on 2006-07-27
> **jrjr said:**
> It is asking for your password. Put yours in and try it again.
I did that and I tried it again.

---

