---
title: "Eclipse on Ubunutu: Why are my java files opening in gedit?"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-26
It seems odd that when I left click a file in the project explorer it opens with gedit. Also, I found that if I drag the file over to the right it opens as it should, BUT the .java file has no color syntax and no intelli-sense!?

---

### Post by SlickRick on 2010-02-26
Right click the file and go to properties. On the properties window there should be an "open with" tab. There you can select what program to use to open that file by default. If the program is not listed you would need to add it to the list.

If you want syntax highlighting in gedit, click the "view" menu and go down to "highlight mode" in the drop down. Select the language (in this case java which is under sources) and it will highlight it.

I have no idea what intelli-sense is, so maybe someone else can help with that one

---

### Post by TurnOfTide on 2010-02-26
You need to install the eclipse package under synaptic package manager. Eclipse from the Ubunutu software center only installs the bare-essentials, and includes no java editor/jdk tools (ie: Java Perspective).

---

### Post by narthir on 2010-10-18
Hi, i have the same problem but cant make it work. I uninstalled Eclipse with Ubuntu SC and reinstalled it with Synaptic but it still didnt help. Some Ideas?

---

### Post by john77eipe on 2010-10-18
narthir@
You want to a java file to open in eclipse when double clicked?

I use Eclipse and all files are handled directly through eclipse workspace. I haven't thought of opening a solitary java file using eclipse!!

Try OpenWith > Use a custom command.

---

### Post by narthir on 2010-10-18
I am sorry i didnt wrote it right. I am using the workspace, i am opening a project, doubleclicking on a sourcefile (*.java) and it opens it in gedit (the view where always was the source file remains gray).

---

### Post by GregBrannon on 2010-10-18
Here's something to check:

[http://ubuntuforums.org/showthread.php?t=1324360]("http://ubuntuforums.org/showthread.php?t=1324360")

Here's another similar complaint, more recent, but I'm not sure the OP fixed it.  Even so, it might give you some ideas:

[http://ubuntuforums.org/showthread.php?p=9834245#post9834245]("http://ubuntuforums.org/showthread.php?p=9834245#post9834245")

Please report back, fixed or not, to let us know if you've cracked it.

---

### Post by narthir on 2010-10-18
Thank You very much. It was as in the second thread, too bad i didn't find it before. I didn't know you can select the editor in eclipse. I right clicked on the file, selected Open with > Java editor, and it seams eclipse did set it as default now, because after restart he still opens everything in the Java editor. Thanks again :)

---

