---
title: "Timestamp in terminal"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by mitk0o0o0 on 2011-07-10
I just watched a video about ffmpeg and i saw the guy's terminal and it was really cool how it was customised, i somewhat customized mine by making background black transparent and chaning colors but i found the timestamps next to the commands and stuff will be much cooler.

I was wondering, how can i do that? What do i need to edit since it's not in the settings menu.

First step is typing this in terminal, right?
> gksu gedit .bashrc

---

### Post by mitk0o0o0 on 2011-07-10
Ok so i have changed the line to this

```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w (\t) $ '
```It's all good now, any ideas how to make only the timestamp part in red color?

This is the timestamp part btw
```
 (\t) 
```EDIT: Got it now with timestamp red, quite good :P

```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w \[\033[0;31m\](\t) \$ '
```

Is there a code to end the red text code? Cause now whatever i type shows up red.

---

### Post by patchwork on 2011-07-10
You must turn off the color red after the timestamp, ie:
```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w \[\033[0;31m\](\t)\[\033[0;0m\] \$ '
```

---

### Post by haqking on 2011-07-10
There are many ways to customise your consoel/terminal.

Remember you dont have to use the Built in terminal, there are tons of others one out there and they all come with different customisation preferences.

I personally use Guake and i love it.

There are lots of others, find the one you like as they all have different settings you can play with ;-)

---

### Post by bodhi.zazen on 2011-07-10
See also :

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

Personally I prefer zsh ;)

You can do a ton if interesting things in .bashrc, here is what I do (I source this file for both bash and zsh).

[http://bodhizazen.net/Tutorials/envrc](http://bodhizazen.net/Tutorials/envrc)

---

### Post by mitk0o0o0 on 2011-07-10
Thank you all for the informative replies. :)

---

