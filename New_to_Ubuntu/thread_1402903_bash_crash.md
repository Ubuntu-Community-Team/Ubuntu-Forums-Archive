---
title: "bash crash"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Bob Appleby on 2010-02-09
I believe I understand how to recover from crashed programs, but how do you recover when bash locks up? It just happened and I had to reboot.

---

### Post by mushwars on 2010-02-09
what do you mean by bash? Were you running something in the terminal?

What exactly happened? i.e. "I was typing in open office and my computer froze"

---

### Post by Bob Appleby on 2010-02-10
In the desktop terminal program the command line is known as bash (Bourne Again SHell).I had been using it for several minutes, experimenting with a number of things when it froze up. Since then I have been trying alt+control+f2 which sends the machine to a login mode when it freezes, but I can't find how to do the login. It looks like this:

Ubuntu login
password

In the first line I've typed both the password and on another try, my login name. Nothing shows on the second line when I try to type. Any ideas?

---

### Post by patchwork on 2010-02-10
Your password will not appear on the screen as you type.  Use your username on the login and type your password below.  It takes a certain amount of faith.   That being said, I'm not sure that will stop bash from operating in the background without totally killing the X server...

---

### Post by nothingspecial on 2010-02-10
Nothing shows when you type your password.

Just type your username, hit enter. Then your password which you wont see and hit enter.

---

### Post by muteXe on 2010-02-10
When you say it "froze up", maybe you typed in a command that takes a very long time to complete?  Or maybe typed a command that resulted in an infinite loop?

---

### Post by patchwork on 2010-02-10
Did you try CTRL-C?

---

### Post by Bob Appleby on 2010-02-10
Just tried alt+control+delete using login name and password, as mentioned above and it gave me some login information and left me at the command line. Tried the word login and it complained about the root. pressed alt+control+backspace and it put me back to the login/password phase. exit did not work. what next?

I have not tried control C.

---

### Post by Bob Appleby on 2010-02-11
I went through the bash commands at 
[http://ss64.com/bash/](http://ss64.com/bash/)
and picked out the shutdown command, which seemed to hold promise. When bash freezes, do the following:

control + alt + f2 
then type username and password when asked.
At the $ type sudo shutdown -r now. 
Type the password when asked. 
The system will shutdown and reboot.

---

### Post by nothingspecial on 2010-02-11
> **Bob Appleby said:**
> I went through the bash commands at 
[http://ss64.com/bash/](http://ss64.com/bash/)
and picked out the shutdown command, which seemed to hold promise. When bash freezes, do the following:

control + alt + f2 
then type username and password when asked.
At the $ type sudo shutdown -r now. 
Type the password when asked. 
The system will shutdown and reboot.

Well, that`s bash doing that, so bash hasn`t crashed.

---

### Post by Bob Appleby on 2010-02-12
As I understand it when windows freezes the action produced by alt+ctrl+del does not say that windows did not freeze. By the same token alt+ctrl+f2 would seem to be similar. Doesn't it take control away from bash?

---

### Post by nothingspecial on 2010-02-12
Well in a sense you are starting a new instance of bash by logging in to a new session. You have 6 ofthem Ctrl Alt F1-F6

The 7th is where X runs so you press Ctrl Alt F7 and your gui appears.

I use them like work spaces, if you see what I mean.

---

### Post by AndresM on 2010-02-12
This might confuse a bit, but I&#7743; new: how about alt+f2 then typing xkill and killing the window with the X cursor?

---

