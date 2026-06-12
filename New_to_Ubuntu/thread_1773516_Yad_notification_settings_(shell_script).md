---
title: "Yad notification settings (shell script)"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by lol768 on 2011-06-02
I've just installed [_Yad_]("http://code.google.com/p/yad/") which is a fork of zenity with many more features.

Currently, I've been trying to get the menu feature of the notification icon to work. To enable the menu you use the following command:

```
yad --notification --listen
```

Yad then listens on stdin for various settings. For example, if you typed menu:Quit!quit into the terminal it would add a context menu to the notification icon.

I can get the above to work in the terminal, but I am now trying to put it into a shell script, and I have no idea how to specify these settings.

In an [_example script_]("http://code.google.com/p/yad/wiki/USBFlash") on the Google code page the script uses echo to send the settings like this:
```
echo "menu:$MENU" >&3
```

however when I try and do this in my shell script I get a file descriptor error. 

Could somebody point me in the right direction as to how to do this?

Thanks

---

### Post by DaithiF on 2011-06-02
Hi,
i've never used yad, but the example seems fairly straightforward.

they 
(a) create a fifo pipe
(b) attach it to a file descriptor 
(c) run the yad command and redirect its stdin so that it comes from this file descriptor
(d) redirect whatever menu text you need to that file descriptor

in code:
```
# (a) create fifo pipe
PIPE=$(mktemp -u --tmpdir ${0##*/}.XXXXXXXX)
mkfifo $PIPE

# (b) attach a filedescriptor to this pipe
exec 3<> $PIPE

# (c) run yad and tell it to read its stdin from the file descriptor
yad --notification --kill-parent --listen \
    --image=drive-removable-media --text="Removable media" \
    --command="xdg-open $BASEDIR" **<&3** &

# (d) write stuff to the file descriptor
echo "menu:$MENU" >&3

```

hope this helps.

---

### Post by lol768 on 2011-06-02
Thanks for your help. I'll try it out later and mark the thread solved if I can get it to work.
Edit: The code works fine. Thanks again.

---

