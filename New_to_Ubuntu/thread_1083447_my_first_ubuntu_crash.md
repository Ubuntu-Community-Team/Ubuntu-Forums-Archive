---
title: "my first ubuntu crash"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by jimmybarcelona on 2009-03-01
So I experienced my first ubuntu lock up today, and don't know what caused it. The problem seemed to stem from firefox. My internet stopped responding, but still showed as connected in the upper right corner. Anytime I tried to left or right click on the network icon in the corner, the computer would freeze for about 20 seconds or so. While it was frozen I thought it was a GUI failure, so I hit ctrl+alt+F2 to switch to a virtual console. There I ran "sudo shutdown -r now" to try and reboot the system. Bash took the command, but then it just sat there. So I didn't have my place to type in commands anymore, because it was still working on the last shutdown command, but it wasn't doing anything. So I ctrl+alt+F7 back to the GUI to find it unfrozen. I try to shutdown normally, but a window comes up that says firefox is still running. I switch to terminal and type in "killall firefox" but it doesn't appear to work. Everytime I try to shutdown it still says firefox is running somewher inthe background. I used top at the command line, but didn't see it. Finally I just tell the computer to turn off without waiting for firefox, and it freezes. I had to hold down the power button until it shut off. What should I have done in this situation?

---

### Post by taurus on 2009-03-01
Should look to see if something that is associated with firefox from the output of this command.

```
ps -A
```

---

### Post by utnubuuser on 2009-03-01
In terminal> topwould tell you what's taking up compute cycles.
if you've got it installed, htop is a little clearer at times.

then ps -A to get the process id no# to kill.

---

