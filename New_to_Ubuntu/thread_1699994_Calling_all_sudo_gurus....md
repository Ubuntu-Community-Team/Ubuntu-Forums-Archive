---
title: "Calling all sudo gurus..."
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Procreate on 2011-03-04
I've been doing a little bit of reading and I've learned that the sudo command is one of the more (if not, most) important commands. I've read that it gives the user temporary privileges to execute a change to the system, or something along those lines. Does the sudo command give the user root privileges? Or simply admin privileges? How much power does it give exactly? If someone could clarify that'd be great.

I understand that sudo is a security measure and supposedly works like a charm. So does it make the system more secure simply by requesting a password to make changes that could possibly affect the system? Couldn't all changes, even the slightest (such as changing the time) affect the system? Why doesn't it ask for a password for everything you do? I'm confused as to *when *a password prompt is required. How does it know when to prompt for a password...because it seems like even the slightest changes are still changes. How does it discriminate between a small change and a large change? 

Lastly, I've read that it's comparable to the UAC on Windows OS. Would you say it's more secure than UAC? Any advantages or disadvantages over UAC? Better overall?

Sorry for the Q's- I'm just getting into Linux and I'm trying to learn as much as I can...interesting stuff. :D

---

### Post by HermanAB on 2011-03-04
Howdy,

You need to read up on it:
$ man sudo
$ less /etc/sudo.conf

---

### Post by mcduck on 2011-03-04
sudo is a tool that allows you to run a command (or a program ) as some other user. ("**S**ubstitute **U**ser **DO**") If you don't specify any user it assumes you wish to run the command as root user (assuming your normal user account has permission to do that, only admin users do...)

It will ask for password regardless of what you try to run, but has by default a time limit so it doesn't ask you repeatedly (if I remember right the default time limit is 15 minutes, so if you run another command with sudo during that time you don't need to enter the password).

It's not actually "sudo" that's intended to make the system more secure, but the strict use of user accounts with limited power what does that. Normal users don't have the ability to change anything in the system, and that includes admins as well (admins just have the right to temporarily become the root user, who *does* have the power to do anything).

Anyway, you might want to read this one: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ikt on 2011-03-04
> **Procreate said:**
> Lastly, I've read that it's comparable to the UAC on Windows OS. Would you say it's more secure than UAC? Any advantages or disadvantages over UAC? Better overall?

UAC is highlighted by CANCEL OR ALLOW?

If you click cancel whatever was happening may throw up an error message, but if you click allow no negative feedback is provided, therefore if you want to avoid as much fuss as possible you're going to click allow, which leads to people clicking allow mindlessly.

With the prompts in ubuntu for running as root, you are required to enter your password, which you will identify with, what wants to run as root and why should I enter my password?

Small fundamental differences make UAC an 'annoying pop up message' and Linux sudo/admin request a serious question.

> **Procreate said:**
> 
Sorry the Q's

I do not understand why you would be sorry for asking questions?

This is a forum where people can reply if they want, no one is forcing people to reply, therefore people asking questions is wanted, so thank you for the questions :)

---

### Post by seawolf167 on 2011-03-04
Essentially, sudo (**S**uper **U**ser **DO**) allows you to run something with root access without being logged in as root.[I]

sudo [/I]also has a graphical frontend called *gksudo*, just like *gksu *is the frontend to *su*. You would use the *gk-* version when you need to run a graphical program as root without logging in as root.

---

### Post by mcduck on 2011-03-04
> **seawolf167 said:**
> Essentially, sudo (**S**uper **U**ser **DO**) allows you to run something with root access without being logged in as root.[I]

sudo [/I]also has a graphical frontend called *gksudo*, just like *gksu *is the frontend to *su*. You would use the *gk-* version when you need to run a graphical program as root without logging in as root.

It's Substitute User Do, as the manual says, since it allows you to run a command as *any* other user.

For example "sudo -u mcduck gedit" would run Gedit as user mcduck.

(In the same way, *su* is "Substitute User" and allows you to switch into any other user account, although unlike *sudo* it requires you to have the target user's password.)

---

### Post by seawolf167 on 2011-03-04
Thanks for the info mcduck - I'd only ever heard it referred to by Super User, but now the other commands like you listed make a lot more sense.

---

### Post by Procreate on 2011-03-04
Thanks for the replies all, great information. ;)

I've got some reading to do tonight.

---

### Post by Dagorath on 2011-03-05
OK, I've read all the tutorials on sudo, su, and root privileges that are mentioned in this thread and I have a question.  I should mention that i"m running Kubuntu.

I want to add a line to /etc/apt/sources.list which is owned by root.  From the tutorials mentioned above I thought that I could invoke the Kate editor with root privileges by issuing **kdesudo kate /etc/apt/sources.list **in a terminal.  That command starts the kate editor with the sources.list file loaded but when i want to save the file I get a message saying it cannot be saved.

So... how does one with administrator privileges go about editing and saving a file that root owns?

---

### Post by deconstrained on 2011-03-05
> **Dagorath said:**
> I want to add a line to /etc/apt/sources.list which is owned by root.  From the tutorials mentioned above I thought that I could invoke the Kate editor with root privileges by issuing **kdesudo kate /etc/apt/sources.list **in a terminal.  That command starts the kate editor with the sources.list file loaded but when i want to save the file I get a message saying it cannot be saved.
Save a text file in your home folder, (with a gksudo kate), open up a terminal and type "ls -l". Look at the third column in the row where the test file is displayed. If "root" is not displayed there, then it's a problem with kdesudo or kate. If the program is running as root then it should have superuser privileges when it comes to editing files.

---

### Post by Red Kelly on 2011-03-05
> **Dagorath said:**
> 
.. how does one with administrator privileges go about editing and saving a file that root owns?

Do you have to use kate? try using nano, it will at lest let u know if the problem is with kate or kdesudo.
```
sudo nano /etc/apt/sources.list
```

---

### Post by Dagorath on 2011-03-05
> **deconstrained said:**
> Save a text file in your home folder, (with a gksudo kate), open up a terminal and type "ls -l". Look at the third column in the row where the test file is displayed. If "root" is not displayed there, then it's a problem with kdesudo or kate. If the program is running as root then it should have superuser privileges when it comes to editing files.

That test works as expected and now **kdesudo kate /etc/apt/sources.list **works as it should too!

A pattern is emerging.... I encounter a problem... I post a message about the problem... POOF! the problem magically goes away

---

### Post by anon85 on 2011-03-05
> **mcduck said:**
> It's Substitute User Do, as the manual says, since it allows you to run a command as *any* other user.

For example "sudo -u mcduck gedit" would run Gedit as user mcduck.

(In the same way, *su* is "Substitute User" and allows you to switch into any other user account, although unlike *sudo* it requires you to have the target user's password.)

Correct. and a little catch up with su and sudo.
personally i've never used su. mostly sudo root will do fine and more secure.
ubuntu default set your first user as sudo-er (rootly), but not root. you might wanna give yourself sudo privileged if in other distribution.
but hey for home user, root no root don't matter, unless you sharing your home linux box with strangers. that's just my opinion

---

### Post by Rinzwind on 2011-03-05
> **Procreate said:**
> ...
I understand that sudo is a security measure and supposedly works like a charm. So does it make the system more secure ...

Simpel... compare these...
1. One system that uses root as admin.
2. One system that uses an username as admin.

1. One system that lets you use root to log in.
2. One system that lets an username log in.

In both cases someone trying to access your system remotely knows he only needs a password for root with option 1 and knows he needs both a username and a password with option 2.

Option 2 is more secure. Option 2 is the sudo way.

---

### Post by donkyhotay on 2011-03-05
> **Rinzwind said:**
> Simpel... compare these...
1. One system that uses root as admin.
2. One system that uses an username as admin.

1. One system that lets you use root to log in.
2. One system that lets an username log in.

In both cases someone trying to access your system remotely knows he only needs a password for root with option 1 and knows he needs both a username and a password with option 2.

Option 2 is more secure. Option 2 is the sudo way.

Thats basically it, by not having an account called root you have to guess both username and password rather then password alone. Also proper configuration of sudo allows admins to give users *limited* admin access rather then the everything/nothing you get with root. I believe you can also track sudo usage as well to determine if someone is doing something fishy like asking for privileges they shouldn't have or trying to guess someone else's password.

---

### Post by deconstrained on 2011-03-06
Dammit, disregard this post. I wanted to edit/append but it came out as a double-post.

---

### Post by deconstrained on 2011-03-06
> **Dagorath said:**
> That test works as expected and now **kdesudo kate /etc/apt/sources.list **works as it should too!

A pattern is emerging.... I encounter a problem... I post a message about the problem... POOF! the problem magically goes away

I've had that happen before. I've often found it happens when I unconsciously did something different or changed something, even as trivial as rebooting.

[quote=Procreate]I understand that sudo is a security measure and supposedly works like a charm. So does it make the system more secure simply by requesting a password to make changes that could possibly affect the system?[/quote]
Just to be clear, Unix's permissions system encourages you to be more deliberate and careful when you perform actions that can have system-wide ramifications, that's all. As for security, it's better to disable the root user altogether and perform operations as superuser using sudo. For one, there's one less venue along which the system could be compromised. If root's password is found/cracked the system is helpless, whereas an attacker would have to determine (1) the usernames of everyone on the system--not possible remotely, (2) which users are enabled to use sudo (which requires root permissions to begin with, in order to view /etc/sudoers), in addition to (3) their passwords. In the case of root it's just 'root' and then the password.

---

### Post by mcduck on 2011-03-06
> **Rinzwind said:**
> Simpel... compare these...
1. One system that uses root as admin.
2. One system that uses an username as admin.

1. One system that lets you use root to log in.
2. One system that lets an username log in.

In both cases someone trying to access your system remotely knows he only needs a password for root with option 1 and knows he needs both a username and a password with option 2.

Option 2 is more secure. Option 2 is the sudo way.

In addition to that you spend much less time and use much less programs and tools running with full root privileges. Even with an admin account, you still are just a normal user and have no permissions over most of the system stuff, only running the exact thing you need to do with higher permissions.

"Minimum force required" is pretty much the key philosophy in Linux/Unix security. Every user and every service should only have the exact permissions they need to work. That makes security easier to handle, and in case something goes wrong minimizes the possible damages.

This is also the reason why many of the system services in Linux run as daemons, users of their own. That allows configuring their permissions just like any other user's. A web server, a printer driver, a music player and a desktop user all need access to different parts of the system, and have no reason to mess with anything else. None of them should have access everywhere.

---

