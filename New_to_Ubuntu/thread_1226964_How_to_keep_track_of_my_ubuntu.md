---
title: "How to keep track of my ubuntu?"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by bobigeorge on 2009-07-30
Dear friends,

I have installed ubuntu 9.04 on my HP laptop. My room mates know the password and they usually use my laptop.

I wanted to know if there is a way to **know which files they have accessed what changes they have made to my system settings etc...**

Please suggest me a solution... because my friends usually try around with ubuntu a lot and alter many settings..

Thanks in advance...

---

### Post by RomeReactor on 2009-07-30
Hi. If you're worried about your friends changing anything in your system, you could change your password and let them use a guest account.

---

### Post by presence1960 on 2009-07-30
change your password and create unpriviledged accounts for them.

---

### Post by DanFoxDavies on 2009-07-30
What they said ^

---

### Post by beren.olvar on 2009-07-30
If you still want to see what has been modified you can try writting in a terminal:

find / -mtime n

this will show you the files modified since n days ago (actually rounded down, so if you want the files modified in the las 24hours n=1, two days ago n=1, etc...)

of course this will show you A LOT of output, and not only related to your friends activities.

---

### Post by twright on 2009-07-30
One technical solution you could use (if you have a geeky side) is to create a one partition onto which you do a clean install of Ubuntu and then another empty one, mount them together using unionfs (google for a howto) then any files changed will be on a separate partition and can instantly be reverted. Either that or make sure they have separate user accounts and look in the sudo logs for anything system wide they do.

---

### Post by llamabr on 2009-07-30
> **RomeReactor said:**
> Hi. If you're worried about your friends changing anything in your system, you could change your password and let them use a guest account.

Not a guest account, but rather an account of their own.  The linux security system is completely undermined by giving access to your account, or sharing your password.  The system of ownernship and permissions works exactly because everyone uses their own account.

Otherwise, you'll ultimately be chasing your own tail, as you try to see what they did, and they try to subvert you using those same tools.

---

### Post by naveedmanzoor21 on 2009-07-30
I think this would help you

Go and unlock your your root account and create an password for root  . By this your friends cannot do any modifications as they don't know the root password

Follow this go to System > Administration > User and Groups and click on root account and click unlock button and goto Properties and change the password by clicking change password by hand.

---

### Post by LowSky on 2009-07-30
> **naveedmanzoor21 said:**
> I think this would help you

Go and unlock your your root account and create an password for root  . By this your friends cannot do any modifications as they don't know the root password



Dumbest idea, as his account still has Sudo privlages it wouldn't matter if root is enabled.


Best option is to set up an account for them with no sudo access. the less they can do the better

---

### Post by twright on 2009-07-30
> **LowSky said:**
> Dumbest idea, as his account still has Sudo privlages it wouldn't matter if root is enabled.
If the root password is not set they can bypass any other ones at bootup. This is a stupid default although admittedly it has saved many people I know :-) .

---

### Post by naveedmanzoor21 on 2009-07-30
> **LowSky said:**
> Dumbest idea, as his account still has Sudo privlages it wouldn't matter if root is enabled.


Best option is to set up an account for them with no sudo access. the less they can do the better
All you need do at the same time is uncheck the  Administer the system option for other users in User Privillages Tab  of Propeties of the User Account other than root.

---

### Post by bobigeorge on 2009-07-30
Thank you all for valuable suggestions...

But I was looking sor something like a EVENT LOG... any idea??

---

### Post by llamabr on 2009-07-30
[http://www.linuxforums.org/forum/linux-security/109864-auditing-logging-all-commands-arguments.html](http://www.linuxforums.org/forum/linux-security/109864-auditing-logging-all-commands-arguments.html)

Sure, there are things like this, but they're just as easy to subvert as they are to implement.

Plus they're a bit rude.  Just set up an account for your friends, rather than spying on them.

---

### Post by bodhi.zazen on 2009-07-31
> **bobigeorge said:**
> Thank you all for valuable suggestions...

But I was looking sor something like a EVENT LOG... any idea??

You could set up something such as tripwire or ossec. Search on Linux HIDS (HIDS = Host Intrusion Detection System). HIDS monitors your files for changes.

But really the easiest thing to do is set each user with an unprivilaged account and make our home directory private (chmod 700 $HOME). Linux permissions will take care of the rest.

---

### Post by bobigeorge on 2009-08-06
Thank you friends...

I have decided to settle down with account management..

---

