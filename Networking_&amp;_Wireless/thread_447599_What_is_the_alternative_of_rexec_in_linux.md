---
title: "What is the alternative of rexec in linux?"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by hoydooley on 2007-05-18
When I used Windows XP, I used rexec and X emulator (exceed) to connect to a school server to remotely run X programs.
But now I can't do it in feisty.
I don't know what is the alternative of rexec.
I can't use ssh with -X option because ssh daemon is not installed on the school server.
Any suggestions?

---

### Post by Jussi Kukkonen on 2007-05-18
> I can't use ssh with -X option because ssh daemon is not installed on the school server.
Any suggestions?

Well, the server has to have some service running for this to work... Maybe you should find out what services they offer? (then again, rexec maybe a known protocol, I've just never heard of it)

---

### Post by Ken_Lewis81 on 2007-05-18
SSH is the right tool to use; it's the standard remote shell tool.

From looking over the internet, Windows' rexec authenticates you to the remote computer, so you would need to replace that functionality.  Having the school machine run 'sshd' via a set of tools called 'mingw32' would be my recommendation.  I'm guessing you didn't use Remote Desktop for a good reason, but it has parallel functionality in Ubuntu.

I apologise for not being able to offer more help, I don't understand your problem well.

Take care.
Ken.

---

### Post by hoydooley on 2007-05-18
Thanks a lot for your replies.

This is the details of my situation:
I used a X server emulator called "Exceed." when I used windows xp.
I configured the configuration file of exceed to use rexec to connect to it.
I could run X software such as gedit, openoffice, and etc on windows xp through the connection.
But I don't know how to do the same thing in ubuntu.
and i'm a student (not the administrator) so that i can't install any software on the school server.
The OS of the school server is solaris. 
I don't know what kind of daemon is installed on it. 
But i know sshd is not installed on it.

Is remote desktop supported in solaris?
Can I use Applications>Internet>Terminal Server Client?

---

### Post by netztier on 2007-05-18
> **hoydooley said:**
> 
The OS of the school server is solaris. 
I don't know what kind of daemon is installed on it. 
But i know sshd is not installed on it.


Hit the admin over the head with some large trout. Running Unix without some form of SSH is like running a car workshop without a proper tool trolley: you won't ever be able to get anything done properly. Or maybe the sshd is just not available to you, i.e. firewalled? Now that'd make no sense either - leaving REXEC open, but having ssh closed...

Have you tried **telnet** to login to the remote server? Using the same Username/Password you used with REXEC, you should be able to login, set the $DISPLAY variable to point back at your IP address and then launch the application you want to use from the shell. On your local Linux box, you'll have to make sure that X.org allows for incoming connections. Make sure that firestarter or iptables (should you be running either of them) allow for it and that you allow connections from that server with the **xhost** (check **man xhost** for details) command.

Definitely, using SSH with X-forwarding would be best way to do that - also for Windows clients! Do yourself and other users a favour and have word (and/or a beer?) with the admin! ;-) So at least you might find out *why* he doesn't offer SSH on that box.

> **hoydooley said:**
> 
Is remote desktop supported in solaris?
Can I use Applications>Internet>Terminal Server Client?

No, Terminal Server Client supports RDP. That's Microsoft's Remote Desktop Protocol. Chances are few that Solaris is ever going to support that.

best regards and best of luck with the admin

Marc

---

### Post by ricrac on 2007-05-18
Excerpt from .. [http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=r/rexec](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=r/rexec)
...Because it sends passwords to the remote system in clear text, use rexec only on a secure network. See ssh for a more secure alternative....
It's not included default anymore because it's insecure.

If the school is running rexec in the open you can probably telnet and run x apps over telnet.
Were you running a vpn in windows?

Horribly insecure if you're giving all the facts. You should contact their administration.  If this is really on the net, it is bad network citizens like this that provide relays for hackers, instead of spending a few minutes training users to use putty/SSH.

Be sure you never use the same username or password on any other system, since the school one is always comprimised, being used in plain text in a potentially "hostile" environment.

---

### Post by hoydooley on 2007-05-21
I unchecked the System>Administration>Login Window>'Deny TCP Connections to Xserver' checkbox.
and the following method solved the problem.
```
$ xhost + schoolserverip
$ telnet schoolserverip

Login: myid
Password: ******

Welcome!

$ setenv DISPLAY myip:0.0
$ xclock
```

In some shell, I had to replace "setenv DISPLAY" part to "export DISPLAY="
Thank you for all of you again.

---

