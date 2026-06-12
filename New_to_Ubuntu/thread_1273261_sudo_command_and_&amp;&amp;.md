---
title: "sudo command and &amp;&amp;"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by mathfreak123 on 2009-09-23
I have a command of the form cmd1 && shutdown (options are implied), and shutdown requires sudo.

Can I try "sudo cmd1 && shutdown" so that both commands will work, or does it have to be "cmd1 && sudo shutdown"? Also, is there a way to have sudo have me immediately enter my password after I press enter, so I can just leave the computer and let it take care of itself (cmd1 takes a while to finish)?

---

### Post by Bachstelze on 2009-09-23
If running cmd1 as root is okay, you can get a root shell with

```
sudo -i
```

and then just run

```
cmd1 && shutdown
```

---

### Post by mathfreak123 on 2009-09-23
Ok, I think that did it! Thanks for your help!

---

