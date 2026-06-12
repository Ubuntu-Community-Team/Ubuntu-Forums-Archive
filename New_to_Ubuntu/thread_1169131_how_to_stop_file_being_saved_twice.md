---
title: "how to stop file being saved twice?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by listerdl on 2009-05-24
Hi, does anyone know how to stop a file being saved twice?

I use the text editor quite a bit but for some reason files are saved twice, so 'file' becomes 'file~'

How can I stop this duplication?

Thanks!!

---

### Post by Didius Falco on 2009-05-24
Hi,

If you are referring to gedit, go to **Edit/Preferences/Editor** and change the settings there.

Regards,

Didius

---

### Post by Locutus_of_Borg on 2009-05-24
file~ is actually a backup for in case you need to restore an errant save

---

### Post by blueridgedog on 2009-05-24
Many editors will create a lock file named file~ so that other initiations of the editor will see that the file is being edited.  In vi and vim you will get a warning that there is a temporary file and will be asked if you want to attempt to recover.  If your system is leaving those files after you have saved and exited the program, that is a problem. They typically get left if you reboot with an edit session open (even though you have saved the file and do not care to reboot with it open, the application never removes the file~).

---

### Post by Locutus_of_Borg on 2009-05-24
> **blueridgedog said:**
> Many editors will create a lock file named file~ so that other initiations of the editor will see that the file is being edited.  In vi and vim you will get a warning that there is a temporary file and will be asked if you want to attempt to recover.  If your system is leaving those files after you have saved and exited the program, that is a problem. They typically get left if you reboot with an edit session open (even though you have saved the file and do not care to reboot with it open, the application never removes the file~).


do this and tell me if this happens on your system:

```

echo "this is a test" > test
gedit test
<ctrl+s>
<ctrl+q>
ls test*

```

i dont use gedit much for anything, so this is its default behavior.  

and in fact the preferences dialog suggests the ~ files are backups

---

### Post by mcduck on 2009-05-25
> **blueridgedog said:**
> Many editors will create a lock file named file~ so that other initiations of the editor will see that the file is being edited.  In vi and vim you will get a warning that there is a temporary file and will be asked if you want to attempt to recover.  If your system is leaving those files after you have saved and exited the program, that is a problem. They typically get left if you reboot with an edit session open (even though you have saved the file and do not care to reboot with it open, the application never removes the file~).

Files ending with a "~" are not lock files, they are backup files as suggested previously in this thread.

And, as they are backups, their main idea is that they are kept after you finish editing the file. In fact the backup file isn't usually even created until you save a changed version of a file.

---

### Post by lisati on 2009-05-25
I concur that the files with "~" are backups to provide a way of undoing changes you make to a file. The file doesn't actually get saved twice when you click on "save" - what usually happens is something like this:
[LIST=1]
[*]User clicks on "save"
[*]Editor deletes file with "~", if it exists
[*]Editor renames normal file to end with "~", if it exists
[*]Editor save work you've just done with the original name
[/LIST]

---

### Post by blueridgedog on 2009-05-25
> **mcduck said:**
> Files ending with a "~" are not lock files, they are backup files as suggested previously in this thread.



Correct...I was confusing it with .file.swp, which is left behind after a vim editing session that dies.  

Which causes you to get:

E325: ATTENTION
Found a swap file by the name ".file.swp"
          owned by: user   dated: Mon May 25 08:34:26 2009
         [cannot be read]
While opening file "file"
             dated: Mon May 25 08:31:55 2009

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r file"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file ".test.swp"
    to avoid this message.
"test" 1 line, 15 characters

---

