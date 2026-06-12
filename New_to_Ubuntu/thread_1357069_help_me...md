---
title: "help me.."
date: 2009-12-16
forum: New to Ubuntu
---

### Post by 0863963 on 2009-12-16
[SIZE=3]Hi Everyone I have a simple questions:[/SIZE]
 
[SIZE=3]1 - How can I create another account?? [/SIZE][SIZE=3]Means the user account.[/SIZE]
 
[SIZE=3]2 - How do I add programs?[/SIZE]
 
[SIZE=3]3 - How do I change the system clock from 24 to 12 ..?[/SIZE]
 
 
[SIZE=3]Thank you very much...[/SIZE]

---

### Post by ubudog on 2009-12-16
> **0863963 said:**
> [SIZE=3]Hi Everyone I have a simple questions:[/SIZE]
 
[SIZE=3]1 - How can I create another account?? [/SIZE][SIZE=3]Means the user account.[/SIZE]
 
[SIZE=3]2 - How do I add programs?[/SIZE]
 
[SIZE=3]3 - How do I change the system clock from 24 to 12 ..?[/SIZE]
 
 
[SIZE=3]Thank you very much...[/SIZE]

To create another account, go to System, Administration, Users and Groups.  Then click on the icon that says "Click to make changes" Enter your password and press enter.  Then click on the "Add user" button at the top of the screen.  Enter the user details.

To add programs, go to Applications, Ubuntu Software Center.  Lots of useful programs there for new ubuntu users.

To change the clock from 24 to 12, go right click the time on the top right corner, click Preferences, then click the bubble with "12 hour format" on the side of it.  

Hope that helps :)

---

### Post by baddog144 on 2009-12-16
To add another account, go to System -> Administration -> Users and Groups, click Unlock, then click Add User

To add programs, use the Add/Remove programs program, located in Applications -> Add/Remove...

I'm sorry to say I don't know how to change the clock from 24-hour time to 12-hour time though :(

EDIT: Beaten! :P

---

### Post by ubudog on 2009-12-16
For beginners, I would recommend you take a look around [http://system76.com/index.php]("http://system76.com/index.php")  Lots of useful stuff there.

---

### Post by 0863963 on 2009-12-17
[SIZE=4]Thank you very much...[/SIZE]

---

### Post by chuina on 2009-12-17
> **baddog144 said:**
> To add another account, go to System -> Administration -> Users and Groups, click Unlock, then click Add User

To add programs, use the Add/Remove programs program, located in Applications -> Add/Remove...

I'm sorry to say I don't know how to change the clock from 24-hour time to 12-hour time though :(

EDIT: Beaten! :P

why the edit beaten ?
i can use both 12/24 format by giving password and simply editing !!!:)

---

### Post by northern lights on 2009-12-17
> **chuina said:**
> why the edit beaten ?
cause the second poster was faster than the third...

@the OP: It is advisable to use a descriptive topic title. Threads with titles such as "Need assistance", "Please help", "A problem" or "Few questions" will inevitably get less people to read your post. It will further make people read it that have no knowledge on the topic and saved time by skipping it if they had been informed what it's about by the title. So please, refrain from generic titles. Imagine every thread was titled like that...

---

### Post by 0863963 on 2009-12-18
> **baddog144 said:**
> To add another account, go to System -> Administration -> Users and Groups, click Unlock, then click Add User
 
To add programs, use the Add/Remove programs program, located in Applications -> Add/Remove...
 
I'm sorry to say I don't know how to change the clock from 24-hour time to 12-hour time though :(
 
EDIT: Beaten! :P
 
 

** How do I add a program from Flash Memory? Eg Messenger..**
 
**Is ubuntu system accepts all programs xp Windows** **??**

---

### Post by chuina on 2009-12-18
using windows program is a technical issue.
it varies by machine to machine.
u have to install wine first.

to install wine,
1.by command,
open a terminal from Applications>Accessories>Terminal and type

```
sudo apt-get update
sudo apt-get install wine
```or, 
2.by browsing (firefox)
go to this web: 
[http://appnr.com/](http://appnr.com/) 

for more help related wine, go to this link:

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)


[There are many types of softs provided by the Ubuntu community. 
you can use them from **Applications>Ubuntu Software Center**...]

---

### Post by ukripper on 2009-12-18
Ubuntu Guide - [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

---

### Post by northern lights on 2009-12-18
> **0863963 said:**
> ** How do I add a program from Flash Memory? Eg Messenger..**
 
**Is ubuntu system accepts all programs xp Windows** **??**
Ubuntu is a Linux operating system. It is not a Windows clone (Thank goodness).

It's API and binary execution mechanisms are fundamentally different. Natively, a Linux OS cannot run .exe files - the binaries you so far have come across.

As chuina has correctly pointed out, there are ways to run Windows applications. This however should be the odd unreplaceable program and not the regular practice.

As for your messenger, for instance, Ubuntu comes with *Pidgin* pre-installed. It's a multi-protocol messenger app that supports MSN, Yahoo Chat, Google Talk, ICQ, IRC and some other protocols. If you're familiar with Trillian under Windows, that's comparable.

You will have to find (which is not too hard) equivalent apps to replace what you're currently using.

---

### Post by sailor2001 on 2009-12-18
Can't find the program you want? Try system/admin/synaptics..1st time there click settings/repositories to make sure everything has been checked. Also click 3rd party to see if anything that maybe there is ticked.

---

### Post by Mornedhel on 2009-12-18
> **northern lights said:**
> As for your messenger, for instance, Ubuntu comes with *Pidgin* pre-installed. It's a multi-protocol messenger app that supports MSN, Yahoo Chat, Google Talk, ICQ, IRC and some other protocols. If you're familiar with Trillian under Windows, that's comparable.

(Pedantic mode) I would like to point that on the most recent Ubuntu releases, Pidgin is no longer the default IM app, and has been replaced by Empathy as the Gnome project's IM app of choice. The goal is to have better integration with the desktop environment through the superior Telepathy framework (superior in architecture; protocol support is lagging behind Pidgin in several areas, but catching up).

Pidgin is still in the repositories and can be installed very easily.

Be advised that MSN and Yahoo support in Linux still does not have all the features implemented (audio/video for instance).

---

### Post by northern lights on 2009-12-18
> **Mornedhel said:**
> (Pedantic mode) I would like to point that on the most recent Ubuntu releases, Pidgin is no longer the default IM app, and has been replaced by Empathy as the Gnome project's IM app of choice. The goal is to have better integration with the desktop environment through the superior Telepathy framework (superior in architecture; protocol support is lagging behind Pidgin in several areas, but catching up).
Unaware. Still happily running a stable Jaunty. Won't upgrade till Lucid in April. Thanks for clarifying.
Better a pedant than sloppy.

---

### Post by ubudog on 2009-12-18
> **ukripper said:**
> Ubuntu Guide - [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Yeah, good site.  Used it when I was a noob.

---

### Post by 0863963 on 2009-12-18
[SIZE=4]Thank you very much for the clarification ..[/SIZE]

---

### Post by joes7 on 2009-12-18
Add programs
```

Applications->Add/Remove..

```

---

### Post by joes7 on 2009-12-18
> **ubudog said:**
> Yeah, good site.  Used it when I was a noob.
Me too :)!

---

### Post by ukripper on 2009-12-21
> **ubudog said:**
> Yeah, good site.  Used it when I was a noob.

I use it as one of my reference point.

---

### Post by joun on 2009-12-25
Good questions :) thank you
[FONT=MS Shell Dlg][SIZE=2][FONT=MS Shell Dlg][SIZE=2] 
[/SIZE][/FONT][/SIZE][/FONT]

---

