---
title: "Environmental Variables for Ubuntu?"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by kelper on 2010-06-25
Hello,
I installed Netbeans from a .sh file, and not from apt-get. I want to be able to open netbeans by saying "netbeans" in the terminal. How do I set this up?

---

### Post by sanderd17 on 2010-06-25
you need to make a little script in a bin folder. Can you say what command/file you need to exectue now? Then I can give you the code to create the script.

Please give the exact location of the command/file.

If I assume its the file netbeans in the directory /usr/local/netbeans-6.9/bin/, you will need to do the following:

```

sudo gedit /bin/netbeans

```

In the file, write

```

#! /bin/bash
/usr/local/netbeans-6.9/bin/netbeans

```

save and exit gedit and make your script executable:

```

sudo chmod +x /bin/netbeans

```

Now you can execute netbeans just by typing "netbeans".

---

### Post by mikewhatever on 2010-06-25
An executable or a link to it needs to be in the PATH, which by default is '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:'. In other words, place a link to the netbeans executable in any of these, and the command should work.

---

### Post by kelper on 2010-06-25
Here's where the shortcut points to:
/bin/sh "/usr/local/netbeans-6.9/bin/netbeans"

---

### Post by sanderd17 on 2010-06-28
Sorry for the late reply, I didn't manage to get online in the last few days. I've adapted my previous post with your parameters, hope it all goes well.

grtz, Sander

---

### Post by lkjoel on 2010-06-28
For Environment Variables, type
```
gedit ~/.bashrc
```

---

