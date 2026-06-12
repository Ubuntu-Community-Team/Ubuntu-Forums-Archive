---
title: "shell script not working"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by crowhill on 2010-07-10
hi there

my script

```
#!/bin/bash
/home/crowhill/programs/matlab/program/bin/matlab -glnx86;
```

is not working. it's supposed to start matlab. the thing is that if i type the exact same command in a terminal it works. i therefore conclude that this command needs to be executed in a terminal. how do i have to modify the above script to make this happen?

thanks so much,
cheers,
crowhill.

---

### Post by flanagan on 2010-07-11
I am not familiar with the matlab command line, but, does the command you type from a terminal (the one that works) contain the same semi-colon after the parameter?

---

### Post by crowhill on 2010-07-11
thank you very much for the reply!

the command in the terminal has no semi-colon. however, that makes no difference as far as the script is concerned. it works neither way.

i've now modified my initial script a little bit. it's now

```
#!/bin/bash
gnome-terminal -e '/home/crowhill/programs/matlab/program/bin/matlab -glnx86'
```

this opens a terminal and executes the given string as command. the problem is that the terminal stays open after matlab has come up. if i close the terminal, matlab terminates ... it's really confusing!

thank you very much again,
cheers,

crowhill.

---

### Post by crowhill on 2010-07-11
i solved it!

it's a matlab thing, not a ubuntu or gnome thing.

the correct script is

```
#!/bin/bash
setsid /home/crowhill/programs/matlab/program/bin/matlab -desktop;
```

cheers,

crowhill.

---

