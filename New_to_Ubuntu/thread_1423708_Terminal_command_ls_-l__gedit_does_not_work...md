---
title: "Terminal command ls -l | gedit does not work.."
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-07
*Terminal command*** ls -l | gedit ***does not work*..

Am using Ubuntu Karmic and when I try to pipe the ls command output into gedit as shown above all I see is a blank pane in gedit. Please Help !

---

### Post by Bachstelze on 2010-03-07
I don't think gedit can handle text it recieves on standard input. Why would you want to do that anyway?

---

### Post by patchwork on 2010-03-07
Try ```
ls -l > "name of file" && gedit "name of file"
```EDIT:  nice catch, kaibob, I started to use <name of file>, but thought it might be confusing with the ls -l > redirect....sorry for the confusion

---

### Post by kaibob on 2010-03-07
> **patchwork said:**
> Try ```
ls -l > "name of file" && gedit "<name of file"
```

I believe there's a typo in the above command. The following seems to work fine:

```
ls -l > "name of file" && gedit "name of file"
```

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-07
Many thank'x this works and gives me what I want BUT I would yet like to know the reason the standard pipe | fails ? Very much appreciate the quick response. :-)

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-07
Sure it can :-)

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-07
> **kaibob said:**
> I believe there's a typo in the above command. The following seems to work fine:

```
ls -l > "name of file" && gedit "name of file"
```

Thank YOU kaibob this works just fine. Would be nice to know WHY the other redirect/pipe | fails ?

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-07
> **Bachstelze said:**
> I don't think gedit can handle text it recieves on standard input. Why would you want to do that anyway?

Well sometimes in a very LARGE file system instead of having to scroll up and down in the terminal it is easier to have the file and directory information in a text file in gedit or your preferred editor. Also if you need to compare two or more file or directory contents this comes in handy.. especially if you want to monitor a directory over a period of time, when files may have been added, deleted or changed.

---

### Post by abcuser on 2010-03-07
> **kaibob said:**
> ```
ls -l > "name of file" && gedit "name of file"
```

I suggest to write all temporally files into /tmp directory, because if you will execute above command twice you will get "name of file" file in gedit input.

Try this:
```
ls -l > /tmp/dummy && gedit /tmp/dummy
```




> **Aruna Hewapathirane-&#3461 said:**
> Would be nice to know WHY the other pipe | fails ?
This is very old bug first reported in year 2003:
[https://bugs.launchpad.net/gedit/+bug/9054](https://bugs.launchpad.net/gedit/+bug/9054)
[https://bugzilla.gnome.org/show_bug.cgi?id=121891](https://bugzilla.gnome.org/show_bug.cgi?id=121891)

---

### Post by abcuser on 2010-03-07
> **Aruna Hewapathirane-&#3461 said:**
> Also if you need to compare two or more file or directory contents this comes in handy..
For this purpose you can also use vimdiff command:
```
vimdiff old_file.txt new_file.txt
```

---

### Post by gmargo on 2010-03-07
**gedit** cannot read from standard input.  But since **vim** was mentioned, I may as well mention that both **vim** (the text-mode version) and **gvim** (the graphical version) will read from standard input given a dash "-" as the filename argument.

---

### Post by kaibob on 2010-03-07
> **Aruna Hewapathirane-&#3461 said:**
> Thank YOU kaibob this works just fine. Would be nice to know WHY the other redirect/pipe | fails ?

Gedit help, which is quoted below, clearly indicates that you should be able to pipe the output of the ls command to gedit. It doesn't work, though. I guess, as abcuser noted, this is a bug. 

> You can use gedit to pipe the output of a command to a text file. For example, to pipe the output of an ls command to a text file, type ls | gedit, then press Return.

The output of the ls command is displayed in a new text file in the gedit window.

Alternatively, you can use the External tools plugin to pipe command output to the current file. 

The external tools plugin adds a run command to gedit's tools menu. I checked and you can do an ls with the run command. This is not what you are looking for but may be worth investigating. If not, the other workarounds  suggested in this thread seem to do the job. 

Not important I know but the command in my earlier post was from patchwork. I just noted a small typographical error.

---

