---
title: "Executable Text File Dialog"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by RealG187 on 2009-09-11
When I open files on FAT/NTFS (Windows) volumes Ubuntu presents me with a dialogue box like the one in the attachment. How can I make it so it just opens the file normally?

---

### Post by Elcid247 on 2009-09-11
in nautilus (file browser) go to edit-> preferences

in the behaviour tab, set the behaviour for Executable text files to view executable text files when opened.

i tried fixing it by running sudo chmod -x recursively on my NTFS text files but for some reason it doesnt work :S

---

### Post by mcduck on 2009-09-11
> **Elcid247 said:**
> in nautilus (file browser) go to edit-> preferences

in the behaviour tab, set the behaviour for Executable text files to view executable text files when opened.

i tried fixing it by running sudo chmod -x recursively on my NTFS text files but for some reason it doesnt work :S

The reason would be that NTFS doesn't support Unix-style file ownerships and permissions. You can't use chmod or chown with NTFS file systems. It has no way to handle the permissions.

---

### Post by RealG187 on 2009-09-11
> **mcduck said:**
> The reason would be that NTFS doesn't support Unix-style file ownerships and permissions. You can't use chmod or chown with NTFS file systems. It has no way to handle the permissions.Ya I understand that the dialog box appears because of the permissions which NTFS doesn't have. But why would it default to that? Doesn't that dialog box appear when "Allow executing file as program" is on? So wouldn't it not show up by default?

Anyways, the preferences helped.

While on the subject, is there a way I can type Unix commands into a text file and run them like a batch file on DOS.

---

### Post by falconindy on 2009-09-12
> **RealG187 said:**
> While on the subject, is there a way I can type Unix commands into a text file and run them like a batch file on DOS.
Sure. Start your file with:
```
#! /bin/bash
```
Continue on and write your script... then when you're done, you'll need to make it executable, so:
```
chmod +x filename
```

---

### Post by RealG187 on 2009-09-13
So you start with "#! /bin/bash" then add the commands, mark it as executable or say to execute in the dialog box I posted?

---

### Post by RealG187 on 2010-03-09
Okay ya now I know about shell scripts and since changing nautilus' behaviour for executable text file to view them I can't run them.

How can I run shell scripts from Nautilus without making it ask me to run every text file on a non-unix filesystem?

---

### Post by RealG187 on 2010-03-17
I tried adding "gnome-terminal" and "bash" custom commands to the open with tab but it didn't work :(

Is there a custom command I can add to open with to make it so I can execute shell scripts from the open with menu?

---

### Post by patchwork on 2010-03-17
Have you looked into [app runner]("http://hacktolive.org/wiki/App_Runner")?

It will add a line to the menu (right-click) that allows you to run scripts.

If it is only one script that you want to run, you could use a keyboard shortcut or launcher, with the command

```
gnome-terminal -e /path/to/script
```

Did you make the script executable before trying to run it in bash or gnome-terminal?
```
sudo chmod +x /path/to/script
```

---

