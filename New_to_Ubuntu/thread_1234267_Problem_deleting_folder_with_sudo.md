---
title: "Problem deleting folder with sudo"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Asgiliath on 2009-08-07
Hi everyone.
I already looked for the way to delete a folder that was created using a sudo command and have typed this into the terminal:
```
sudo rm -rf /usr/share/amsn/skins/Darkmatter
```I get no error so the command seems to work but the folder is still there with all the files inside it. Any suggestions?

---

### Post by Humanum on 2009-08-07
You may want to check if there aren't files that are read only ...

---

### Post by credobyte on 2009-08-07
Can you show us the exact error message you get upon executing this command ?

---

### Post by wojox on 2009-08-07
```
gksudo nautilus
```

---

### Post by Asgiliath on 2009-08-07
> **credobyte said:**
> Can you show us the exact error message you get upon executing this command ?

Well that's the thing that puzzles me: I don't get any error message...

> **wojox said:**
> ```
gksudo nautilus
```

Is nautilus the only way to delete folders owned by root? If yes, what is the entire command I should enter to do so?

---

### Post by credobyte on 2009-08-07
Try:
```
cd /usr/share/amsn/skins/Darkmatter && sudo rm -r ./* && cd .. && sudo rm -r Darkmatter

```

---

### Post by unutbu on 2009-08-07
Perhaps there is a space at the end "Darkmatter ".
If there is, rm will behave as you described:
```

% ls -l /tmp/test
total 4
drwxr-xr-x 2 user user 4096 2009-08-07 17:09 Darkmatter 
% ls -l /tmp/test/ | cat -A
total 4$
drwxr-xr-x 2 user user 4096 2009-08-07 17:09 Darkmatter $
% rm -rf /tmp/test/Darkmatter
% ls -l /tmp/test/ | cat -A
total 4$
drwxr-xr-x 2 user user 4096 2009-08-07 17:09 Darkmatter $
```

You can test if you have a space in your directory name by running
```

ls -l /usr/share/amsn/skins | cat -A
```

It will place a dollar sign ($) at the end of the name. If there is a space, 
you will see a space -- as in "Darkmatter $".

If you do find that there is a space in the directory name, you can remove the  directory with
```

sudo rm -rf "/usr/share/amsn/skins/Darkmatter "
```
or
```

sudo rm -rf /usr/share/amsn/skins/Darkmatter*
```

---

### Post by Asgiliath on 2009-08-07
It worked! Thanks a lot for your help guys :)

---

