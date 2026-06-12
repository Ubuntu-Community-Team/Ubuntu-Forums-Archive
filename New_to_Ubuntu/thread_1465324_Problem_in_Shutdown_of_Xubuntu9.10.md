---
title: "Problem in Shutdown of Xubuntu9.10"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Dactula on 2010-04-29
Hi All,

I am new to Linux and trying out Xubuntu9.10 live CD from CD-ROM drive of  my old PentiumIII PC. I can't shutdown or restart the PC while using Xubuntu. I have tried the Quit button on the top right corner of the desktop as well as the log out option but that didn't work. I downloaded the free Ubuntu guide from this community but that seems to be Ubuntu specific. Is there any guide or ebook available for free download specifically meant for Xubuntu ? Please help.

---

### Post by jvc26 on 2010-04-29
What happened when you clicked the button at the top right of the screen?

J

---

### Post by Kakers on 2010-04-29
This doesn't really help you much in the way of fixing the problem but you can try this:

Open up a Terminal window "Applications -> Accessories -> Terminal" and type the following to try and shutdown:

> sudo shutdown -h now

---

### Post by Dactula on 2010-04-29
> **jvc26 said:**
> What happened when you clicked the button at the top right of the screen?

J

most buttons disappeared from the top bar of the desktop but not the icons on the desktop like file system etc . I waited for about 5 minutes but no menu for any options appeared and the machine didn't shutdown.  I had to switch off the power ultimately.

---

### Post by Paddy Landau on 2010-04-29
Old computers often have a problem with something called ACPI. (I don't know what it means, but it solved my problem on an Xubuntu installation of mine.)

When you start your Live CD, *before* you choose "Try Xubuntu without making any changes to your computer":

[LIST]
[*]Press F6
[*]Use your down-arrow to choose **acpi=off** and press Enter to select it.
[*]Press Esc
[/LIST]
Then continue to "Try Xubuntu without making any changes to your computer".

If that doesn't work, repeat the process and also choose **noapic**.

If that also doesn't work, then sorry, I don't know how to fix it.

---

### Post by Dactula on 2010-04-30
@ Kakers & Paddy

Thanks for your tips. I ultimately needed to use both methods  you two suggested to fix the problem. During booting the live cd I pressed F6 and followed Paddy's instructions and later followed Kaker's tips as the Quit button didn't work even then. Following Kaker's instructions alone almost worked but the machine hanged with the message "system halted" on the monitor screen. Thanks a lot once again. This problem is solved.

---

### Post by Paddy Landau on 2010-04-30
Good news, I'm glad it worked.

Please mark the thread as solved.

---

