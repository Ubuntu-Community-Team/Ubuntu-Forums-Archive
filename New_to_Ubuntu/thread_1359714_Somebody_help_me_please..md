---
title: "Somebody help me please."
date: 2009-12-20
forum: New to Ubuntu
---

### Post by folabiklan on 2009-12-20
I installed ubuntu 9.10 on my desktop. When i finished installing i restarted. And it worked fine. When i wanted to shut down i found that the buttons for shut down, hibernate etc would not work. After 30 mins, i found dt the switch user button worked so i shut down on that page.

When i put the computer back on later, it went well, showed the splash screen then shows a small white terminal window. I cannot do anything. Av tried startx it says x is already working error

---

### Post by cartisdm on 2009-12-20
Unfortunately I don't know specifically how to help you out, and I am certain there are others on this forum that can.  However, I've had installations be screwy for just no reason in the past and since it sounds like you just did a recent install it wouldn't hurt to spend another 30 minutes formatting and installing again.

If it happens again, nothing lost and nothing gained.  But if it fixed it, it saves you from waiting on a response on the forums :)

---

### Post by prshah on 2009-12-20
> **folabiklan said:**
> showed the splash screen then shows a small white terminal window. I cannot do anything.

Press Ctrl+Alt+F1 (or F2,F3) to get a text mode terminal (Virtual Terminal). Login as normal, and give the command```
sudo service gdm restart
```

Then press Ctrl+Alt+F7 to switch back to graphical mode. Has the desktop appeared? Please post back for further troubleshooting if required.

---

### Post by folabiklan on 2009-12-20
Thank u so much for responding. Both commands gave errors.  I ran then correctly typed but it gave so output but nothing happened. I can go back to the log on screen where u choose d account but when u try to log on it then goes back to terminal.

Its on a dual boot with windows xp by the way. I used mepis b4 wit no problem

---

### Post by prshah on 2009-12-20
> **folabiklan said:**
> Both commands gave errors.  I ran then correctly typed but it gave so output but nothing happened. I can go back to the log on screen where u choose d account but when u try to log on it then goes back to terminal.

Which "both" commands? I have given only one command.

what is the error output? If it is too long, please post back only the lines that you think are relevant to your situation.

The "white" terminal you talk about seems to me to be the default X. You may apparently not be running a "Window Manager". However, without the detailed error messages, I cannot be certain.

Here's something else to try; at the login screen, enter your username (or select it); but before entering the password, press "F10" and choose "Gnome" as your session. Then enter your password and proceed; does it work as expected now?

If you cannot find "Gnome" in the F10 menu, please select whatever you feel suitable, and see if the situation resolves itself. Otherwise, please post back with what options are available in the F10 menu.

---

