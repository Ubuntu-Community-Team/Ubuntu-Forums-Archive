---
title: "Broken Packages"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by rick astley on 2009-04-10
Ive just moved from [COLOR="Red"]fail[/COLOR]dows to ubuntu and loving it so far. Can someone describe to me what is going on here in the screenshot:

[http://img301.imageshack.us/img301/2863/err.png](http://img301.imageshack.us/img301/2863/err.png)

what are these broken packages it notifies me of?

what was the problem with Ultamatix installing also?

There are some of the errors in the terminal that i dont understand.
Thanks fellas!
Rick.

---

### Post by AndrewMc on 2009-04-10
If package "x" is broken, that usually just means that it needs other packages installed to work properly. In your case, you should install the tango-icon-theme-common, tango-icon-theme, and python-gnome2-extras. Then the "dpkg -i ..." should work without complaint.

Best of luck!

---

### Post by Eisenwinter on 2009-04-10
In Linux, there are things called "program dependencies", often shortly called "dependency", "dep", "build dep", and so on.

You are trying to install a program which depends on several things, however, they are not installed, which is why you're getting the "broken package" error.

You have tried to install it from the package manager manually, issuing the "dpkg -i <package>" command.

Have you checked the program you're trying to install is not in the package manager repositories?

Try, in terminal:
```
sudo apt-get install ultamatix
```

But before you install, make sure to clean up the errors, by issuing the following command in terminal:
```
sudo apt-get -f install
```

The **-f** switch means "fix package errors".

Report results.

P.S: and can you please resize the screenshot image, or just provide a link to it? It's very big, and makes the whole page really big and more difficult to look at. :)

---

### Post by rick astley on 2009-04-10
Eisenwinter: when i try that i get this error message (in the terminal)



```
user@ubuntu:~$ sudo apt-get install ultamatix
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```


What does "E:" refer to? A drive or directory?


thanks

---

### Post by Eisenwinter on 2009-04-10
E: simply means it's an error message.

Is synaptic open? If it's open, are you downloading/installing anything?

Have you issued **sudo apt-get -f install** _before_ doing **sudo apt-get install ultamatix**?

---

### Post by rtom on 2009-04-10
> **rick astley said:**
> What does "E:" refer to? A drive or directory?

This case it means ERROR, there's a Synaptic or software upgrade running. Close all the windows you have open except the one you're working on, run ```
sudo apt-get install -f
```, then ```
sudo apt-get install tango-icon-theme-common tango-icon-theme python-gnome2-extras
```

If all correct, you can install ultamatix with the dpkg -i command (since it's not in the repository)

---

### Post by Eisenwinter on 2009-04-10
Also note that forcefully ending a package manager's process, while it's downloading or installing packages, will raise this error.

---

### Post by rick astley on 2009-04-10
ah, excellent. there was an update running in the background. add that to the newbie list of mistakes.

packages have installed correctly now.

anyway, thanks to all!
rick.

---

