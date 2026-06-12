---
title: "Saving parts of a command..?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-04
What is the best way to save a string (permantly) so that I can recall it later on the CLI? This would be like a partial aliase, EG:



svn checkout [repo_name]/project1



where repo_name = "file:///home/windsor/svn/"


This would be incredibly helpful, thanks.

---

### Post by J V on 2010-03-04
if you use it a lot just hit the up arrow...

---

### Post by Jordanwb on 2010-03-04
Perhaps you could write a bash script? [http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial) See part 4.

---

### Post by TurnOfTide on 2010-03-04
I don't use the command a lot, I want to build commands by saving strings that I can recall quicker, just like how ~ writes out /home/[username]/   .I want something like that.

---

### Post by TurnOfTide on 2010-03-04
> **Jordanwb said:**
> Perhaps you could write a bash script? [http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial) See part 4.

Yes but I don't think it will persist then next time I open a shell.

---

### Post by William Shotts on 2010-03-04
> **TurnOfTide said:**
> What is the best way to save a string (permantly) so that I can recall it later on the CLI? This would be like a partial aliase, EG:



svn checkout [repo_name]/project1



where repo_name = "file:///home/windsor/svn/"


This would be incredibly helpful, thanks.

If you mean the entire command, then you could add this line to your [FONT=Courier New].bashrc[/FONT] file:

[FONT=Courier New]alias svn_checkout='svn checkout file:///home/windsor/svn /project1'[/FONT]

This will create an *alias* that can be invoked this way:

[FONT=Courier New]svn_checkout[/FONT]

If you mean that you only want to store the repo_name, then add this line to your [FONT=Courier New].bashrc[/FONT] file:

[FONT=Courier New]export REPO_NAME="file:///home/windsor/svn"[/FONT]

This will create an *environment variable* that can be invoked as follows:

[FONT=Courier New]svn checkout $REPO_NAME/project1[/FONT]

---

