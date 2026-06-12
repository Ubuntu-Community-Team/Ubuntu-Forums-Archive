---
title: "clarification of jargon for newbies"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by degarb on 2010-02-02
If someone posts "save script to path'  what does that mean?   I know that dirs in the path variable in windows mean, but not linux.  Furthermore what extension and what permissions and what to set as executable.

Also, someone posted, cp some file in the terminal.  what does cp mean?

---

### Post by RiceMonster on 2010-02-02
cp means copy

save script to path would mean to save the script in directory that is in $PATH. To find out the directories your path, run in terminal:
```
echo $PATH
```

If you want to make the script executable, do either of these (in a terminal):
```
chmod a+x /location/of/script
chmod 755 /location/of/script
```

Note, if the script is not in your home directory, type sudo before the above commands.

---

### Post by Leppie on 2010-02-02
dir/folder are like the dirs/folders in windows.
cp = copy

about the script, you will have to be more specific. in linux you can run many different kinds of scripts direcly off the command line.

---

### Post by bodhi.zazen on 2010-02-02
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

And for gui terminology :

[https://wiki.ubuntu.com/DocumentationTeam/StyleGuide/StandardTerminology](https://wiki.ubuntu.com/DocumentationTeam/StyleGuide/StandardTerminology)

---

### Post by Chris Edgell on 2010-02-02
Thanks, I needed that.  (Referring to the terminology tutorial.)

---

