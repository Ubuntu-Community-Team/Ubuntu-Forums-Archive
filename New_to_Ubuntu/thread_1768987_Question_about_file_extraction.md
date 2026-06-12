---
title: "Question about file extraction"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-27
when a file with the extension of .sh gets extracted, how do you install it into Ubuntu?

---

### Post by Joe of loath on 2011-05-27
Navigate to the directory it's in with the terminal, then run ./script_name.sh

---

### Post by Smart Viking on 2011-05-27
Files with the file extension .sh are not compressed files(or should not be), thus, you should not extract them. They are shell scripts, that means that they are text files with shell commands. You execute those files so you don't have to write all of them down. You don't need to install them to execute them, but you could move those files to /usr/bin so it will always be available in the shell through the PATH variable.

---

### Post by noidian on 2011-05-27
I concur with the shell script part but you might need to move them to the path only depending on what you want to do with it. One thing you can be wary of is: some scripts require different shell so you might need to change to another shell to run the shell script.

---

### Post by Smart Viking on 2011-05-27
> **noidian said:**
> I concur with the shell script part but you might need to move them to the path only depending on what you want to do with it. One thing you can be wary of is: some scripts require different shell so you might need to change to another shell to run the shell script.
Not if the shell script contains a shebang, which most do. If the shell contains a shebang and you execute it with a forward slash it should work just fine unless the shebang is incorrect.

You could always just launch $ shell file.sh anyways.

---

### Post by TAspr on 2011-05-27
> **Smart Viking said:**
> Not if the shell script contains a shebang, which most do. If the shell contains a shebang and you execute it with a forward slash it should work just fine unless the shebang is incorrect.

You could always just launch $ shell file.sh anyways.

What do you mean the shell?  

It is the boot_info_script060.zip which let to the shell file.  I am not even going to attempt this..

---

### Post by webofunni on 2011-05-27
Shell is the interactive system to communicate with system. Shell is where we execute commands. To execute the script that you mentioned 

1. Go to the place where the zip file is stored. say it is in your home directory. 
2. You need a shell, to get that press ALT+F2 and enter gnome-terminal and enter you will get a shell to execute commands. 

do

```

unzip boot_info_script060.zip
./boot_info_whatever.sh

```

---

