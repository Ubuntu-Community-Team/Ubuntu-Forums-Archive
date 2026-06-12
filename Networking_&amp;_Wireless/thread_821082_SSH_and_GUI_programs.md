---
title: "SSH and GUI programs"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2008-06-06
So I've been playing around with ssh and was thinking, is there any way for me to run a gui program on an Ubuntu Desktop via ssh?  So the program would run on the desktop in the gui?

---

### Post by Farenji on 2008-06-07
Yes, I do it all the time. Couldnt live without it anymore. :)

For that you need to have "X11Forwarding yes" in /etc/ssh/sshd_config on the remote host, and "ForwardX11 yes" in /etc/ssh/ssh_config on your local host but I think it's the default. You can also turn on X11 forwarding in the client with the "-X switch but notice that it wont work if it's disabled on the remote host. If you make any changes to sshd_config you'll have to restart the ssh daemon with "sudo /etc/init.d/ssh restart" before the changes take effect.

You can then just ssh to the remote host and then start up a X application. The display will go over the ssh tunnel (so it's encrypted!) to your local machine and it will look like you're running the application locally. If you include a "&" after the command you get your prompt back, otherwise it will wait until the remote program is closed.


f.e:
```

you@local:~$ ssh -X remotehost
Password:
Welcome to remotehost! bla bla!
you@remotehost:~$ rhythmbox &
you@remotehost:~$

```

And you will get a rhythmbox window on your local screen! You can use the prompt to start up additional X apps, all of them will be appearing on your local screen.

You can also just press alt-f2 and enter "ssh -X remotehost rhythmbox", it will do the same.

---

