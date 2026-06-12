---
title: "writing a script?"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by supermooshman on 2010-08-18
Hi All,

Searching the forum and google I found a lot of detailed guides into how to write a script for special things.

Now my question is (it probably has a really simple answer but I don't seem to find it):
- writing a script, can I just put in all things that normally would be put into the terminal?
- where should I put these things? (gedit, leafpad ea?)

Thanks!

---

### Post by CharlesA on 2010-08-18
Yes, that's pretty much it.

You can use if statements and variables as well.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by supermooshman on 2010-08-18
> **CharlesA said:**
> Yes, that's pretty much it.

You can use if statements and variables as well.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

thanks, seems like a very clear explanation
but (yes always a but :) if I make the hello world script, how do I save it - and how do I run it?

is it, write the thing, save as filename.sh and...?

---

### Post by Zeike on 2010-08-18
> **supermooshman said:**
> is it, write the thing, save as filename.sh and...?

you can run the script by running

'sh filename.sh'
or
'bash filename.sh'

Optionally, you can set the script as executable with
'chmod +x filename.sh'
And then you should be able to run the script with
'./filename.sh'
This will only work if you have a #!/bin/sh (or #!/bin/bash or #!/usr/bin/perl or whatever you're using at the top of the script).

---

### Post by djyoung4 on 2010-08-18
> **supermooshman said:**
> thanks, seems like a very clear explanation
but (yes always a but :) if I make the hello world script, how do I save it - and how do I run it?

is it, write the thing, save as filename.sh and...?
chmod it.  you have to make it executable.  Under properties > permissions > there should be a little check box that says make this executable or:
```
chmod 755 +x path/to/file.sh
```

---

### Post by ubudog on 2010-08-18
I recommend Emacs, you can find it in my signature.

---

### Post by supermooshman on 2010-08-18
guess who just got his terminal saying?
```
hello world
```

everyone thanks a dozen!

---

### Post by ubudog on 2010-08-18
Nice!  I remember my first program... :p

---

### Post by Zorgoth on 2010-08-18
I recommend just reading 'man bash' - that is essentially how I learned a large percentage what I know about scripting.

---

### Post by ubudog on 2010-08-18
> **Zorgoth said:**
> I recommend just reading 'man bash' - that is essentially how I learned a large percentage what I know about scripting.

Lol, me too.

---

