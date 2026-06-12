---
title: "Hotkeys? Can this be done in ubuntu?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-13
I want to make a hotkey so that any time I press it commonly used text is placed into whatever document or form I'm currently in. So for example, say I write out my address often so I assign it to a hotkey like Ctrl+G. Then anytime I'm writing an email or a word document or whatever I can just press Ctrl+G and the text is placed into the email/document.

Can this be done in ubuntu?

---

### Post by DaGrimReefah on 2009-07-13
[https://wiki.ubuntu.com/Hotkeys](https://wiki.ubuntu.com/Hotkeys)

---

### Post by ltwinner on 2009-07-13
Thats for multimedia hotkeys on a laptop, not what I'm looking for. I'm looking to assign text to user defined hotkeys.

---

### Post by marcopalla on 2009-07-14
not veryfied but you ca work with it:

> write a file with your address inside: /myT/text.txt

>then write a script file (= a text file):
#!/bin/bash
#this is my command that paste myaddress

paste /myT/text.txt

#end

>then save the previuos like /bin/mycommand.sh

> test in a shell:
[jonny@mypc bin]$ ./mycommand.sh

>then go to System > Preferences > Keyboard Shortcuts and associate your mycommand.sh to a shortcut

would it work?
m.

---

### Post by jmszr on 2009-07-14
Itwinner,

This sounds like what you want: [http://ubuntuforums.org/showthread.php?t=1052846](http://ubuntuforums.org/showthread.php?t=1052846) .

---

