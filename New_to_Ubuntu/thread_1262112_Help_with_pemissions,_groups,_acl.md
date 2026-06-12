---
title: "Help with pemissions, groups, acl"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Ralph L on 2009-09-09
I am trying to set up a multi user system.  I would like each user to be able to control who can see, use, and replace files and folders.  I first attempted to use the classical Linux/Unix permissions of user/owner, group, and others.  This works ok with 2 exceptions:
A.  To permit a file to one other person it is necessary to set up a group with only that person's user name in it.  This is ok except that the group must be set up by the Administrator.  This is a big nuisance for such a common action and slows down user progress.  Is there any way to allow each user (non admin) to create their own local groups?

B.  To allow sharing-users to see a single file/folder in a folder it is necessary to make the entire folder viewable to the sharing user.  This is undesirable in that it lets users sharing a file see what else the file owner is doing.  One possible solution is for the user to limit the contents of the Home folder to contain just 2 folder (Unshared Documents, and Shared Documents.  Then the sharing user can only see these two folders, but this forces all unshared files one level further down in the hierarchy--a big nuisance. Is there any way to limit the sharing users visibility to just the shared folders/files and not to the entire contents of the folder?

I also tried to use the ACL feature, and while this makes it easier to permit a file to a single user, groups must still be created by the administrator, and sharing users have still visibility to files they don't need to know about.  In addition, when I copy a file, even if I use cp under Terminal, the ACL permissions are lost.  Is there any way to copy a file with ACL permissions and have them retained in the new file?

Thanks for any help

Ralph

---

### Post by KIAaze on 2009-09-13
A) Maybe you could allow non-admins to create groups by using the 
/etc/sudoers file and eventually some custom scripts.
[http://www.gentoo.org/doc/en/sudo-guide.xml](http://www.gentoo.org/doc/en/sudo-guide.xml)

My suggestion would be to create a script which allows creating/removing groups and adding/removing people from them, but only in such a way that users can only modify their own groups.(you could use automatic prefixes for created groups. ex: if joe creates group "family", it will create group "joe_familiy")

Then you can add a rule to sudoers, so that users can run the script with sudo.

I don't know exactly how to identify who is running a command with sudo, but I think it's possible.

This will probably be complex, so it increases the security risks.

Two security tips for writing scripts to be used with sudo:
1)**ALWAYS USE ABSOLUTE PATHS!** (just using program/script names without path is also ok if you make sure the PATH variable is reset by sudo (default I think) )
This prevents users from creating custom scripts and moving into the appropriate directory to run them. (I used this exploit successfully once on one of my own scripts.)

2)Make the scripts unreadable by users. This makes it harder for them to find exploits.

B)
I didn't even know about the ACLs before. But apparently ACLs are supposed to be moved/copied when using mv/cp:
> The cp and mv commands copy or move any ACLs associated with files and directories.
[http://www.softpanorama.org/Access_control/acl.shtml](http://www.softpanorama.org/Access_control/acl.shtml)

> Is there any way to limit the sharing users visibility to just the shared folders/files and not to the entire contents of the folder?
With the standard unix permissions, you can't prevent someone from listing the contents of a directory containing a shared file, but you can prevent them from opening it, as well as from listing the contents of any unshared directory.
ex:
```
[66][~]$  ls -ld test/
d------r-x 3 root root 4096 2009-09-13 09:02 test/
[67][~]$  ls -l test/
total 4
---------- 1 root root    0 2009-09-13 08:59 tata
-------r-- 1 root root    0 2009-09-13 08:59 toto
d--------- 2 root root 4096 2009-09-13 09:02 tutu
[68][~]$  cat test/tata
cat: test/tata: Permission denied
[69][~]$  cat test/toto
[70][~]$  ls test/tutu/
ls: cannot open directory test/tutu/: Permission denied
[71][~]$

```

---

### Post by mcduck on 2009-09-13
A) Create a new qroup, an add both user's to that group. Now they can set file's ownership to that group, and access any files assigned to that group. You only need root privileges to set up the group and add those users to it, after that root permissions are not required.

I must admit I didn't quite understand what you meant with "To permit a file to one other person it is necessary to set up a group with only that person's user name in it", since that's not true at all, and you definitely don't need to create new groups with existing user's names, the groups already exist. Anyway, as long as both users belong to one common group they can simply set file to belong to that group and it will be accessible to both users.

B) Create your shared directory somewhere else than inside one user's home directory. If you want, you can then symlink it into those user's homes for easier access.

---

### Post by Ralph L on 2009-09-13
I found at least one method to copy files and retain ACL permission.   That is to use the --preserve all, or the -p, option on cp.  It may also be possible to use scp with the same option.  I will start using this for backup, since I do a simple copy to backup files.  I think a simple copy is safer than using tar or some other format that gathers files for backup into a single large file.  I have had these fail on restore.

I could not find any way to do a copy, retaining ACL permissions, using a gui.  Nautilus won't do it and I could find no Nautilus extensions that would do it.  Anybody know of a gui for this purpose.

Ralph

---

### Post by KIAaze on 2009-09-14
You can write your own nautilus script to do it. It's really easy if you already know how to write bash script, which is easy if you know how to use the command-line. :)

Here are some tutorials:
[https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto) (best)
[https://help.ubuntu.com/community/Nautilus_Scripts#Copy%20To](https://help.ubuntu.com/community/Nautilus_Scripts#Copy%20To) (contains copy script!)
[http://linuxtuts.blogspot.com/2008/07/nautilus-scripts-for-making-small.html](http://linuxtuts.blogspot.com/2008/07/nautilus-scripts-for-making-small.html)
[http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

And the nautilus script archive with lots of custom scripts:
[http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php)

One of the links above had CopyTo amd MoveTo scripts and I just added the "--preserve=all" option:

copyto_preserveall.sh:
```
#!/bin/bash
# To copy selected files to a location

LOCATION=$(zenity --file-selection --directory --title="Select a directory") || exit

IFS=$'\n'
for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    if [ -e "$LOCATION"/"$(basename $FILENAME)" ];then
       zenity --question --title="Conflict While Copying" --text="File ""$LOCATION"/"$(basename $FILENAME)"" already exists. Would you like to replace it?"
       case "$?" in
          1  )  exit 1 ;;
          0  )  cp --preserve=all -a -- "$FILENAME" "$LOCATION" ;;
       esac
    else
       cp --preserve=all -a -- "$FILENAME" "$LOCATION"
    fi
done

```

moveto_preserveall.sh:
```
#!/bin/bash
# To move selected files to a location

LOCATION=$(zenity --file-selection --directory --title="Select a directory") || exit

IFS=$'\n'
for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    if [ -e "$LOCATION"/"$(basename $FILENAME)" ];then
       zenity --question --title="Conflict While Moving" --text="File ""$LOCATION"/"$(basename $FILENAME)"" already exists. Would you like to replace it?"
       case "$?" in
          1  )  exit 1 ;;
          0  )  mv --preserve=all -f -- "$FILENAME" "$LOCATION" ;;
       esac
    else
       mv --preserve=all -- "$FILENAME" "$LOCATION"
    fi
done

```

Save the scripts as "copyto_preserveall.sh" and "moveto_preserveall.sh" (or whatever name you want) in the "~/.gnome2/nautilus-scripts" directory and then run:
```
chmod +x ~/.gnome2/nautilus-scripts/*.sh
```

They should now be available in the context menu of nautilus under "Scripts".

Now, I haven't tested this yet (don't know how to set/get ACLs), but it should do what you want. :)

Here's also a simple example I used to get an idea of the variables passed by nautilus:
```
[18][~/.gnome2/nautilus-scripts]$  cat ./echo.sh
#!/bin/bash
echo NAUTILUS_SCRIPT_SELECTED_FILE_PATHS = $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS >~/nautilus.log
echo NAUTILUS_SCRIPT_SELECTED_URIS = $NAUTILUS_SCRIPT_SELECTED_URIS >>~/nautilus.log
echo NAUTILUS_SCRIPT_CURRENT_URI = $NAUTILUS_SCRIPT_CURRENT_URI >>~/nautilus.log
echo NAUTILUS_SCRIPT_WINDOW_GEOMETRY = $NAUTILUS_SCRIPT_WINDOW_GEOMETRY >>~/nautilus.log
[19][~/.gnome2/nautilus-scripts]$  cat ~/nautilus.log
NAUTILUS_SCRIPT_SELECTED_FILE_PATHS = /home/kiaaze/.gnome2/accels /home/kiaaze/.gnome2/eog /home/kiaaze/.gnome2/gedit
NAUTILUS_SCRIPT_SELECTED_URIS = file:///home/kiaaze/.gnome2/accels file:///home/kiaaze/.gnome2/eog file:///home/kiaaze/.gnome2/gedit
NAUTILUS_SCRIPT_CURRENT_URI = file:///home/kiaaze/.gnome2
NAUTILUS_SCRIPT_WINDOW_GEOMETRY = 800x550+632+283

```

The selected files can also be referred to with the more traditional "$@" and "$*" bash variables.
From the bash manual:
```
   Special Parameters
       The shell treats several parameters specially.  These parameters may only be referenced; assignment to them is not allowed.
       *      Expands to the positional parameters, starting from one.  When the expansion occurs within double quotes, it expands to a single word with the value of each parameter separated by the
              first character of the IFS special variable.  That is, "$*" is equivalent to "$1c$2c...", where c is the first character of the value of the IFS variable.  If IFS is unset, the param&#8208;
              eters are separated by spaces.  If IFS is null, the parameters are joined without intervening separators.
       @      Expands  to  the  positional parameters, starting from one.  When the expansion occurs within double quotes, each parameter expands to a separate word.  That is, "$@" is equivalent to
              "$1" "$2" ...  If the double-quoted expansion occurs within a word, the expansion of the first parameter is joined with the beginning part of the original word, and the  expansion  of
              the last parameter is joined with the last part of the original word.  When there are no positional parameters, "$@" and $@ expand to nothing (i.e., they are removed).
```

edit:
If you use Konqueror/KDE:
[http://lindesk.com/2008/10/action-context-custom-service-menus-konqueror/](http://lindesk.com/2008/10/action-context-custom-service-menus-konqueror/)
Just discovered this. :)

---

### Post by Ralph L on 2009-09-17
KIAaze

Thank you very much for your detailed instructions.  I don't know how to write scripts but with all your examples, I am going to learn.  It will be a few days before I get to try anything, but again thank you.

Ralph

---

