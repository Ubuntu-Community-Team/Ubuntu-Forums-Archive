---
title: "Opening multiple programs in a single command line?"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-07-13
I'm attempting to make a keyboard shortcut which opens all of my IM clients at once, but am having trouble figuring how to assign both programs to a single command line. I'm using the CompizConfigManager program to do this. The two programs I'd like to open are Skype and Pidgin. They open fine one by one in the command line if I simply enter "Pidgin" or "Skype", but they do not both open if I do "Pidgin Skype". Am I missing a semicolon or something?

---

### Post by linuxman94 on 2011-07-13
Put two ampersand symbols in between the two commands to execute them both.  So in your case it would look like this.

```
pidgin && skype
```

---

### Post by Matt__ on 2011-07-13
just a single '&' will do it, using a double amper means;

execute command one but only execute command two if command one was successful :)

so any typo or other error will stop both opening

---

### Post by mcduck on 2011-07-13
multiple commands can be separated by a semicolon if you want to enter them on the same line, and in this case you'll probably want to start the programs in the background so add an ampersand after each program

```
command1 &; command2 &; command3 &
```

Alternatively you could create a small shell script to launch your programs, and maker the keyboard shortcut execute that script:
```

#!/bin/sh

command1 &
command2 &
command3 &
```

---

