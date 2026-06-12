---
title: "can the password be typed once?"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by sallam on 2010-10-22
Greetings

I get asked for my passwords many times. Is there a way to set this so that I type it once and then ubuntu trust me for the rest of the time the laptop is on?
I noticed that if I log off then log in, typing my username and password in the process, ubuntu let me be for the rest of the log in time.

---

### Post by Zzl1xndd on 2010-10-22
Ubuntu should only ask you for your password while logging in, or when you access something that requires elevated privileged (Eg: installing software via the software centre or package manager).

There are methods of getting around this, however it isn't recommended and normally isn't discussed in the forums.

---

### Post by Paqman on 2010-10-22
> **sallam said:**
> Is there a way to set this so that I type it once and then ubuntu trust me for the rest of the time the laptop is on?


Ubuntu does trust you, but the only way it can be sure that it's you is to get you put your password in.

---

### Post by malspa on 2010-10-22
It's an interesting question, though.  I personally would not do this, since it tosses away one of the main things that makes Linux the secure OS that it is, but I've often wondered why folks who have an aversion to typing in passwords don't simply always run as root.  Or, if they're Ubuntu users, create a root account and then always run as root.  I think doing so would be inviting trouble, but it's your system, not mine.

---

### Post by coffeecat on 2010-10-22
> **sallam said:**
> I get asked for my passwords many times.

If you get asked many times then you must be doing system changes many times. Are you sure you need to? Apart from login you are prompted for your password only when you do something that needs administrator powers, such as installing software or updating the system or running commands with sudo in the terminal. Even then there is a 15-minute timeout so that you are not re-prompted within this 15-minute window. 

> **sallam said:**
> Is there a way to set this so that I type it once and then ubuntu trust me for the rest of the time the laptop is on?

Yes, but I will say no more. :wink:

> **sallam said:**
> I noticed that if I log off then log in, typing my username and password in the process, ubuntu let me be for the rest of the log in time.

The only explanation I can think of for this is that you did not do anything requiring administrator privileges after you logged in again.

---

### Post by Hippytaff on 2010-10-22
Might be worth reading this - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ivarn on 2010-10-22
The password is a protection and is there for a reason.
You can auto login though. But the password protects you from system breakdowns.
What if you get hacked? You can get hacked if you use a server because ports are then open. So if you get hacked, the hacker can't hurt your pc much.
This is also why your password is hidden when you type it in terminal.
If your password is hard or takes long time to type, then change it to something easier.
If you don't run a server on your pc you can use an easy password such as your name, username or something.
You can also delete the keyrings password. Just go to your home folder > .gnome2 and delete the keyrings folder. restart the pc and on your next login it will ask you to set a new keyring password, leave it blank and click OK. Now it will tell you how this can be a security risk so just press yes to continue.

EDIT: If you don't care about the security at all. Here's how you disable the password. But do this on your own risk since this is NOT recommended 
Go to the terminal and type:
```
sudo visudo
```
Find the line that says:[FONT=monospace][/FONT] %admin ALL=(ALL) ALL[FONT=Verdana]
[/FONT]and change it to:[FONT=monospace][/FONT] %admin ALL=(ALL) NOPASSWD: ALL[FONT=Verdana]
[/FONT]Now, save the file and you're done.

---

### Post by oldos2er on 2010-10-22
> **sallam said:**
> I get asked for my passwords many times. 

**sudo -i** will give you a root terminal which remains open until you close it.

---

### Post by Rubi1200 on 2010-10-22
> **oldos2er said:**
> **sudo -i** will give you a root terminal which remains open until you close it.
+1 to this suggestion!!

Although it is possible to modify sudoers, I would recommend against it for all but highly experienced users who know and understand the potential risks of such an action. One mistake and your system could be compromised!

```
sudo -i
``` allows you to administer the system in a root environment, but be warned that this, too, can lead to some nasty results if you are not careful.

---

