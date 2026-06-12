---
title: "Computer hangs at least 3 times during the last hour"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by shearer_007 on 2009-01-03
I'm a new Linux convert.

I've just installed ubuntu this week. It seems like my system is incompatible with this OS...it has hung at least 3 times in the last hour.

Anyone facing/faced the same problem?

I'm using semphron 2500+ processor 754 64bits

---

### Post by shearer_007 on 2009-01-03
there it is...hang again.

I cant move anything but the mouse

---

### Post by shearer_007 on 2009-01-03
seems like im the only one with the problem :(

---

### Post by sydbat on 2009-01-03
What, exactly, are you doing when this happens? 

Have you had to restart X to solve it (using Ctrl > Alt > Backspace)?

---

### Post by shearer_007 on 2009-01-03
i reset my cpu:(

---

### Post by sydbat on 2009-01-03
> **shearer_007 said:**
> i reset my cpu:(I'm not exactly sure what you mean by that. Do you mean you have rebooted? Can you also tell us what you are doing when your computer "hangs" (ex. what programs are you running, etc)?

---

### Post by shearer_007 on 2009-01-03
I manually press the reset button and reboot my computer.

I only had 2-3tabs of mozilla running when that happens.

---

### Post by sydbat on 2009-01-03
If you can move your mouse, you still have some control over your computer. Hard reboots can be bad if used all the time.

Try this - if the computer stops fully responding, try going to another desktop...Ctrl + Alt + left or right (<- ->). If you can do that and then have full control again, it is probably Firefox acting up. There is an app that you can use to kill the badly acting app. It is called the "Force Quit Button" and can be added to one of your panels by right clicking a panel (top or bottom) and adding to panel.

From the Force Quit help file:> The Force Quit button enables you to select a window to terminate an application. This button is useful if you want to terminate an application that does not respond to your commands. 

To terminate an application, click on the Force Quit button, then click on a window from the application that you want to terminate. If you do not want to terminate an application after you click on the Force Quit button, press Esc.I have used this a few times and it comes in handy if something "freezes".

Back to pressing the rest button/hard reboot - instead, try Ctrl + Alt + Backspace. This will quit the current desktop and go to the login screen. Better for your system to do this if an app freezes and you have no other way to make it respond.

If that does not work, and you HAVE to reboot, use Alt + SysRq + REISUB. This command should reboot a fully non-responsive system.

If either of these do not work, and you can only hard reboot, I would begin checking hardware then software causes.

I hope this helps.

---

