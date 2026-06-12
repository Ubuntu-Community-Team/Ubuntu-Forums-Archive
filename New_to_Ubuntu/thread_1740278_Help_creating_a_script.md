---
title: "Help creating a script"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Hoopz on 2011-04-26
I tether my cellphone for an internet connection.  I am using easytether to accomplish this
In order to get online I have to run

```
easytether connect
```

If I do this in terminal it states that the connection is established and sits there until I press Ctrl-C so I leave this like that and open a new terminal window and type 

```
sudo dhclient easytether0
```


to get an ip address.

When I try to combine this in a script so I can just double click on an icon on the desktop it doesn't work right.  I have tried different ways and can get either the first command to work and not the 2nd or I can get the 2nd command to work and not the 1st

---

### Post by Vaphell on 2011-04-26
```
easytether connect &
sudo dhclient easytether0
```

& puts commands in the background which allows other commands to run at the same time.
You may want to put a delay
```
sleep 5
```
to give enough time to set up connection in case it's not instant

---

### Post by Hoopz on 2011-04-26
Doing it like this
```
#!/bin/sh
#
#

easytether connect &
sleep 3
sudo dhclient easytether0 
```

opens the windows then puts it in the background and the internet connection doesn't work.

 I tried putting the & after the dhclient command and it just sits there with the window open I wait a while but still don't have an internet connection.  I get the same results not using the & symbol at all

---

### Post by Hoopz on 2011-04-26
Is there a way to have each command open it's own terminal window?

---

### Post by Crusty Old Fart on 2011-04-27
> **Hoopz said:**
> Is there a way to have each command open it's own terminal window?
Maybe this:
```

#!/bin/bash
set -e

gnome-terminal -x easytether connect
sleep 3
gnome-terminal -x sudo dhclient easytether0

exit 0

```See:
```

man gnome-terminal

```Good luck.

---

### Post by Hoopz on 2011-04-27
Awesome!!!  That worked! Thank you both for your help.

---

### Post by Crusty Old Fart on 2011-04-27
> **Hoopz said:**
> Awesome!!!  That worked! Thank you both for your help.
Ah...that's good.

I wasn't 100% sure that it would.

Sometimes we just get lucky :cool:

Have fun,

Crusty

---

