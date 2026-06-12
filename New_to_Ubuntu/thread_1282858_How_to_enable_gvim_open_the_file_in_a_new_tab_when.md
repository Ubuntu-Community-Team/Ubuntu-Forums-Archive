---
title: "How to enable gvim open the file in a new tab when clicking it in nautilus?"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by sundol on 2009-10-04
When a file is opened by gedit in a nautilus, gedit opens them using multiple tabs in a gedit window (gedit is the default editor).

I want to do same thing for gvim.
I know that :tabnew open files in a new tab of currently working gvim window. However, how same things can be done in nautilus?

Thanks.

---

### Post by major.stubble on 2009-10-27
> **sundol said:**
> When a file is opened by gedit in a nautilus, gedit opens them using multiple tabs in a gedit window (gedit is the default editor).

I want to do same thing for gvim.
I know that :tabnew open files in a new tab of currently working gvim window. However, how same things can be done in nautilus?

Thanks.

**DISCLAIMER**: This solution may not be supported by Canonical Ltd. and may have unintended consequences.  Use at your own risk.

```
$ cd /usr/share/applications
$ sudo cp gvim.desktop gvim.desktop_$(date -I)
[sudo] password for user:
$ sudo gvim gvim.desktop

```Look for "Exec=gvim -f %F" (usually line 72).  Modify to say:

```
Exec=gvim -f --remote-tab %F
```Save the file and exit.  Double click on a text file.  Will also work with 'Open With'.  Will *not* work from the command line.  For that you will need to execute:

```
$ gvim --servername GVIM --remote-tab "filename"
```May want to alias that in your ${HOME}/.bashrc.

---

