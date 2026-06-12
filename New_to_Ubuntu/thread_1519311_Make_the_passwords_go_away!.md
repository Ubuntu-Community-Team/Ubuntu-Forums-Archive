---
title: "Make the passwords go away!"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by austellis on 2010-06-28
Ok, I am a TOTAL newbie with the Linux, Ububtu, everything.  I came from Windows XP...and figured id try something new.  I love it so far...just 2 issues...one is I cant figure out how to make WINE work...but thats for another thread - the big one is - IM FREAKEN TIRED OF IT ASKING FOR A PASSWORD!!!  I set it to just log me in on start up.  I am the ONLY person who uses this computer.  I don't need any passwords for anything!  But when I check my email - password.  When I install something - password.  When I want to change the screensaver - PASSWORD.  GRRR!  Will someone tell me how to make it stop before I go back to Windows?  BTW please explain it to me like Im reading how to do this in a For Dummies book.  Thanks!

---

### Post by lukeiamyourfather on 2010-06-28
***[COLOR="Red"]Linux is not windows.[/COLOR]*** Passwords are there to protect the system (e.g. your data). The system can automatically log the user into the system, but the other password prompts for installing software and other administrator activities will always require a password.

It takes a little getting used to, but when you use it for a few years and never have any issues with spyware and viruses you'll learn to understand it and appreciate it. Glad you made the first step by installing Linux, stick with it and you'll thank yourself later. Cheers!

---

### Post by lisati on 2010-06-28
Needing a password to check your email has nothing to do with Ubuntu - it is normally a requirement of your email provider. What you *can* do is ask the email software you're using to remember the password for you.

---

### Post by S.R on 2010-06-28
Linux was built along the premise of being a multi-user system.  To that end the OS asking you for your password is a way of protecting you AND saying, "Hey you are getting ready to do something that will affect your system." It also keeps your system more secure and greatly reduces the chances of an unauthorized access. That is one reason microsoft came out with the UAC (User Action Control) box and why so much more of the windows enviroment is compromised.

Once you get your system configured the way you want it you should see fewer of these request. When you work in the terminal using sudo that password entry should be good for 15 minutes (which you can change) and when working from the gui it should be good as long as you are working with that one action.

Email programs can be configured to retain your password. It sounds like your system and email passwords are the. That's bad form there if that is the case. 

If you still want to work toward a password free environment after the "buyer be aware" spiel. Please search here on the forum. There are already several good threads on this topic.

Best of luck

---

### Post by carlexpc on 2010-06-28
A few keystrokes for password prompts is worth the headache of a compromised system. You'll get used to the hassles of typing in your password.

Try to stay with Linux a little longer. Eventually you would realize it's worth the shift from M$ Windows. Cheers!

---

### Post by Windows Nerd on 2010-06-28
Fuuny, I saw a rant in Recurring discussions claiming almost the exact same thing just earlier today.

I have no problem with the system asking me for a password when required-it adds much more security to the OS than Windows could ever dream of having without a absolute rewrite of their OS (which Windows really needs right now in my opinion).

Scott

---

### Post by Paqman on 2010-06-28
> **austellis said:**
> I am the ONLY person who uses this computer.

Actually, you aren't. 

If your computer has a connection to the internet, then millions of people and machines have access to it. That's what the passwords are there for.

---

### Post by endotherm on 2010-06-28
another thing to consider, is that once your system is configured to your needs, you won't have to change much on a system level regularly. really just for updates and installs.

and, you shouldn't need a password to change a screensaver. if you do, somthing is not quite right.

---

### Post by Rubi1200 on 2010-06-28
These links help explain the use of passwords, known as sudo, in Ubuntu:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It is important to try and understand that the security model is there to protect you and your system.

In my opinion, that is a small price to pay for the occasional inconvenience of entering a password.

---

### Post by austellis on 2010-07-04
> **S.R said:**
> Linux was built along the premise of being a multi-user system.  To that end the OS asking you for your password is a way of protecting you AND saying, "Hey you are getting ready to do something that will affect your system." It also keeps your system more secure and greatly reduces the chances of an unauthorized access. That is one reason microsoft came out with the UAC (User Action Control) box and why so much more of the windows enviroment is compromised.

Once you get your system configured the way you want it you should see fewer of these request. When you work in the terminal using sudo that password entry should be good for 15 minutes (which you can change) and when working from the gui it should be good as long as you are working with that one action.

Email programs can be configured to retain your password. It sounds like your system and email passwords are the. That's bad form there if that is the case. 

If you still want to work toward a password free environment after the "buyer be aware" spiel. Please search here on the forum. There are already several good threads on this topic.

Best of luck

I have no idea what the "terminal" is

---

### Post by MooPi on 2010-07-04
Go to your menu /Accessories/Terminal .
Terminal is kinda the hub of what most of us linux geeks use to get things done. It's not necessary but it sure makes things easier when you learn how to use it. I live in a terminal while on my computer and couldn't do half of what I do without it.

---

### Post by Garthhh on 2010-07-04
> **austellis said:**
> I have no idea what the "terminal" is
Terminal is much like the DOS prompt in XP
You will find you can do anything from terminal that you can do using a GUI [graphical user interface], at the cost of being able to find the right code to enter [cut n paste]

you will find that looking in synaptic for what ever software you need will reduce or eliminate your need for "wine".  sometimes you need to search here on the forum 1st to figure out what the package you need is called

---

### Post by prodigy_ on 2010-07-04
> **austellis said:**
> I have no idea what the "terminal" is

As much as it may feel alien to you, I must say that terminal (command line interface shell) makes your life much easier in any flavor of Linux, including Ubuntu. If you know how to use it, of course.

You can open terminal from Applications menu (Applications/Accessories/Terminal). Alternatively, you can press Alt+F2, type "gnome-terminal" in the dialog box that will appear and press Enter.

Note that terminal doesn't suppress password prompts by itself! If you need superuser rights for some action (e.g. to mount a partition or to edit a configuration file in /etc), you'll need to use **sudo** command and you'll still be asked for your password. However, you can open an interactive superuser shell with **sudo -i** command in terminal.

In superuser shell (also called "root shell") you don't need to enter your password anymore. But there's a tradeoff you need to be aware of: one single wrong command from such a shell can theoretically destroy your operating system (or your data!) completely and without warning. Linux isn't Windows. It won't babysit you and protect you from your own mistakes.

So the choice is simple: either play safely and enter passwords or become a command line "hacker" (and inevitably shoot yourself in the foot a couple times while you're learning).

---

### Post by ankit singh on 2010-07-04
U need to get some tutorial for linux. Go to this link  

[http://www.linux.org/lessons/]("http://www.linux.org/lessons/")
:guitar:

---

### Post by ankit singh on 2010-07-04
ubuntu documentation for terminal

[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by Penguin Guy on 2010-07-04
Sorry, but we're not allowed to tell people how to disable passwords on these forums. You could [try googling it]("http://www.google.com/#q=how+to+disable+password+prompts+in+ubuntu") though.

---

### Post by 29732 on 2010-07-04
And there's this very nice book..

You have to buy it though
:-(
Click [HERE]("http://www.amazon.com/Ubuntu-Non-Geeks-Pain-Free-Get-Things-Done-Guide/dp/159327257X/ref=sr_1_6?ie=UTF8&s=books&qid=1278254630&sr=8-6")

---

### Post by 29732 on 2010-07-04
and there's a freebie book 

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

have fun
^.^

---

### Post by The Cog on 2010-07-04
> **austellis said:**
> But when I check my email - password.You should be able to get your email program to remember the password for your email service. Can you tell us which program you use for checking email, and someone should be able to help configure it.
> When I install something - password.
You won't easily be able to remove the password prompt for system configuration, but as others have said, this should become less frequent as you get the system settled. And having given the password once, you don't need it again for 15 minutes. 
> When I want to change the screensaver - PASSWORD.
That shouldn't happen. When I use System->Preferences->Screensaver, I don't have to give a password. Personal settings shouldn't need your password again. How are you trying to change the screensaver?

---

### Post by rburkartjo on 2010-07-04
it is a good thing not to disable the password prompt. yes it can be a p.i.t.a but it makes you think twice before doing something and that can be a good thing. i used a non pass word system for a while however you can really mess your system up. as i did. just my 2cents but if you really want to disable all passwords prompt do as mentioned before a google search. the terms of this board prevent users from giving out links and that is good imoo

---

### Post by RJ12 on 2010-07-04
Also, when you use the "sudo" command and it asks you for the password, it is being inputed, just you don't see any feedback. Some call this a feature and some call it a bug. Most password prompts in Terminal do not give you any feedback that you are typing a password (like with Asterisks ***)

---

