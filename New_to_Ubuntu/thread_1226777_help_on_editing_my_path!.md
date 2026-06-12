---
title: "help on editing my path!"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by nmobrien4 on 2009-07-29
I am pretty new to the linux terminal, but have been trying to learn as much as I can for about a week now. I am using linuxcommand.org to speed up my learning process, and have found it very helpful. There is a chapter on writing scripts which contains a simple hello world program. The website states that one should have a bin directory inside of the home directory in which to store scripts. It gives very vague "instructions" on how to edit the path to include the ~/bin. 

"A better way would be to edit your .bash_profile file to include the above command. That way, it would be done automatically every time you log in."

I do not seem to have a .bash_profile, but have been looking around on different websites and from what I understand, editing the .bashrc would accomplish the same thing. Well I tried entering:  "export PATH=$PATH:*~/*bin" into my .bashrc fileand then typed the name of the hello world script that I had created earlier, and I got a "command not found" error message. Is it necessary to restart/log back in for it to work. I only ask because I do not actually have ubuntu installed (I am running it from the cd drive) and therefore can not log out without erasing everything.

any help would be much appreciated.

---

### Post by sdlynx on 2009-07-29
yes, I'm pretty sure you need to reboot, or at least log out and back in

try adding "cd ~/bin" to the end of your bashrc.  I'm not nearly informed on this but its what I would try lol

---

### Post by llamabr on 2009-07-29
You'll have to restart bash for it to work.  your .bash_profile or .bashrc only gets read and updated when you login to the shell.

So before you run your script, just type:

```
bash
```

at the prompt, and then try running it.

---

### Post by ecmatter on 2009-07-29
I remember tripping over that section of that tutorial.

1.  Create a bin directory in your home folder

```

mkdir ~/bin

```2.  **Open your .bashrc file**  Your .bashrc file is a hidden file in your home directory.  You can either find it in nautilus (press CNTRL H to view hidden files), or enter the following in the terminal:

```

sudo gedit ~/.bashrc

```3.  Add the following to the end of your .bashrc file:

```

PATH="$HOME/bin:$PATH"

```(The tutorial you're working through does this differently.  In the terminal: **export PATH=$PATH:*directory**.  *Both methods work.)

4.  Save your changes to .bashrc and reboot.

---

### Post by nmobrien4 on 2009-07-29
Thanks for your help everyone. It's working now.

---

### Post by ecmatter on 2009-07-30
[s]I got to looking at my own PATH and noticed that my ~/bin was listed twice.  So I looked at my ~/.profile and found the following:

```
[s]
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi[/s]

```So, in other words, it isn't necessary to add anything to your .bashrc file.  As soon as you create a bin in your home directory and reboot, the bin is added to your PATH automatically by your ~/.profile.

Apologies for the bad advice.[/s]

---

### Post by nmobrien4 on 2009-07-30
No worries. It all worked out.

---

### Post by bodhi.zazen on 2009-07-30
IMO you should put $HOME/bin LAST on the path.

This is a (small) security thing. If you put it first somebody could add a malignant script such as ~/bin/sudo and when you run "sudo" the malignant script will be called.

If ~/bin is last, the "real" sudo will be called.

I say this is a minor security risk because it somebody can add such a script you are in trouble already (you have already been cracked).

---

