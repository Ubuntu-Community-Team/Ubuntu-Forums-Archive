---
title: "sudo not available"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Suparna on 2010-01-27
I am on Ubuntu 8.04. I am trying to sudo. Getting the following message.

[FONT=monospace]Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
bash: sudo: command not found
[/FONT]
I am quite new to ubuntu. How do i solve this problem. i need very simple instructions please.

Suparna

---

### Post by barnex on 2010-01-27
quick workaround: instead of "sudo", just type:

```
/usr/bin/sudo
```

To permanently solve this problem, search for something like "adding directories to your PATH in .bashrc"

---

### Post by lotharmat on 2010-01-27
The following will prepend your $PATH variable with /usr/bin

```
PATH=~/usr/bin:"${PATH}"
```

---

### Post by Suparna on 2010-01-27
Tried /usr/bin/sudo. Got some garbled message!usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

what now?
thanks for helping me try.
suparna

---

### Post by LuisGMarine on 2010-01-27
Interesting error.  Did you recently try to install a piece of software somewhere in the /usr/ folder?  If so you could have ran the wrong command and changed some permissions around.

I did some googling around, and it came down to just re-installing the sudo package.  I'm aware that you cant do it from the command line, so we can try re-installing it through the GUI.

Go to System > Administration > Synaptic Package Manager

In the search box type in "sudo" and right-click the package and select "mark for reinstallation"

Try that, reboot for good measures and see if it works.

---

### Post by Suparna on 2010-01-28
Tried to reinstall sudo and then restarted the machine. Did not work!

Still looking for a solution.

Thanks anyways.

Suparna

---

### Post by Cheezespread on 2010-01-28
Did you try what Lotharmat suggested ?. The error that you are receiving is hinting at the PATH variable not having /usr/bin directory included .

---

### Post by Suparna on 2010-01-28
Yes. Here is the response.

Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
bash: sudo: command not found

Suparna

---

### Post by Cheezespread on 2010-01-28
```
echo $PATH
```

Can you try and give us the results ?.

---

### Post by Suparna on 2010-01-28
Here it is.


PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/

---

### Post by flabdablet on 2010-01-28
#

---

### Post by Cheezespread on 2010-01-28
```
export PATH = "$PATH:/usr/bin"
``` should also do I believe.

---

### Post by flabdablet on 2010-01-28
Open a new Terminal window. Type this command:```
echo $PATH
```In a fresh installation, the result should look like this:```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```If what you see looks different, do this:```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```and you should find sudo works as expected until you close that Terminal window.

If it does, your next job is to restore the standard default setting for PATH. In Ubuntu, this is initially set in /etc/environment. If your /etc/environment file is missing, or does not include the line```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```, then you can fix it with```
echo PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" | /usr/bin/sudo tee -a /etc/environment
```

---

### Post by Suparna on 2010-01-28
Seems to have worked! THANK YOU VERY MUCH.

Suparna

---

### Post by lotharmat on 2010-01-28
Don't forget to mark the thread as solved (thread tools)

---

### Post by Suparna on 2010-01-28
Yes, indeed!

Suparna

---

### Post by flabdablet on 2010-01-28
FYI, the broken value of $PATH you reported earlier
```
PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/
```
looks to me like the result of a typo in a script. There's probably a line somewhere in something you've used sometime that looks like this:
```
PATH="PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin"
```
when what it actually should look like is this:
```
PATH="$PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin"
```
The effect of the second (correct) version is to append ":/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin" to the existing value of the PATH variable. This is a fairly typical idiom for making the shell search in extra places to find commands, and is similar to Lotharmat's original suggestion for putting /usr/bin back in there.

The first version (with PATH instead of $PATH) ignores the previous contents of PATH and simply sets it to what you reported.

Whenever you enter a shell command (like sudo or grep or ls) that isn't actually built into the shell, it looks through all the directories listed in $PATH for a program with that name. And since /usr/bin was no longer listed in your $PATH, the shell failed to find /usr/bin/sudo when you told it to sudo.

The "garbled message" you got when you tried entering **/usr/bin/sudo** as a shell command is simply the standard "helpful" usage hint that /usr/bin/sudo gives out if it's invoked without being told what to do. Now that your $PATH is fixed, you should find that you get the exact same garbled message when you enter just **sudo** by itself.

The fact that there is such a huge difference between the reactions of newbies and seasoned Unix users to  standard usage hints is a big part of the reason why [sites like this]("http://www.art.net/~hopkins/Don/unix-haters/handbook.html") exist :)

---

