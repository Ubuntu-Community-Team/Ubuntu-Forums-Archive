---
title: "Reading .Exes?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Obese Outlaw on 2009-09-13
Basically I want to learn more about this .exe, it is a keylogger but I want to read its commands etc. Wordpad on windows can open .exes and make it readable...but I'm not on windows..so is there something similar to wordpad besides kate? (kate just makes a bunch of question marks)

thanks.

Edit:

Example of what kate shows

$&#65533;B &#65533;HP&#65533;u&#65533;u&#65533;u&#65533;<r@

---

### Post by Malta paul on 2009-09-13
An .exe file is a MS windows execute file and won't work in Linux.
Having said that you may be able run it using 'Wine' or a virtual program like "VirtualBox".

 :D

---

### Post by Obese Outlaw on 2009-09-13
I'm not trying to run it..

I'm trying to READ the file as in explore the coding.

---

### Post by Malta paul on 2009-09-13
Sorry I don't think you can.:(

---

### Post by stderr on 2009-09-13
An .exe is a binary file. Binary is just 0s and 1s. Text files have a character encoding such as ASCII. Binary files don't. With the likes of a hex editor you may be able to pull out some strings, but much of it will appear as garbage. Trying to open a binary file with a text editor (which expects a character encoding of some kind) isn't going to do you much good ;)

Try a hex editor, or you can use a command such as strings to get just the readable strings out of a binary file such as an exe. For example 

```
strings ~/path/to/my.exe
```

To actually explore the code, we're talking about another group of programs entirely, called decompilers - taking compiled code and trying to work backwards to produce some kind of high level language code from that. 

What exactly are you trying to achieve?

---

### Post by Obese Outlaw on 2009-09-13
Thanks for some useful info.

Basically, I want to see where the information is going after the person keylogs me (it's a runescape keylogger) I'm just interested, and if I can figure it out I can get into their logs and see which accounts they got etc.

---

### Post by falconindy on 2009-09-13
I think you're misunderstanding how a keylogger works. It's usually backed by an IRC bot and the keystrokes you enter are sent directly to the bot and output in whatever channel the bot sits in. In order to see what the keylogger captured you'd have to preemptively figure out what port the information is being sent out on and monitor outbound traffic on that port.

---

### Post by Obese Outlaw on 2009-09-13
And I can't figure out ports by reading the exe at all, it wont be in the code :confused:?

---

### Post by NCLI on 2009-09-13
You can use Wireshark to monitor your network traffic.

---

### Post by falconindy on 2009-09-13
> **Obese Outlaw said:**
> And I can't figure out ports by reading the exe at all, it wont be in the code :confused:?
A keylogger is a separate program that installs like a trojan virus. It doesn't **only** capture keystrokes from a particular program -- it captures **all **of them. A single key logger could capture your bank account user/password, your runescape login/password and your email user/password. It's up to the recipient of the captured keystrokes to determine what they're related to.

---

### Post by Obese Outlaw on 2009-09-13
Yeah I know what they do, all I am trying to do is read the file and eventually figure out where all the strokes are going and read them.

---

### Post by stderr on 2009-09-13
Far easier than trying to decompile code will be, as NCLI says, to let the keylogger run, not type anything sensitive, and monitor your outgoing traffic with something like wireshark. Minimising your itnernet usage over the period will help distinguish it frmo other normal traffic. But chances are, just grabbing an IP and port won't help you much, if whoever's doing it is any good.

---

