---
title: "Can't connect to X server"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by IamAcoconut on 2007-01-04
I sshed into a server, and everything's fine until I try to use apps with GUI. I get ```
cannot connect to X server

```On my previous OS opening port 6000 solved the problem (so my local pc could be an X server). How to do it in Ubuntu? I can't do it via Firestarter (can't add any rule).

---

### Post by IamAcoconut on 2007-01-05
Nobody knows how to open a port?

---

### Post by netztier on 2007-01-05
> **IamAcoconut said:**
> Nobody knows how to open a port?

[LIST]
[*]does the remote SSH server support X-forwarding? check /etc/ssh/sshd.config if it is a linux box.
[*]did you invoke the ssh connection with the **-X** option to enable X fowarding?
[*]what is the content of the DISPLAY environment variable on the remote system? Try [FONT="Courier New"]**echo $DISPLAY**[/FONT]
[*]when using X forwarding over SSH, make sure that there's no login scripts on the remote system that automatically set the $DISPLAY variable based on your source IP address.
[/LIST]

If before, you needed to open port 6000 with an SSH connection, you were not using SSH to "carry" the X session, but you used native X transport over TCP, which is something firewall admins rarely like to see, because it requires a port to be opened on (local) firewalls and the TCP connection needs to be setup in the incoming direction.

For native X transport, the [FONT="Courier New"]**$DISPLAY**[/FONT] variable will read something like [FONT="Courier New"]**yourpc.yourdomain.com:0.0 **[/FONT]or [FONT="Courier New"]**<your ip address>:0.0**[/FONT]. As mentionned above, this will most probably have been set by a login script on the remote system. 

When using X forwarding with SSH, [FONT="Courier New"]**$DISPLAY**[/FONT] should be something like [FONT="Courier New"]**localhost:11.0**[/FONT]

There's no need to open tcp/6000 or any other port; all you really need is X forwarding over SSH.


best regards

Marc

---

### Post by IamAcoconut on 2007-01-05
Thanks, Netztier!
I forgot the -X option, as I've been previously using KSSH which did it for me.
Now it works

---

