---
title: "What is /var/mail/root  ???"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by electropsy on 2010-02-28
[I]HI.

  I am new to ubuntu , and when i am installing something i get a [/I]message: You have mail in /var/mail/root   , but i dont now what it is .
 
 Can someoneexplain me what significance that log have ?


**Thanks**.

---

### Post by Barriehie on 2010-02-28
The system has sent an email to *root*.

---

### Post by Paddy Landau on 2010-02-28
Open a terminal (from your menu, Accessories > Terminal).


[LIST=1]
[*]Type the word *mail* and press Enter.
[*]You'll see a list of messages (or maybe just one message).
[*]Enter the number of the message that you want to read, e.g. press *1* and Enter.
[*]Press 'd' to delete the message.
[*]Repeat steps 3-4 until you've deleted all the messages.
[*]Type *quit* and press Enter.
[/LIST]
A bit messy, but that's how email used to work before GUI environments.

---

### Post by Paddy Landau on 2010-02-28
I forgot that the mail was from root.

Type *sudo mail* instead of just *mail* and press Enter.

---

### Post by spikyjt on 2010-02-28
Just to dig a bit deeper: When you install software you do it as the administrator, or "root" user in unix terms. You achieve this on Ubuntu by running the install command as root, using sudo. All the messages fed back from the installation are given to the root user, whose login you have temporarily assumed, hence the notification that the root user has new mail. Although you may not use your local mail system, accessing internet mail via a client such as Evolution, Thunderbird or KMail, your system services can send mail messages internally. Some of them have done so and they would send their mail to the root user by default. You can read them by typing ```
sudo mail
``` at the command line. You will then get a very basic command line mail reader. You'll probably find it will be a warning message from some system service, possibly one that is not configured yet. If you want to read this mail regularly, your best bet could be to set up sSMTP, to forward the mail to an internet mail server, or set up a script to move the root mailbox to your user account, and add your local mailbox to your MUA.

EDIT: someone else above is much more succinct than me, and quicker at typing!

---

