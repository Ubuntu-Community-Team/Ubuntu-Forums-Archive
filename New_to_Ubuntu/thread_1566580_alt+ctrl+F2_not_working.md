---
title: "alt+ctrl+F2 not working"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by NoNameWill on 2010-09-02
I got an update today and after the update my nvidia driver was not working. So I d/l the most current one from nvidia. Checked to see if the adds to the blacklist were still there. 
They were so I logged out and went into terminal through a gui for low graphics.

But when I try to press alt+ctrl+F2 I get nothing. What am I doing wrong?

---

### Post by AlphaLexman on 2010-09-02
Does 'Alt-F2' do what you want?
Or are you trying to get into another terminal?

---

### Post by NoNameWill on 2010-09-02
When I have terminal open neither does anything. I was looking at my keyboard shortcuts and it say ctrl-alt-T to get to terminal. But that doesn't work either.

What I wanted to do is go to tty with no desktop environment. I know I did it before I think when I installed the nvidia driver. I am probably missing a step maybe? The only way I can get nvidia to work stable is to install it this way and not through synaptic.

[http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx)

---

### Post by diablo75 on 2010-09-02
ALT-F1 thru ALT-F6 should all bring up ttys.  ALT-F7 is the GUI.  I'm not sure why this wouldn't work.  Do you have any program open when you're doing this because you shouldn't (or you shouldn't have any "in focus" (on top)) of the desktop because it might "steal" the keyboard command away from the system and do something different or nothing at all.

---

### Post by diablo75 on 2010-09-02
> **NoNameWill said:**
> When I have terminal open neither does anything. I was looking at my keyboard shortcuts and it say ctrl-alt-T to get to terminal. But that doesn't work either.[/URL]

This just creates a new terminal session in the current window with a new tab at the top; like CTRL-T does in Firefox.  And it's not what you're trying to do.  Minimize all programs and then hit whatever ALT-F# key you'd like and it should work.

---

### Post by NoNameWill on 2010-09-02
I just closed firefox and tried it. Nothing. So what do I have to put into terminal to find out what is running?

---

### Post by NoNameWill on 2010-09-02
Ok alt-F5 seems to refresh the desktop. Nothing

---

### Post by diablo75 on 2010-09-02
Can you not just use a regular terminal window to do whatever it is that you're trying to do?  I wasn't aware that there were even minor differences in the way the CLI works between bash in the GUI and a tty.

---

### Post by NoNameWill on 2010-09-02
> **diablo75 said:**
> Can you not just use a regular terminal window to do whatever it is that you're trying to do?  I wasn't aware that there were even minor differences in the way the CLI works between bash in the GUI and a tty.


I can open terminal from applications but when when I tried to install nvidia driver from downloads it said I needed to exit from x server. I had to reboot and start tty from the low graphics window on start.

---

### Post by spiky001 on 2010-09-02
If you type a command in tty terminal ( although you cant see) dose it execute it???

---

### Post by NoNameWill on 2010-09-02
I don't know how to not see it? I did execute the install of nvidia the the sh command through tty.

I just tried doing alt+s to do a quick post and I think alt isn't registering.

---

### Post by spiky001 on 2010-09-02
so it,s just you cant see what you type ( I have the same prob am also looking for info) commands work in mine just cant see what i type
```
sudo reboot -h 0
```
this works so terminal is working
Sorry to hijack post

---

### Post by NoNameWill on 2010-09-02
Thanks all that have helped. I was looking into my keyboard layout and found the problem.  Apparently under keyboard preferences>options. The alt key was set to Key the 3rd level. I don't know that is but I changed it to the win key. Now every thing works.

---

### Post by NoNameWill on 2010-09-02
> **spiky001 said:**
> so it,s just you cant see what you type ( I have the same prob am also looking for info) commands work in mine just cant see what i type
```
sudo reboot -h 0
```this works so terminal is working
Sorry to hijack post

 No problem. Though I can see my commands in terminal so you might have a different problem. :)

---

