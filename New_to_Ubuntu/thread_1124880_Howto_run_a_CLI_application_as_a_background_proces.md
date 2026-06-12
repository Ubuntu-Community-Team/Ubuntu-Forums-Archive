---
title: "Howto run a CLI application as a background process?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by jevchance on 2009-04-13
Hello,

I'd like to use HandBrakeCLI to encode videos. However, its an interactive CLI application. I'd like to start the process and send it to the background so it just runs until it finishes without interaction (daemon?).

The HandBrakeCLI command looks something like this:

$ HandBrakeCLI -i input.avi -o output.m4v --preset="AppleTV"

When I run this command, the application shows me the progress continually until the encode is finished. Ideally, I'd like to immediately get back to the command prompt, then see the program running as a process using top, at least until its finished.

I tried this command:

$ HandBrakeCLI > /dev/null -i input.avi -o output.m4v --preset="AppleTV" &

I thought that would work, but its not. Maybe I have the syntax wrong, not sure.

Can someone please shed some light on this for me?

---

### Post by freakyzoidberg on 2009-04-13
guess you can try this

> HandBrakeCLI -i input.avi -o output.m4v --preset="AppleTV"  > /dev/null 2>/dev/null &

2>/dev/null stand for stderr redirected to null as stdout

---

### Post by hyper_ch on 2009-04-14
you might want to have a look at screen. It will not run things in the background but you will have a virtual terminal session in which you can have multiple terminals. You can detach it and re-attach it anytime you want. So you still have all the output info there and can check its status anytime.

---

### Post by anewguy on 2009-04-14
I thought you could fork unattached processes from the CLI?

Dave :)

---

### Post by WhiskyChris on 2009-04-14
To run a command in the background you would put & at the end of the line, for instance

```
firefox &
```

would open the firefox web browser in the background, and return the prompt to you after showing you the PID of the process. After firefox is closed (the process is finished) you are told so in the terminal. The problem with this however is that closing the terminal kills the process.

Another command you can look into is nohup, running

```
nohup firefox
```

would run the process firefox, returning full control of the prompt. This is useful for initiating long processes via ssh, allowing you to logout again while the process keeps on going.

Hopefully one of these will be what you need!

EDIT: Firefox is an example of a command to run as I'm currently looking at a firefox browser - obviously this can be substituted with whatever command you need to run!

---

