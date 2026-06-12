---
title: "Remote access to a single graphical program running on remote server?"
date: 2015-07-23
forum: Networking &amp; Wireless
---

### Post by andrewlandels on 2015-07-23
Hello,

I have root access to two computers running Ubuntu, one at work and one at home, that I regularly connect between. Is it possible to use ssh -x to connect to a computer remotely, then access a job that's running a graphical interface on the remote computer, and display it in its current state on the local computer?

For a hypothetical example, lets say I have an instance of firefox running on the remote computer and I want to see the web pages I have open on the remote pc from my local pc. Is it possible to open a window which is a copy of the one displayed on my remote pc from the terminal?

I'm not interested in whole-screen share or remote desktop solution, I only want to load the visual display from one specific job id.

Cheers,
Andrew

---

### Post by SeijiSensei on 2015-07-23
That works if you launch the program after connecting with "ssh -X".  Once you have a shell on the remote machine, if you type "firefox &" at the prompt, Firefox will appear on your local screen.

I don't think there's a way to redirect the output of an already running program, but I may be wrong.

---

### Post by gordintoronto on 2015-07-24
What do you have against remote desktop, since it will provide what you want.

---

### Post by tgalati4 on 2015-07-25
With a script to set the approriate environment variables that then runs your specific job, it may be possible:

[http://askubuntu.com/questions/203173/run-application-on-local-machine-and-show-gui-on-remote-display](http://askubuntu.com/questions/203173/run-application-on-local-machine-and-show-gui-on-remote-display)

Open a terminal and examine your environment variables in your local environment and your remote environment and note the differences.

```
env
```

---

### Post by andrewlandels on 2015-08-02
Thanks for the responses!

> [COLOR=#000000]What do you have against remote desktop, since it will provide what you want.[/COLOR]
I don't have a specific problem that I want fixed, I'm just interested in learning how the x server works on Linux. I want to know if the input-output is a single, integrated stream - so that only the whole desktop can be interacted with as a complete entity, or if it is made up of discrete parts that can be interacted with on a case-by-case basis. I don't know enough about what I'm asking to ask the right questions for the answers I want - and probably lack the background required to understand the actual answer I want - so I asked using an example instead.

> [COLOR=#000000]With a script to set the approriate environment variables that then runs your specific job, it may be possible:[/COLOR]

[http://askubuntu.com/questions/20317...remote-display]("http://askubuntu.com/questions/203173/run-application-on-local-machine-and-show-gui-on-remote-display")

[COLOR=#000000]Open a terminal and examine your environment variables in your local environment and your remote environment and note the differences.[/COLOR]
Thanks for this - I'll have a play around and see what I find!

Cheers,
Andrew

---

### Post by SeijiSensei on 2015-08-02
X is a protocol that applications can use to redirect their output to a remote display.  You do not have to export the entire display.  Did you try my example of running firefox remotely after using "ssh -X"?

---

