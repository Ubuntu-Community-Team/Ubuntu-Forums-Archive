---
title: "Files ending in ~"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by amcavoy on 2009-12-18
I have tried to use "clean" and "autoclean" to get rid of the files ending in ~ but it doesn't work (after I move example.ext, I end up with example.ext~ for instance).  How do I get rid of these files?

---

### Post by herbertportillo on 2009-12-18
You can easily remove them by typing
```
rm example.txt~
```

or if you have several, you can type
```
rm *.txt~
```

---

### Post by andrew.46 on 2009-12-18
Hi amcavoy,

A cautious method is to try the following:

```
sudo find / -name '*~' -ok rm {} \;
```

and you will be prompted to delete or not with each file found by pressing 'y' for yes and 'n' for no.

Andrew

---

### Post by forgetclosure on 2009-12-18
this is a normal part of the text editor for ubuntu (gedit).
the file that is example.txt~ is actually a backup file of example.txt automatically created by gedit, and you can change this function in the settings :)

also, just an unimportant sidenote, the .txt extension isn't necessary in linux - no extension is either, because when you double-click on a file (and someone correct me if i'm wrong please) it analyzes the mime-type of the file, and runs the correct program :)

also, andrew.46's way of deleting all of them will work, but just so you know, it will delete every backup file in your system (hence the "/")

---

### Post by bodhi.zazen on 2009-12-18
These files are generated automatically by editors. Assuming you are using gedit, 

Go to Edit -> preferences -> Editor tab

Unselect "Create a backup copy before saving" and if you wish also unselect the auto save every 10 minutes.

You can delete those files using any number of command like tools

rm -rf *.*~

or see man find 

careful with those command ;)

---

### Post by sisco311 on 2009-12-18
I wrote a nautilus script:
```


#!/bin/bash

# size of the window:
WIDTH="400"
HEIGHT="400"

# set this to FALSE if you don't want to auto-select the files
CHECK="TRUE"

# text displayed :)
TEXT="Select files..."

if [ ! -e /usr/bin/trash ]; then
  zenity --question --text "This script requires trash-cli to be installed. Do you want to install it?" && apturl apt://trash-cli
  exit 1
fi

find $@ \( -name "Trash" -prune -o -name "*~" \) -a -type f| sed "s/\(.*\)/"$CHECK"\n\1/" > /tmp/deltilde

if [ ! "$(cat /tmp/deltilde)" ]; then 
  zenity --info --text "No file found."
  rm /tmp/deltilde
  exit 2
fi

IFS="
"

zenity --list --text "$TEXT" --column "Delete" \
--width $WIDTH --height $HEIGHT \
--checklist --multiple --separator "
" \
--column "File" $(cat /tmp/deltilde) | \
while read file; do
  trash "$file"
done  

if [ -e /tmp/deltilde ]; then 
  rm /tmp/deltilde
fi

exit 0



```

It displays a list of the files, allowing you to select which of them to move to the Trash.

Save the script in ~/.gnome2/nautilus-scripts and make it executable.

The script requires [trash-cli]("apt://trash-cli") (click the apturl link to install it).

Usage: Right click in nautilus -> Scripts -> <name of the script>

Use it on your own risk! :evil:

Screenshot attached.

---

### Post by andrew.46 on 2009-12-19
Hi firgerclosure,

> **forgetclosure said:**
> also, andrew.46's way of deleting all of them will work, but just so you know, it will delete every backup file in your system (hence the "/")

Indeed it will, my apologies for making this less than clear. The same syntax can be used for local files only by using:

```
find $HOME -name '*~' -ok rm {} \;
```

and this is perhaps closer to what the OP is after?

Andrew

---

### Post by l-x-l on 2009-12-19
> **andrew.46 said:**
> 
```
sudo find / -name '*~' -ok rm {} \;
```


What does "-ok" do? I don't see it referenced in the man pages. Why not use -exec instead?

---

### Post by sisco311 on 2009-12-19
> **l-x-l said:**
> What does "-ok" do? I don't see it referenced in the man pages. Why not use -exec instead?

[I]Like  -exec but ask the user first.  If the user agrees, run the command.
[/I]
```
man find | less --pattern\= "\-ok command"
```

---

### Post by andrew.46 on 2009-12-19
Hi l-x-l,


> **l-x-l said:**
> What does "-ok" do? I don't see it referenced in the man pages. Why not use -exec instead?

It is in there:

```

Like  -exec but ask the user first.  If the user agrees, run the
command.  Otherwise just return false.

```

If *-exec* is used the whole process assumes the speed of a runaway train and with no request for confirmation all files will be deleted. Great in the hands of an experienced user but potentially disastrous for those less sure of the implications of the command.

Andrew

---

### Post by l-x-l on 2009-12-19
> **sisco311 said:**
> [I]Like  -exec but ask the user first.  If the user agrees, run the command.
[/I]
```
man find | less --pattern\= "\-ok command"
```

> **andrew.46 said:**
> Hi l-x-l,

It is in there:

```

Like  -exec but ask the user first.  If the user agrees, run the
command.  Otherwise just return false.

```

If *-exec* is used the whole process assumes the speed of a runaway train and with no request for confirmation all files will be deleted. Great in the hands of an experienced user but potentially disastrous for those less sure of the implications of the command.

Andrew


Thx to the both of you. I see it now in the man page.

---

### Post by Gourgi on 2010-01-09
> **sisco311 said:**
> I wrote a nautilus script:
```


#!/bin/bash

# size of the window:
WIDTH="400"
HEIGHT="400"

# set this to FALSE if you don't want to auto-select the files
CHECK="TRUE"

# text displayed :)
TEXT="Select files..."

if [ ! -e /usr/bin/trash ]; then
  zenity --question --text "This script requires trash-cli to be installed. Do you want to install it?" && apturl apt://trash-cli
  exit 1
fi

find $@ \( -name "Trash" -prune -o -name "*~" \) -a -type f| sed "s/\(.*\)/"$CHECK"\n\1/" > /tmp/deltilde

if [ ! "$(cat /tmp/deltilde)" ]; then 
  zenity --info --text "No file found."
  rm /tmp/deltilde
  exit 2
fi

IFS="
"

zenity --list --text "$TEXT" --column "Delete" \
--width $WIDTH --height $HEIGHT \
--checklist --multiple --separator "
" \
--column "File" $(cat /tmp/deltilde) | \
while read file; do
  trash "$file"
done  

if [ -e /tmp/deltilde ]; then 
  rm /tmp/deltilde
fi

exit 0



```

It displays a list of the files, allowing you to select which of them to move to the Trash.

Save the script in ~/.gnome2/nautilus-scripts and make it executable.

The script requires [trash-cli]("apt://trash-cli") (click the apturl link to install it).

Usage: Right click in nautilus -> Scripts -> <name of the script>

Use it on your own risk! :evil:

Screenshot attached.

thanks for the script, works great
i used gvfs-trash instead of trash-cli.

---

### Post by tulpie on 2010-03-25
this script kill all *~
At your own risk :D :D :D

```
#!/bin/bash
cd "$nautilus_script_current_uri";
v="files"
ls *~ | sort > $v
cat $v | while read line; do
  rm "${line}"
done
rm $v
exit 0
```

:popcorn:

---

### Post by detroit/zero on 2010-03-25
Bash aliases to the rescue:
```
alias clean='rm -f "#"* "."*~ *~ *.bak *.dvi *.aux *.log'
```

---

