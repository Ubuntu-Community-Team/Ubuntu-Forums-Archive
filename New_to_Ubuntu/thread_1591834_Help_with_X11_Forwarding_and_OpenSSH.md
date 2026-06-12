---
title: "Help with X11 Forwarding and OpenSSH"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by Sum Guy on 2010-10-09
I've been setting up OpenSSH on a couple of computers, one as a server and the other as a client, and I'm having a bit of trouble getting X11 forwarding to work. I've tried looking up a guide, but nothing I've found seems to work. I think I managed to get it going on the server, as one of the guides I found suggested checking the $DISPLAY variable and mine seemed right, but I can't seem to forward anything. The server is running Ubuntu Desktop 9.04 (what I had on hand when I set it up), and the client is running 10.04. Is there anything else I need to do, other than install and configure OpenSSH?

---

### Post by JustinR on 2010-10-09
What methods have you tried to get it to work so far?

I don't know what you have tried - but because this thread is in absolute beginners section the correct syntax for the command for the client machine should be:
```

ssh -X USERNAME@IPADDRESS

```

Remember that the 'X' is a *_capital_* 'X'.

---

### Post by Sum Guy on 2010-10-10
I've tried that command with that layout, before and after checking the config files for both server and client. On the client, I uncommented the lines that allow X11 forwarding in ssh_config, while in the server I found the line reading X11Forwarding yes was already uncommented, and tried adding X11UseLocalHost no to the end of the file after seeing it in another thread in this section. When I use the above command, I get the statement: 
```
/usr/bin/X11/xauth:  /home/encoder/.Xauthority not writable, changes will be ignored
```
followed by a terminal prompt for the server. When I try a GUI application I get the error:
```
X11 connection rejected because of wrong authentication.
Error: Can't open display: localhost:10.0
```
What else do I need to change?

---

### Post by CharlesA on 2010-10-10
Check the permissions on that file with this command:

```
ls -l /home/encoder/.Xauthority
```

They should look like this:

```
charles@atlantis:~$ ls -l .Xauthority
-rw------- 1 charles charles 54 2010-10-10 02:13 .Xauthority
```

You shouldn't need X11LocalHost, I don't have that setting enabled on my server and X11 forwarding works fine.

---

### Post by Sum Guy on 2010-10-10
Thanks for pointing that out. It was owned by root, so I changed it and now it works! Thanks again.

---

