---
title: "sudo/gksudo"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by Primus1 on 2010-08-16
I have searched and found that gksudo should be used when dealing with graphical applications.
Is there an easy way to know what is a graphical app and what isn't, ok Gimp is graphical, so is gksudo only used on apps in the Applications- Graphics part of the menu list?

---

### Post by Primus1 on 2010-08-16
I have searched and found that gksudo should be used when dealing with graphical applications.
Is there an easy way to know what is a graphical app and what isn't, ok Gimp is graphical, so is gksudo only used on apps in the Applications- Graphics part of the menu list?

---

### Post by Zeike on 2010-08-16
> **Primus1 said:**
> I have searched and found that gksudo should be used when dealing with graphical applications.
Is there an easy way to know what is a graphical app and what isn't, ok Gimp is graphical, so is gksudo only used on apps in the Applications- Graphics part of the menu list?

Graphical in this case doesn't mean apps that deal with apps, it means apps that have a GUI (graphical user interface).  Everything that you don't run completely in a terminal or console is 'graphical' in this sense.

---

### Post by bodhi.zazen on 2010-08-16
> **Primus1 said:**
> I have searched and found that gksudo should be used when dealing with graphical applications.
Is there an easy way to know what is a graphical app and what isn't, ok Gimp is graphical, so is gksudo only used on apps in the Applications- Graphics part of the menu list?

Why would you run gimp as root ?

In general, you should only be performing system administration as root.

In general, commands you run in a terminal use sudo

sudo chmod ....

Applications, such as gedit or nautilus or networkmanager, are graphical.

---

### Post by ubudog on 2010-08-16
Say you want to open the file manager as root.  It is better to use gksudo for that.  You can do that using the command:
```
gksu nautilus
```  (nautilus is the file manager)

For GIMP though, you do not need to be root (admin) to run it, so it does not use gksudo.

---

### Post by Ozymandias_117 on 2010-08-16
> **Primus1 said:**
> I have searched and found that gksudo should be used when dealing with graphical applications.
Is there an easy way to know what is a graphical app and what isn't, ok Gimp is graphical, so is gksudo only used on apps in the Applications- Graphics part of the menu list?

A graphical app is anything that has a window. If it only runs in the terminal, then it isn't graphical.

---

### Post by ubudog on 2010-08-16
But you only need to use gksudo for graphical apps that need to be ran as root.

---

### Post by Primus1 on 2010-08-18
Sorry about this late reply, I've been having problems.

Thanks for the answers, I get it now. Marking this as solved.

---

### Post by Primus1 on 2010-08-18
"Why would you run gimp as root ?"

I don't, just giving it as an example of what I thought (then) was 'graphical' but from your answer I understand the difference now, thanks.

marking as solved.

---

### Post by lisati on 2010-08-18
Threads merged. 

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2010-08-18
> **Primus1 said:**
> "Why would you run gimp as root ?"

I don't, just giving it as an example of what I thought (then) was 'graphical' but from your answer I understand the difference now, thanks.

marking as solved.

OK, we do not have to slap you with a wet fish then :lolflag:

Glad you got your question answered.

---

### Post by Primus1 on 2010-08-19
Thanks guys, I admonish myself, the link you gave looks familiar, I think I've read it before! What a memory!

HAL: "I can feel it Dave ... I'm losing my mind ..."  :)

---

