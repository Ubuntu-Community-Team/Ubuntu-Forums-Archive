---
title: "acpi exiting"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by emmwee on 2009-03-18
For "ideeological" reasons, I'm very happy that I substituted Windows with Linux, and I'm satisfied with my Ubuntu that can do all what Windows can do, and I even find it more userfriendly than Vista.
There are only 4 things I would like to resolve. I will post my 4 problems in 4 separated threads.

2nd problem:
Sometimes, after turning off my system,it doesn't turn off definitely: after leaving ubuntu but before reaching the definite end, there appears an error message: “acpi exiting”. Even I wait some time, nothing happens anymore and I have to power off the pc.
What does it mean? What should I do?

---

### Post by unutbu on 2009-03-19
Are you using Intrepid?
If so, does the shutdown hang after it reports that it is attempting to shutdown ALSA?
If so, take a look here: [http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436). Search for "Shutdown hangs".
Take a look at the bug report, and if it seems to be the same problem, try the workaround listed on the same page.

---

### Post by emmwee on 2009-03-19
Sorry, I'm a newbie and sometimes too courageous. Before doing something I should avoid, maybe better if I ask: Should I go now (as a preventive action) to the terminal under ubuntu and write:
"sudo ln -s /etc/init.d/NetworkManager /etc/rc0.d/K40NetworkManager
sudo ln -s /etc/init.d/NetworkManager /etc/rc6.d/K40NetworkManager".
Or should I write it only into the prompt after I get the "acpi exiting" message?

P. S. Yes, I use Intrepid.
P. P. S. No idea what ALSA means.

---

### Post by unutbu on 2009-03-19
The commands 

```
sudo ln -s /etc/init.d/NetworkManager /etc/rc0.d/K40NetworkManager
sudo ln -s /etc/init.d/NetworkManager /etc/rc6.d/K40NetworkManager
```

are meant to be typed into a terminal while running Ubuntu, before shutting down.

However, if you do not see any message regarding ALSA when the shutdown hangs, then 
the above commands probably are not going to fix your problem.

You have some options:

[list]
[*]Try the above commands anyway. They are very simple, and safe.
After running the commands, try shutting down. If it works, great. If it does not work, 
then press 

```
Alt-SysRq R 
Alt-SysRq E
Alt-SysRq I
Alt-SysRq S
Alt-SysRq U
Alt-SysRq B
```
Wait a few seconds between each key combination.

This is a safer and better way to reboot than turning off the power abruptly.
After rebooting, type
```
sudo rm /etc/rc0.d/K40NetworkManager
sudo rm /etc/rc6.d/K40NetworkManager
``` in a terminal
to restore your machine to its current state.
[*]On this page [http://ubuntuforums.org/showpost.php?p=6176637&postcount=28](http://ubuntuforums.org/showpost.php?p=6176637&postcount=28)
I've listed 3 solutions to the shutdown problem. The first one is the same as one we have been discussing. The other two are things you might want to try if the above commands do not work.
[/list]

---

### Post by emmwee on 2009-03-21
Yhanks!!!
Once again I turned off and the pc didn't shut down correctly but visualized "acpid exiting". As you told me, I typed "Alt+SysRq+r" and so on, and it rebooted my system without problems.
Last question: What's the reason why I should type, after returnung to Ubuntu:
> sudo rm /etc/rc0.d/K40NetworkManager
sudo rm /etc/rc6.d/K40NetworkManager

---

### Post by unutbu on 2009-03-21
When you type
```

sudo ln -s /etc/init.d/NetworkManager /etc/rc0.d/K40NetworkManager
sudo ln -s /etc/init.d/NetworkManager /etc/rc6.d/K40NetworkManager

```
it creates "symlinks" from ```

/etc/rc0.d/K40NetworkManager --> /etc/init.d/NetworkManager
/etc/rc6.d/K40NetworkManager --> /etc/init.d/NetworkManager

```
The presence of these symlinks causes the machine to run the /etc/init.d/NetworkManager script whenever the machine shutsdown or reboots.

Since this did not help fix your shutdown problem, you are free to remove the symlinks. 
You can also keep them if you wish, it will not hurt anything.

---

