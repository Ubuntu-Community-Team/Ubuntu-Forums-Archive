---
title: "the symbol &gt; at the terminal screen"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by chihwahli on 2010-07-14
I used Xbuntu 10.04 LTS
I created an file with special signs -->  &quot;la*
and tried to delete it with the command rm &quot;la*

According  to the webiste:
[http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html)

I  cannot do it like this. Only with Inode number.
But this is not the  problem at this moment.
When I try rm &quot;la* at the terminal screen the  prompt changes to > :

At the /tmp directory:

$ rm &quot;la*  (press enter)
>

when the > sign comes instead of  loginname@xxx$ 
I cannot do anything, typing q or quit enter does  nothing.
What does > means? What is happening? How can I correct  it?

---

### Post by da burger on 2010-07-14
That means it expects more input. When you used and opening quote bash expected a closing quote as well.

You can delete that file if you preface each of those symbols with a \ or if you surround the file name with single quotes.

---

### Post by Brandon Williams on 2010-07-14
The '"' symbol in the file name is being treated as a special character, and bash outputs the '>' prompt to indicate that you are still within a quoted string. It will not attempt to execute a real command until you close the quoted string with another '"' character.

For what you're trying to do, you don't need the inode. You just need to escape the special characters in the file name:
```
rm \"la\*
```

---

### Post by bodhi.zazen on 2010-07-14
See also :

[http://www.linuxconfig.org/Bash_prompt_basics](http://www.linuxconfig.org/Bash_prompt_basics)

[http://www.grymoire.com/Unix/Sh.html#uh-23](http://www.grymoire.com/Unix/Sh.html#uh-23)

[http://networking.ringofsaturn.com/Unix/customizebashshell.php](http://networking.ringofsaturn.com/Unix/customizebashshell.php)

---

### Post by chihwahli on 2010-07-14
Aah ok. Now I know what > means thanks a lot! Very informative.  3 cheers to everyone who helped out!

---

