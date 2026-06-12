---
title: "Is PuTTY really needed in Linux?"
date: 2015-11-02
forum: Networking &amp; Wireless
---

### Post by Xayide on 2015-11-02
Do you really need to use PuTTY or another terminal emulator in Linux? There is an SSH and Telnet commands, so what's the difference between using them and using PuTTY, Teraterm or others?

---

### Post by TheFu on 2015-11-02
Putty and teraterm run on Windows.
ssh runs on Unix-like systems.

telnet isn't used since the mid-90s. It is only interesting to troubleshoot issues with other protocols these days. Sorta like  how plain FTP shouldn't be used anymore.

Do you **need** to use ssh? No. But 80+% of the power of Unix comes from using the shell and being able to easily run programs/tasks on remote systems. Much of the power comes from simple automation too. Automation with a GUI is  100x harder than with a tiny script. Would you buy a 130mph sports car and only drive it 35 mph on the freeway?

For example, I wanted to convert 150 or so video files into audio mp3s today. There are probably GUIs which do that, but a few years ago, I wrote a tiny script that does it.   x2mp3.sh.
```
#!/bin/bash

for filename in "$@"; do

   NEW=${filename/%??/mp3}

   mplayer -benchmark -vc null -vo null \
           -ao pcm:fast:file=output.wav $filename && \
      lame --preset cd output.wav "$NEW"
      # lame --preset hifi output.wav "$NEW"
   rm output.wav
done
```
Simple. 1 command   ....  like  **~/bin/x2mp3.sh  /tmp/*mp4** and go work on something else for a few minutes. With ssh, I ran that job on a faster computer in a different room than the netbook I'm using now.

**The network is the computer.** thanks to ssh.

Lots of other examples here.   My "scripts" directory has a few hundred previously-solved answers ready to go.

---

### Post by Xayide on 2015-11-02
Thankyou, that was a great explanation! :D

---

