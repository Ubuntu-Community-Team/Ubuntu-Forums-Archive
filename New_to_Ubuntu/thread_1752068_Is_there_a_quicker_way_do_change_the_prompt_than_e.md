---
title: "Is there a quicker way do change the prompt than export PS1='prompt'?"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by leftaroundabout on 2011-05-07
I'm happy with the rather lengthy default prompt containing the whole path, it's really useful for navigating over the whole filesystem. But after a while I usually settle most open terminal windows to one particular directory, and then I like to set the prompt to '\n$', which gives a better focus to the process outputs of the programs (like g++ or pdflatex) that I repeatedly run there. That happens really often, so at the moment I type export PS1='\n$' at least once every time I log in.

That's ok, but of course I'm lazy, so I'd like to have some kind of shortcut for this. The naïve way to do this is putting a shell script in /usr/bin saying nothing but
```
export PS1='\n$'
```and giving it a fast-to type name, but that doesn't work: apparently it only changes the PS1 variable locally, not affecting its value outside the script itself.
Is there any way to literally export this variable out into the surrounding shell, so that I then see it as the new prompt, or any other way to quickly change it?

---

### Post by gmargo on 2011-05-07
Here's how I do it.  I have several shell functions in my $HOME/.bashrc file that change the PS1 prompt.  So when I want a minimal PS1, I just type "promptsimple".  If I want to go back, I can just type "promptnormal".

Here's an example of three such functions from my .bashrc.  Note the last line calls the "promptnormal" function within the .bashrc to set PS1 initially.
```

# Functions to set the PS1 prompt
promptbasic()
{
    PS1='\u@\h \!\$ '
}

promptsimple()
{
    PS1='\$ '
}

promptnormal()
{
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
}   
promptnormal

```

---

### Post by leftaroundabout on 2011-05-08
Thanks, that's exactly what I wanted.

---

