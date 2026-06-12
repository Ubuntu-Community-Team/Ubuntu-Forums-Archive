---
title: "Postfix and php"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Richard1953 on 2011-04-27
Hello,
I have a setup with a lamp stack. I've installed postfix ok. (I think).I can send mail from the command line BUT only as SUDO. If I try to send mail either as a normal user or via apache/php the postfix log says it won't do it as "only superuser can send mail" (I may be paraphrasing, but that's the essence). I think I have missed out a step in configuring either postfix or php:confused:, but despite doing a lot of googling I can't see the solution. Any advice gladly accepted. Thanks:biggrin:

---

### Post by Richard1953 on 2011-04-28
Sorry to bump this but.... anyone?, Please!

---

### Post by paulm23 on 2011-04-28
Can't say I've ever seen this, sounds policy driven.  Can you give me the version of Ubuntu/Kubuntu you are using and what command you used to generate the error message.

---

### Post by indytim on 2011-04-28
For the php end, suggest that you check your permissions on /var/www.  Both the owner and the group should be aligned to your login id if you are using your LAMP strictly for development.

IndyTim / DataMan

---

### Post by Richard1953 on 2011-04-28
Thanks for your interest.:)
I'm using Hardy (8.04) and any postfix command you like; postfix status,postfix check, you name it!
Unless this is normal?
The actual REAL problem is I am trying out a contact form in a web page - this goes of to a bit of php code that essentially gets the name of the visitor, the email address and message wraps it all up and then sends it via the php mail() command to postfix.
The postfix log says that I (the visitor)  has tried to send a mail but they don't have permission. (only root can do this)!!:confused:

If I use the telnet .... command on the terminal it works- sorry I can't remember if I used sudo or not.

I hope this helps - I don't have access to the pc atm so can't send any copies of configs etc. so the above is from memory.

---

### Post by Richard1953 on 2011-04-28
@indytim,
Can you expand on that?
Apache is open to the world, as you'd expect(?) on port 80 and (I think) that /var/www is owned by apache  (and root) only is this wrong?

---

### Post by paulm23 on 2011-04-28
When you're able to get to your machine can you copy and paste the line with the error. I need to know which part of postfix is giving the error.  And main.cf if that is acceptable.

---

### Post by indytim on 2011-04-28
Beyond the error message requested above, you might want to swing over to the Servers board and post up there.  You should find some hard core postflix people haunting about there.

I've never used postflix so I have no first hand knowledge to provide meaningful solutions for you.  The checkout that I offered is Apache 101 with respect to permissions etc.

Stay tune here also as more direct support may be coming from other members.

Good Luck,

IndyTim / DataMan

---

### Post by Richard1953 on 2011-05-13
[SIZE=2]**Solved**[/SIZE]
Hi Guys,
Thanks for all the help -I fixed it... It was due to my complete stupidity and ignorance!!!
The send mail command in postfix main.cf was wrong should have been sendmail -t -i and I had set it to something like /etc/sbin/postfix ----:oops::oops:  Sorry , what a dummy!!!

---

