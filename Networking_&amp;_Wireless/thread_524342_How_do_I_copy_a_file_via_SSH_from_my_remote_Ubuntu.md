---
title: "How do I copy a file via SSH from my remote Ubuntu box to a local Windows box?"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by mjpatey on 2007-08-13
Hi,

I just installed SSH on my Ubuntu machine, and am following  the instructions on this page:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server)

And voila, using Putty, I'm able to login remotely to my Ubuntu machine from a Windows machine on the network.  Yay!

However,  I'm having a hard time copying a file from the Ubuntu machine to the Windows machine.  In the section that describes "How to copy files/folders from remote Ubuntu machine into local machine (scp)," I tried the command given, in the following format:

```
scp -r username@192.168.0.1:/home/username/remotefile.txt .
```

The "." at the end evidently tells SSH to copy the file to the current directory-- but it's the current directory of the SSH session, not a directory that's located on my local machine.  How would I copy that hypothetical file in the example (remotefile.txt) from the remote Ubuntu machine to a directory on the local Windows machine on which Putty is running?

I also tried playing an mp3 remotely just to see what it did (I typed "mplayer filename.mp3), and it faithfully played... on the Ubuntu machine.  I can see why this happened, but I was hoping to play it on the machine from which I issued the command.

Thanks for any help you may have!

-Mark

---

### Post by eentonig on 2007-08-13
You'll have to run a SSH server on the windows box. 

When I'm at work, I use winscp (can be downloaded from the same location as Putty I think) to get files from SSH servers. Or, If I'm using SecureCrt, I open a sftp tab and use the CLI.

---

### Post by HermanAB on 2007-08-13
SSH is a client server system.  Unix machines usually has the full SSH installed by default.  Windows doesn't.  You can install PuTTY, but that is only a SSH client, it is not a server.  To get a server on Windows, you need to install Cygwin and OpenSSH, then configure the SSH daemon to start when the system boots up.  This is somewhat tricky.

The general syntax is like this:
scp from to

PuTTY, scp and ssh are client programs that connect to a remote sshd server.

1. Linux/Linux:
Say you have two Linux machines and both have SSH daemon installed:
If you are at the local machine then you are already logged in, so you need login credentials for the remote machine, to copy from the local machine to the remote machine:
scp /home/whoever//wherever/file username@1.2.3.4:~/.

The other way around, from the remote machine to the local machine:
scp username@1.2.3.4:/home/whoever/wherever/file .

This works because there is a server on the remote machine.

2. Windows/Linux: 
Bear in mind that the SSH server daemon sshd runs on the Ubuntu machine.  Unless you install Cygwin and OpenSSH on Windows, you cannot use ssh or scp  while at the Linux machine because there is no server on Windows to connect to.  You need to be at the Windows machine and use the PuTTY client to connect to the Linux sshd server.

I hope that helps!

Herman

---

### Post by GarlicFish on 2007-08-13
If you are on  windows client, you can use the directory syntax of windows for the local file name.
I use pscp that is available with putty.

e.g.

pscp [email]user@remotemachine:/home/user/remotefile.txt[/email] d:\temp\localfilename.txt

or the other way round 
pscp c:\windows\blah.exe user@remotemachine:/tmp/

Be aware that wild cards can lead to wierd behaviour due to lack of case sensitivity on windows.  So usually best to specify whole file names.

also check out psftp for more interactive file copies.

---

### Post by mjpatey on 2007-08-13
Thanks, everyone!  I installed WinSCP on the Windows machine, and it works like a charm for file transfers!  So when I go on vacation and need a file from my Ubuntu machine at home, I can simply run WinSCP from a thumb drive to connect to the SSH server, and voila!

I also like how WinSCP resembles a graphical FTP client... very familiar.  :-)

Thanks again for the help!

-Mark

---

### Post by wirelessmonkey on 2007-08-13
You can also use psftp, from the Putty folks [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) 

Then you can just sftp into the remote machine and pull whatever you'd like.

---

