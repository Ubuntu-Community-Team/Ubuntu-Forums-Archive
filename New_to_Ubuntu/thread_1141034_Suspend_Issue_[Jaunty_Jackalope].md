---
title: "Suspend Issue [Jaunty Jackalope]"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Testrum on 2009-04-28
I absolutely live off of suspend. Every night before I go to bed I press my power button on my laptop (have it set to go into suspend mode) and ever since the upgrade to Jaunty Jackalope I've had errors with suspend. It will go into suspend mode perfectly fine but when I go to wake up there's nothing but a blank screen no matter what I do, ex. click the mouse, hit keys, etc. But when I hit the power button it fires up like I had turned it off completely :confused:

---

### Post by Ugluk on 2009-04-28
Same problem here.

---

### Post by chrisod on 2009-04-28
I had that problem with 8.04 but in Jaunty suspend is now working normally again. Go figure... In 8.04 I found that suspend worked if I invoked it from the command line, but not if I selected it from the GUI or just closed the laptop lid. You might want to try suspending from the CL and see if you get a better result. This is the command that was working for me.

```
sudo /etc/acpi/sleep.sh sleep
```

---

### Post by Testrum on 2009-04-28
> **chrisod said:**
> I had that problem with 8.04 but in Jaunty suspend is now working normally again. Go figure... In 8.04 I found that suspend worked if I invoked it from the command line, but not if I selected it from the GUI or just closed the laptop lid. You might want to try suspending from the CL and see if you get a better result. This is the command that was working for me.

```
sudo /etc/acpi/sleep.sh sleep
```
I'll try that but I really don't want to have to input a command line every time I want to enter suspend mode :(

---

### Post by chrisod on 2009-04-28
It's really not that big of a deal. Put a terminal shortcut on the task bar - and if you don't use the terminal regularly it's a simple up arrow to recall the last command and enter. Honestly I think it's quicker than clicking and selecting suspend.

---

