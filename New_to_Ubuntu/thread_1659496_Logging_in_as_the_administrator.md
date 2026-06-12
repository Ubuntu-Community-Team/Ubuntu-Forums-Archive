---
title: "Logging in as the administrator"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by JoeLeeto on 2011-01-04
Hey everyone, I was exploring Maverick Meerkat just these days and I think I must have clicked somewhere I shouldn't, because when I logged in again, Ubuntu asked for a password that I had no idea of what it was.  
I tried to use the password I have to enter whenever I tried to install something through the Programs Central, but no work. What I wanted to know is, is there a way to log in as the administrator of the computer, on that "pick-your-user" screen thing? If not, is there a a way of having Windows XP recognize Ubuntu partitions (don't remember the name), so I can at least recover my files? Thanks in advance. Any other info you might need, feel free to ask, I'm  the one who needs help :D

---

### Post by or3x on 2011-01-04
have you tried logging in as root?
to do that, choose other at the login screen, then type root

---

### Post by karthick87 on 2011-01-04
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lisati on 2011-01-04
When you installed Ubuntu, it will have asked you for some details for your new installation's first user. This is your administrative user.

By default, the "root" user is disabled in Ubuntu. The preferred method of gaining administrative privileges is with the sudo command. More information can be found at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by johnalexrob on 2011-01-05
> **or3x said:**
> have you tried logging in as root?
to do that, choose other at the login screen, then type root

Can you do that? I thought that ubuntu disables the root account and you cant do that from the login screen anyway.

---

### Post by JoeLeeto on 2011-01-06
Argh, things aren't looking good to me... I was going to try the root-as-a-username thing and got stuck at the "Checking Battery State" at boot :(
Tried to Ctrl+Alt+F6, and a login thingo showed up. Then I read the other answers and discovered I can't do that root thing. All I wanted was to get some of the files inside the notebook that are important, other than that I can format it and start it all over... Any clues? I am willing to even use windows if it is what it will take :D:D
 
 
 
Edit:  First part of the problem solved: Entered in recovery mode and managed to change my password through being root. Now to solve the Checking Battery State, but that's another thread :D Thanks everyone :D

---

