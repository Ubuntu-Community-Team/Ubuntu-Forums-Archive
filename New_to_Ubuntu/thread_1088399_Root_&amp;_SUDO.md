---
title: "Root &amp; SUDO"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by mbele3000 on 2009-03-06
Okay I am running Ubuntu 8.10 and checkgmail was working fine until a day or so ago. While it was working fine it would start up from the Main menu> Internet> checkGmail and it would start fine. Then for some reason it just stopped working and I would start it in terminal and I was getting error messages. Well in terminal using Sudo it starts OK or using Root and typing checkGmail it works. But the second I close the terminal/root window checkGmail stops. How so I get it to work again, do I need to edit scripts to accomplish this?

   "Cooperation is the fundamental basis of success" - unknown

---

### Post by Kareeser on 2009-03-06
You shouldn't need to run CheckGMail using sudo.

Can you type the error messages into a reply for us to see?

---

### Post by anim on 2009-03-06
Kareeser is correct, you shouldn't have to run checkGmail with elevated permissions. You could always try uninstall/reinstall to see if that helps

But to answer your question, you should be able to make the process run in the background by adding the "&" sign after the program name so:

```
~$ sudo checkgmail &
```

---

### Post by mbele3000 on 2009-03-06
this is the error message when I run it in terminal without sudo:

File does not exist:  at /usr/bin/checkgmail line 1251
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached

 Running $ sudo checkgmail & the error message im getting is

[4] 29167

[3]+  Stopped                 sudo checkgmail

What is happening LOL!

  Im just trying to get it to run "normal" from the applications menu without having to go to terminal to get it to run. I get ya that the 
 "sudo checkgmail &" usually will get it to run after I close the terminal window but not this time I guess!?

---

### Post by Majiq on 2009-03-06
The problem is the sudo is getting backgrounded. Use gksudo, instead of sudo. It's the graphical counterpart.

Edit:
In case I wasn't clear, do:
```

gksudo checkgmail &

```

Edit2:
Also, make sure you exit the terminal using the exit command, and not via the "x" in the cordner. Using that button will result in it killing the children processes regardless.

---

### Post by mbele3000 on 2009-03-06
Thank you but how do I get this to run without opening terminal, and get the app to run from the application menu? I know that checkGmail is not a official repo. so if you can point me in the direction to "fix it" that would be great! Thanks allot for all the help so far BTW!  


   "Don't be to poor to pay attention" - unknown 
            (although I'd like to credit my gramps with that one)

---

