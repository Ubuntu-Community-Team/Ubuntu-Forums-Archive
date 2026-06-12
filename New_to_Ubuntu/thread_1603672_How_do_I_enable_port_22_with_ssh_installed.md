---
title: "How do I enable port 22 with ssh installed"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Mick8882003 on 2010-10-23
I am having trouble backing up to my server, I had a script set up to do so. Now it comes up that port 22 is closed and ssh is installed (on the comp I want to back up.)

Help

Thank you, Mick

---

### Post by HermanAB on 2010-10-23
Check that sshd is running:
$ sudo ps -e | grep sshd

If not, start it.
If yes, test it with telnet:
$ telnet localhost 22

If sshd replies, then it is working.
If not, then your firewall settings may be to blame - either disable it or fix it.

---

