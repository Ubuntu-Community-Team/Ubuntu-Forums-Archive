---
title: "Startup  Application runs twice"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by jimwims on 2011-02-18
I am running 10.10 on a remotely located computer.  I want the computer to send a text message to my phone when the computer starts up. I am using sendEmail to do this.  It is a command line driven e-mail client.  When I run it with the necessary command line in terminal it works just fine.  I have included the command line as the command of a startup program in Startup Applications.  It works fine except for one problem.  I receive the text message twice each time the computer starts up,  I have tried using different e-mail services (Gmail and Earthlink) and a normal e-mail address as well as my sms address, but with the same result.  It is as though the command is executing twice on every start-up.  A minor problem, but annoying.

Any suggestions of how I can get rid of the second message?

---

### Post by grahammechanical on 2011-02-18
Is there a way of putting a time delay in the script of your special startup program. Perhaps the program is sending the message before the network connection is properly established. It gets a not ready signal and sends a second time but both attempts get through. A time delay to allow the OS to fully load before your special program runs might fix it. Don't ask me how to do it.

Regards.

---

### Post by jimwims on 2011-02-19
Well, after a little research, it turns out there is an easy way to add a time delay.  You merely run the program from a script, but insert "sleep xx" in a line preceding the line that calls the program, where "xx" is the delay in seconds.  I arbitrarily chose 20 seconds.

However, all that did was to delay both messages by 20 seconds.

Thanks for trying.  At least I learned something about scripts.

---

