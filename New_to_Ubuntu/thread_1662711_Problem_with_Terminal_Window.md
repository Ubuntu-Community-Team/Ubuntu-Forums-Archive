---
title: "Problem with Terminal Window"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by catalina0029 on 2011-01-08
Greetings everyone, 
I am a super newbie here. I installed ubuntu 9.10 a while ago. I've been messing around with it for some time. I recently upgraded to 10.04 ls and it was a mess. I had a problem with the whole grub rescue mess. So I un-installed it and formatted the hard drive. 
I re-installed 9.10 and everything is great again, with one exception. 
When I type (control-alt-F2) to open a terminal window, I have a black screen with a white blinking underline....and that's all. I can see when I type my user name it moves to the next line and I type my password, I think it is at my catalina0029@c-25:~$ but all I see is a blinking underline. How can I get this to show the characters? It worked before I reloaded it. It has to be just a text color thing, but I'm lost.
Thanks,
Dan

---

### Post by star123 on 2011-01-08
> **catalina0029 said:**
> Greetings everyone, 
I am a super newbie here. I installed ubuntu 9.10 a while ago. I've been messing around with it for some time. I recently upgraded to 10.04 ls and it was a mess. I had a problem with the whole grub rescue mess. So I un-installed it and formatted the hard drive. 
I re-installed 9.10 and everything is great again, with one exception. 
When I type (control-alt-F2) to open a terminal window, I have a black screen with a white blinking underline....and that's all. I can see when I type my user name it moves to the next line and I type my password, I think it is at my catalina0029@c-25:~$ but all I see is a blinking underline. How can I get this to show the characters? It worked before I reloaded it. It has to be just a text color thing, but I'm lost.
Thanks,
Dan

first of all to open terminal you need a combination ctr+alt+t
well this is the combination in 10.10.. also wen u type a password the cursor doesnt move in linux for security purposes it blinks at 1 position

---

### Post by catalina0029 on 2011-01-08
Thanks Star123 but I'm not using 10.10, I'm using 9.10 and the cursor blinks in one location when I type the password. Cntrl+alt+t doesn't do anything in 9.10

I'm typing black text on a black screen and need to change the text color to anything else.

---

### Post by star123 on 2011-01-08
> **catalina0029 said:**
> Thanks Star123 but I'm not using 10.10, I'm using 9.10 and the cursor blinks in one location when I type the password. Cntrl+alt+t doesn't do anything in 9.10

I'm typing black text on a black screen and need to change the text color to anything else.

listen for password thing i am sure that whichever linux it is cursor blinks at 1 position only..this is due to security reasons.. u ll not see cursor being displaced while typing a password so dont worry about that just enmter the password and be sure wat u enterde

---

### Post by star123 on 2011-01-08
to check and change ur key combination for terminal follow this
link
[http://ubuntuguide.net/add-a-shortcut-key-to-launch-a-terminal-window-in-ubuntu](http://ubuntuguide.net/add-a-shortcut-key-to-launch-a-terminal-window-in-ubuntu)

---

### Post by catalina0029 on 2011-01-08
im not having a problem loggin in, i just cant c the text. its the wrong color. how do i change the color of the text in the terminal window?

---

### Post by star123 on 2011-01-08
> **catalina0029 said:**
> im not having a problem loggin in, i just cant c the text. its the wrong color. how do i change the color of the text in the terminal window?

terminal->edit->profile prefernces->colors->text color chose anycolor u wanna chose

---

### Post by catalina0029 on 2011-01-08
your not reading my original post. when i type (ctr+alt+F2) i have only a black screen. there is no menu bar to select > edit anything
try it, click ctr+alt+F2 and you'll understand what virtual console I'm talking about

---

### Post by star123 on 2011-01-08
> **catalina0029 said:**
> your not reading my original post. when i type (ctr+alt+F2) i have only a black screen. there is no menu bar to select > edit anything
try it, click ctr+alt+F2 and you'll understand what virtual console I'm talking about

just be relaxed first..being angry wont solve ur prob
tell me one thing wen r u pressing ctr+alt+f2... first of all u power on ur machine u lopg inside it.. everything is fine till there then u press ctr+alt+f2 u get the black screen am i right this way ?

---

### Post by catalina0029 on 2011-01-08
ok, i power up the machine and get a logon screen. I type my userid and password and ubuntu loads to the desktop no problem. i can select applications>accessories>terminal and get a terminal window. no problem. but from the desktop if I want to run a virtual console, I type ctr+alt+F2 or F3 or F4 up to F6. typing F7 closes the virtual terminal. when i have the virtual terminal running, i have black font on black background. there-in lies the problem.
not getting mad, just frustrated.

---

### Post by star123 on 2011-01-08
> **catalina0029 said:**
> ok, i power up the machine and get a logon screen. I type my userid and password and ubuntu loads to the desktop no problem. i can select applications>accessories>terminal and get a terminal window. no problem. but from the desktop if I want to run a virtual console, I type ctr+alt+F2 or F3 or F4 up to F6. typing F7 closes the virtual terminal. when i have the virtual terminal running, i have black font on black background. there-in lies the problem.
not getting mad, just frustrated.

this link ll help u
[http://linux.about.com/library/cmd/blcmdl1_setterm.htm](http://linux.about.com/library/cmd/blcmdl1_setterm.htm)

command
setterm -foreground black -background white -store

---

### Post by catalina0029 on 2011-01-08
ain't this a kick in the pants.
i have two dell d810's 
i have ubuntu installed on a separate external hard drive via usb
one computer will show a virtual terminal black background, white text and the other is black background with black text. wtf?  i'm rotflmao
i haven't taken the time to hit the site you suggested because i just got my wireless card working. fixin one problem at a time.
thanks for your help

---

