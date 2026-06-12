---
title: "Killing script launched by ssh"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by surfdoc on 2007-10-28
Hi,

I'm having trouble finding a solution to this one! 

I have a script that runs two commands, one locally and one remotely via ssh. The script then waits on a user input before killing the two processes by running

kill %1
kill %2

This kills the locally run command and ssh, but doesn't kill the command run by ssh. 45 mins of googling and i was only able to find that lots of people have the opposite problem (killing ssh kills the remote command).

Any ideas what to do? (Is my setup different to other peoples?)

An example of the problem is:

```

#!/bin/bash

sleep 100000 &

ssh remote "sleep 100000" &

read

kill %1

kill %2
```

Ta

---

### Post by scorp123 on 2007-10-28
Please explain in more details. Why do you even need to "kill" the programs? e.g. why not wait until they finish in a regular way? And what programs BTW?

---

### Post by surfdoc on 2007-11-07
I'm using vlc to stream a video from the local machine. The script then runs vlc on the remote machine to pick up the stream. The remote machine doesn't have a keyboard or mouse so i need to kill vlc when the stream has ended.

Ta

---

### Post by stroyan on 2007-11-07
In general you could use pkill to kill off a process on the remote system.

ssh remote pkill vlc

Or you could use a file on the remote system to record the process id to kill.
Your starting script would background the vlc command and write the process
id into the file using "vlc & echo $! >vlc.pid".  Your shutdown script would kill
that process by reading the file using "kill $(<vlc.pid)".

In the case of vlc you might also consider the remote control feature of vlc itself.

[http://www.videolan.org/doc/play-howto/en/ch04.html](http://www.videolan.org/doc/play-howto/en/ch04.html) has notes on using the "-I rc"
module to provided control over a socket.  It seems that the rc feature will only work if the
vlc process has a controlling terminal.  That can be arranged by starting it via an xterm process.

 ssh remote xterm -display :0 -e "'vlc -I rc --rc-host remote:2010 /videos/a.vob"

 echo help | netcat -q 1 remote 2010
 echo quit | netcat -q 1 remote 2010

---

