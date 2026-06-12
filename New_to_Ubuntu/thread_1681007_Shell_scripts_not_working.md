---
title: "Shell scripts not working"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by anirudha on 2011-02-03
I wrote a simple shell script named "shell_script"

#!/bin/bash
echo "Hello"

and gave rwx permissions to it -rwxrwxrwx.

Now when I am running it on terminal, it says:

$ shell_script
shell_script: command not found

I checked my current shell, it is a bash shell 
$ echo $SHELL
/bin/bash

and when I executed the same script preceding with a "bash", it worked

$ bash shell_script
Hello

it even works if I run it as
$./shell_script

Can anyone please tell me how to fix this.


Also I have observed one more file with same file name but ending with ~, 

$ ls -aF
./  ../  .file1.swp  shell_script*  shell_script~
what does this signify?

Thanks

---

### Post by blind2314 on 2011-02-03
Just typing "shell_script" doesn't work because your current directory is not in your $PATH variable. You can verify this by typing ```
echo $PATH
```
 
The "./shell_script" works because that tells it to use the "." link to source the file from the current directory. "bash shell_script" works in much the same way.

---

### Post by ptn107 on 2011-02-03
You must use
```
$ ./scriptname
```
to run it.

If you
```
$ echo $PATH
```
you will see a list of folders you can put your script in if you want to run from anywhere.

FYI: If you make a /home/$USER/bin folder and reopen your terminal, you can put your script in there and then you can just type *scriptname* from anywhere.

---

### Post by Brandon Williams on 2011-02-03
If it works when run as "./shell_script" and not when run as "shell_script", it's just an issue with your PATH setting. Try "PATH=$PATH:." in the shell and then run "shell_script"; it should now be found.

That said, be cautious about adding the current working directory to your path on a system that is accessible to the internet, since it allows some additional attack vectors. I'm not saying don't do it, just be careful.

"shell_script~" is an automatically saved backup copy of the file; the version prior to the last edit.

---

