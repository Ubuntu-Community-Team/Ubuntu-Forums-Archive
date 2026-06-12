---
title: "running headless + vnc"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by jsteezy on 2010-05-21
I want to be able to turn on the computer, then vnc into it without using a keyboard on the computer itself.  My goal is to just leave it plugged into my tv acting as a file+music server, and then if I wanted to watch something on the tv I would be able to just switch the input on the tv to the computers video output. I have all this set up and working properly, but if I need to restart the computer, I have to have a keyboard plugged into it so I can login, I can then immediately start the vnc client on my laptop.  I read a few guides but they all seemed outdated and I couldnt follow them.  Any help is appreciated, thanks

---

### Post by ayenack on 2010-05-21
You may be better off installing SSH.

Take a look at this.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) (Follow the links at the bottom of the page.)

To restart the comp in an ssh session you'd do this.

```
sudo reboot
```

To shutdown you'd do this.

```
sudo shutdown now
```

An alternative to VNC is FreeNX with SSH.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by nhasian on 2010-05-24
jsteezy,

I'm bumping your thread because i would like an answer to this question as well.  Let me know if you found the solution for the issue.

---

### Post by jsteezy on 2010-05-25
When I use NX it starts a new session on the client computer, so nothing I do from the client computer is reflected on the monitor of the server computer.  I am able to login this way without touching the server, so I guess this sort of solved my problem.

Is there some command I can use to switch the server to reflect what I am doing with the client? Im sure I am using all the wrong terms here, I apologize, like I said I am new to linux in general but if someone could point me in the right direction I would really appreciate it.

---

### Post by bodhi.zazen on 2010-05-25
> **nhasian said:**
> jsteezy,

I'm bumping your thread because i would like an answer to this question as well.  Let me know if you found the solution for the issue.

Use ssh.

You do not need to ssh into the box to reboot, simply use ssh

```
ssh user@server sudo reboot
```

You do not need a VNC server or Freenx to issue a reboot command.

You can do all your sysadmin with ssh , forward X applications if needed ```
ssh -X user@server
```

If you need to admin a server, and you want a graphical interface, use webmin.

---

### Post by jsteezy on 2010-05-25
I dont need to admin much, I have everything set up the way I want server-wise (files, printers, web), to the point where as long as the server is turned on everything runs.  I run into problems when I switch the TV to the computers video output and then try to VNC in.  At that point I cannot do anything on the TV, unless I attach a keyboard to the server and login, and then VNC after that.  I can ssh into it without logging in with a keyboard but then nothing I do shows up on the TV.

---

### Post by nhasian on 2010-05-25
> **bodhi.zazen said:**
> You can do all your sysadmin with ssh , forward X applications if needed ```
ssh -X user@server
```


Thanks for the tip.  although i've used ssh for terminal stuff, i didn't know I could forward X applications with the -X switch.

I think that jsteezy and I however may be encountering a bug?  Or maybe is a security feature :)  I have my HTPC running Ubuntu 10.04 DE set to auto-login so the desktop comes right up.  When I try to use the Remote Desktop Viewer from my laptop however, a dialogue box appears saying:

"Unlock Login Keyring
Enter password to unlock your login keyring
The login keyring did not get unlocked when you logged into your computer"

it prompts me for my password before allowing me to remote access into the HTPC which defeats the whole purpose.

---

### Post by johnyates on 2010-05-25
[http://blogs.computerworld.com/ubuntu_auto_login_problem_solved](http://blogs.computerworld.com/ubuntu_auto_login_problem_solved)

---

