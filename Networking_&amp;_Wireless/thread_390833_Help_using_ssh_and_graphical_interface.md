---
title: "Help using ssh and graphical interface"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by merike on 2007-03-22
I'm trying to use ssh with graphical interface. I am able to log on to one server and then from there to log on to another computer that I want to use for running programs, all that through terminal. But if I wanted to see run programs?
After ssh +x "another computer name here" I get
warning: Need basic cursor movement capability, using vt100

---

### Post by Jussi Kukkonen on 2007-03-22
The command is *ssh -X*. You'll also need to have X11 forwarding enabled on the server  -- if you have admin access, set *X11Forwarding yes* in your /etc/ssh/sshd_config

---

### Post by merike on 2007-03-22
It gives the same message with -X.
I can't change anything but sshd_config has the following lines:
```
# X11 tunneling options
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes
```

---

### Post by merike on 2007-03-24
Any suggestions?

---

### Post by chili555 on 2007-03-24
> I am able to log on to one server and then from there to log on to another computerI just tried this in my network and it works fine. LAPTOP -> server -> MachineA. I got xterm and xminicom to pass back to LAPTOP from MachineA with no complaints.

I wonder if the problem is that, in order to pass X applications back to, in my example, LAPTOP, the machine you log into must have X installed (but not necessarily running). In my case, X is installed on my server, although it runs in runlevel 3, so X is installed but not running.

Is X installed on your server?

---

### Post by merike on 2007-03-24
> **chili555 said:**
> Is X installed on your server?
How would I check that? Although I might have nothing to do with that today since server doesn't let me to log forward. It seems to be one of those with its own moods. Sometimes I'm even unable to log on to server.
Oh and how would it look like when I get it to work? I've never done something like that before. After I have used terminal to log in, how would applications be displayed? Would I have to start them from terminal or will I see another computers whole desktop?

---

