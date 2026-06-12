---
title: "[SOLVED] need help form (nautilus-open-terminal)"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by ganesh4it on 2008-12-05
Hi leader..,
       I need one favour frm u all...,
Q:
 From where i cat get the proper nautilus-open-terminal which i can use in my Fedora 8(Linux PC)I tried tp installing nautilus-open-terminal-0.8 but it shows the following 
in my terminal :

< =======================  Plz look it starts ====================>>
checking for NAUTILUS... configure: error: Package requirements (lib nautilus-extension >= 2.17.2 glib-2.0 >= 2.4.0) were not met:

Package gio-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gio-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gio-2.0', required by 'libnautilus-extension', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NAUTILUS_CFLAGS
and NAUTILUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

< =======================  Plz look it Ends ====================>>

let me know the solution ASAP.):P

---

### Post by jgoguen on 2008-12-05
Are you compiling from source?  It's available as a package in Ubuntu, run this command to install it:
```
sudo aptitude install nautilus-open-terminal[/open]

The compile failing suggests that you don't have the required development packages installed.  You'll need to install at least *libnautilus-extension-dev* and *libglib2..0-dev*, possibly others, to make it compile successfully.  Run this command to get all build dependencies:
[code]sudo apt-get build-dep nautilus-open-terminal
```

An alternative would be to create this script as *~/.gnome2/nautilus-scripts/Open Terminal Here*.

```
#!/bin/bash
cd `dirname $NAUTILUS_SCRIPT_CURRENT_URI`
exec gnome-terminal
```

Once you create that script, make it executable with **chmod +x "~/.gnome2/nautilus-scripts/Open Terminal Here"** and in your right-click menu in Nautilus you'll see the **Scripts** sub-menu.  Under that, you'll see **Open Terminal Here** which will open a Terminal in the same directory Nautilus is currently in.

---

### Post by chrisod on 2008-12-05
OP says he is using Fedora. Apt-get won't work as Fedora doesn't use it, it uses Yum, but I'm not up on the syntax for Yum. However, why is the OP asking for Fedora help here? Linux is linux to a certain degree, but he or she is likely to get a better answer quicker at a Fedora forum.

---

### Post by oldos2er on 2008-12-05
[http://download.fedora.redhat.com/pub/fedora/linux/extras/6/i386/repoview/nautilus-open-terminal.html](http://download.fedora.redhat.com/pub/fedora/linux/extras/6/i386/repoview/nautilus-open-terminal.html)

---

### Post by jgoguen on 2008-12-05
> **chrisod said:**
> OP says he is using Fedora.
I interpreted it as OP has used it on Fedora and wants to here as well.  Oops...

The commands for yum, at least for installing, is the same (yum install <package>) but Fedora doesn't allow using sudo by default.  You need to either enter **su** and then enter your root password (not your user password on Fedora) and then give the yum command, or combine them with **su -c "yum install <package>"**, again entering the root password.  I'm not sure about the package names though... but if you download the package linked by oldos2er and install with **su -c "yum localinstall nautilus-open-terminal-0.7-3.fc6.i386.rpm"** it should automatically pick up dependencies.

---

### Post by ganesh4it on 2008-12-11
hi jgoguen..

   Tnku soo much.............

i got sucess wuth ur script...


Its really a wonderful help from u...

adin tnku soo muchh..,:guitar:

---

### Post by ganesh4it on 2008-12-11
but jgoguen..

  Now am opening the current directory..
but i need to open the folder which i selected currently..
any script is available for tat ? ? ?

i guess u know like "Drop to dos in windows"

waiting for u r replay..,

---

### Post by jgoguen on 2008-12-11
Ahh, sorry, I misunderstood.  Use this script instead.  If you choose no directory, or if you choose a file, it will open the current directory.  If you choose a directory, it will open the directory you have selected.

```
#!/bin/bash
base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"

if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
    dir=${base}
else
    while [ ! -z "$1" -a ! -d "${base}/$1" ]; do
        shift
    done
    dir="${base}/$1"
fi  

gnome-terminal --working-directory="${dir}"
```

---

### Post by ganesh4it on 2008-12-18
Tnku soo much Mr.jgoguen....,
.... really a wonder support for me frm u....,:guitar:

shell i rise my nest queary..,:confused:


am using intelj IDEA8.0(trial version) i need the spell checker for my java doc and and also to verify my comments...

is it possible to get ? ? ?

:popcorn:

---

### Post by jgoguen on 2008-12-18
You should open a new thread for that question, it's quite different from the topic of this thread.  I don't know anything about IntelliJ, and you'll have more success finding someone who does with a new thread for that question.

Also, if your original problem is solved, please mark this thread as solved so other users know that this thread provided you with a solution to your question.  To do this, click the Thread Tools link (just above your first post on the right side) and choose the option to mark this thread as solved.

Thanks, and good luck finding answers to your IntelliJ question.

---

### Post by ganesh4it on 2008-12-18
ok my leader..
i ll...:guitar:

---

