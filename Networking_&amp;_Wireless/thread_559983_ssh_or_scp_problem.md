---
title: "ssh or scp problem"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by Jareth on 2007-09-25
Hi,
can't seem to locate this specific prob.

I want to transfer a file from my ubuntu machine to a windows machine using scp. I can already do this between 2 ubuntu machines but have no idea what to do regarding a windows comp.

I would normally type:
scp localfile.txt username@192.168.0.2:/home/username/

but thats for my ubuntu to ubuntu machine,
what would I type for ubuntu to windows machine?
Does the windows machine need something installing aswell?

Ta for now!

---

### Post by elvis on 2007-09-25
SCP relies on a running SSH daemon on the host machine.  Windows, being terribly inferior in that regard, does not come with a preinstalled SSH daemon.

You will need to add one yourself.  The simplest way is to use Cygwin:
[http://www.cygwin.com/](http://www.cygwin.com/)

And follow the guide here:
[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

You will need to make sure that the user you log onto Windows with has a password set.

---

### Post by _Phil on 2007-09-26
Either you install a SSH Daemon on Windows if you want to push the file from Ubuntu or you connect from windows to the Ubuntu machine using WinSCP, a graphical SCP Client for Windows. I would do it this way..

[http://winscp.net/eng/download.php]("http://winscp.net/eng/download.php")

cheers
phil

---

