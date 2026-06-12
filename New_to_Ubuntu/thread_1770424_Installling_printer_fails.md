---
title: "Installling printer fails"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Jos.vh on 2011-05-29
Hi.

I'm using Ubuntu 10.10 and I'm trying to install a Lexmark S305.
I followed the instructions on the Lexmark website. When I starting to install, the system asks me for an administrator password to continue. Then I receive the message that the password is incorrect.....????
The password works fine when I install other programs or when I login as administrator. I even tried to install the driver while being logged in as administrator, but it keeps telling me that I'm using the wrong password.

Any ideas?

Thanks in advance,

Jos

---

### Post by Jos.vh on 2011-05-29
Hi. I just read mkornig's solution to a similar problem. 

> **mkornig said:**
> Thanks for your help and coments, everybody!

I've actually installed the printer by doing the following:

[LIST=1]
[*]connect as a user with root/admin privileges
[*]open a terminal
[*]go the directory in which the driver installation file *sh is located
[*]submit the command: *sudo ./*sh*
[/LIST]
*...*and then, big surprise, the driver wizzard didn't ask for the root password any more.

Lexmark printer prints fine now.




His solution works!!!
Best regards,

Jos

---

### Post by Ray Ratliff on 2011-06-01
> **Jos.vh said:**
> Hi. I just read mkornig's solution to a similar problem. 






His solution works!!!
Best regards,

Jos

I am new to this.  first how do u connect as a user with root/admin privileges and after u open terminal how do u go to a directory where the 
driver file  *sh is.(how do u know where it is?)
By submitting a command, how is that performed? 
Thanks....

---

### Post by mkornig on 2011-06-03
> **Ray Ratliff said:**
> I am new to this.  first how do u connect as a user with root/admin privileges

If you are the only user on your system then you should have admin privileges. Just login as usual.
You may also want to check out the users on the system and their privileges: System > Admin > Users and groups

> **Ray Ratliff said:**
> how do u go  to a directory where the 
driver file  *sh is.(how do u know where it is?)

Assuming that you have downloaded the file recently, it probably is in a directory called "Downloads". If you don't specify anything else, this is where downloaded files are kept.

You can use the command "find" to check where a file is.

Other useful commands you may want to use are: "pwd", "ls" and "cd". You can display further information about a given command (for instance the list of options) with the "man" command. Example: in order to find out about the command "pwd" you type "man pwd" and then press enter.

> **Ray Ratliff said:**
> 
 By submitting a command, how is that performed? 
 
 
Open a terminal, type the command and press enter.

I hope all this makes sense to you and helps? I know that using Unix commands in a terminal is not easy for a beginner. You may want check out a tutorial first (try wikipedia ?).

---

