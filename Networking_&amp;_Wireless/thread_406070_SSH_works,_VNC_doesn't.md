---
title: "SSH works, VNC doesn't"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by sohanley on 2007-04-10
I have been happily connecting to my Ubuntu machine via Remote Desktop for many months, with no problems. Suddenly today, when I attempt to connect (using TightVNC on a WinXP box), nothing seems to happen. It doesn't ask me for my password, and it doesn't time out with an error message about being unable to reach the server. Just nothing at all.

Meanwhile, I *am* still able to SSH into my Ubuntu box. So I'm confused as to what might be causing the VNC problem.

Anyone know how I can diagnose and resolve this problem? Note that I can only SSH, so any solution has to be completely within the terminal. One of the things I was hoping to check was Firestarter, to see if maybe the port VNC connects to is no longer unblocked. How can I check what ports are blocked/unblocked/forwarded via the command line?

---

### Post by bnuytten on 2007-04-21
From your WinXP box: open a command prompt and try: telnet UbuntuIP 5900. You should see output like this:
```
RGB 003.007
```.
Close the connection using ctrl+] and type quit. If this does not work, try telnet UbuntuIP 22 and you should see SSH-blahblah string.

You can check if ssh/vnc is listening on your Ubuntu box with netstat. You should see at least the lines below:
```
netstat -tanp
tcp6       0      0 :::5900                 :::*                    LISTEN     10925/vino-server   
tcp6       0      0 :::22                   :::*                    LISTEN     6830/sshd           

```

---

