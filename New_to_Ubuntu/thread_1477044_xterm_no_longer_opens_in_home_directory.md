---
title: "xterm no longer opens in home directory"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by crowhill on 2010-05-08
hi there

i just installed ubuntu 10. then i noticed that xterm is no longer opening in my home directory /home/myname but, rather, in the root directory. how can i modify this setting?

thank you very much,
cheers,
crowhill.

---

### Post by duanedesign on 2010-05-08
What do you get from the command

```
echo $HOME
```

If it does not return /home/myname then you might need to check your passwd file. You can open the file with the following command.


```
sudo gedit /etc/passwd
```

Then scan the file till you get to your usernam. The entry should look something like this:

> yourusername: x :800:800:yourusername,,,,:/home/yourusername:/bin/bash

---

### Post by crowhill on 2010-05-08
thank you very much for you help!

```
echo $HOME
```

this gives me /home/myname

the entry in /etc/passwd looks as you described it.

still, my xterm opens in / rather than in ~.

any ideas?

thanks a lot,
cheers,
crowhill.

---

### Post by crowhill on 2010-05-09
actually, the /etc/passwd file gives

yourusername: x :800:800:[COLOR="Red"]myfullname[/COLOR],,,,:/home/yourusername:/bin/bash

any ideas?

---

