---
title: "Bash scripting question"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by hwychld on 2010-12-03
Quick question regarding scripting.  As an example:  ```
 #!/bin/bash  dig +short txt &quot;`echo $@`&quot;.wp.dg.cx  
```   Does exactly what it should, outputs the results of the dig command to the terminal.  However, this script:  ```
 #!/bin/bash  alias | grep --ignore-case &quot;$1&quot; 
```   (where $1 is the argument supplied on the command line)doesn't output anything, but run from the command line works just fine.  I have a couple of scripts where the command line works just  fine but the output never appears when run as a script.  So what am I doing wrong?  Thanks  Not sure why the stuff embedded in the code tags is all on one line, in my scripts the commands are not on the same line as the shebang.  Also, I know I could alias these (they are relatively simple) instead of using a Bash script, but I am trying to learn how to do this so it works for more complicated scripts.

---

### Post by sisco311 on 2010-12-03
Well, your script works, but it runs in a sub-shell which does not inherit the aliases from its parent shell, hence does not output anything. ;)

You probably want to run the script in the current shell:
```
source ./script arg
```
```
. ./script arg
```

See:
```
man bash | less +/"source filename \[arguments\]"
```

---

### Post by hwychld on 2010-12-03
DOH!  Yup, that would be it.  I was sure it was a scripting problem and I didn't consider anything else.

Thanks sisco311

---

### Post by DaithiF on 2010-12-03
you might also want to consider using bash functions rather than scripts for these commands ... e.g. this defined in your .bashrc would achieve the same result:

```
function aliasgrep() {
  alias | grep -i "$1"
}

```
then to use it:
```
aliasgrep something
```

---

### Post by AlphaLexman on 2010-12-03
> **DaithiF said:**
> you might also want to consider using bash functions rather than scripts for these commands

Yes, Bash reads Command Execution in this order:
[LIST]
[*]Keywords
[*]Aliases
[*]Special Built-ins
[*]Functions
[*]Non-Special Built-ins
[*]Scripts and Executables
[/LIST]

As Functions are read **before** scripts.

---

### Post by hwychld on 2010-12-03
Great info, thanks guys.

---

