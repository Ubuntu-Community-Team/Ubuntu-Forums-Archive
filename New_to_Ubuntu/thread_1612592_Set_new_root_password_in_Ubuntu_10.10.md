---
title: "Set new root password in Ubuntu 10.10"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by olddai on 2010-11-03
Whenever i boot up my computer i use my password and that's fine. But when i tried to become root i typed in my password and i got back 'Authentication failure'?

Could someone please tell me what's going on here and what i can do to set a new root password. I am the only user of the computer. Thanks

---

### Post by kaldor on 2010-11-03
Try doing "sudo su". Once logged in, use the "passwd" command and follow the basic steps it asks. 

I think that should do it, but it has been a long while.

---

### Post by Hippytaff on 2010-11-03
You can set a new password with
 
```

sudo passwd

```
in the terminal - open a terminal with CTRL+ALT+T

---

### Post by hot_rod_hippie on 2010-11-03
There is pretty much no need to become root in Ubuntu. Instead of using [FONT="Courier New"]su[/FONT], preface all adminstrator level commands with [FONT="Courier New"]sudo[/FONT] and you'll be prompted for your password. Admin tasks from the GUI will ask for rights, just enter your regular password there, too.

Hippie

---

### Post by oldfred on 2010-11-03
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Forum policy on log-in-as-root tutorials
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by coffeecat on 2010-11-03
> **Hippytaff said:**
> ...

@Hippytaff, have you read the three links that oldfred has posted?

---

### Post by Hippytaff on 2010-11-03
> **coffeecat said:**
> @Hippytaff, have you read the three links that oldfred has posted?
 
Point taken, but I didn't advise the op to sudo su, or stay logged in as root, or become root user or disabling root password, I just answered the question about how to change the password.
 
Does that contravene the forum policy? :-s

---

### Post by olddai on 2010-11-03
Aye aye Hippytaff i used sudo passwd and all went well. Thanks for all the replies everyone!

---

### Post by Hippytaff on 2010-11-03
Dim problem
 
Remeber to mark the thread as solved :-)

---

### Post by coffeecat on 2010-11-03
> **Hippytaff said:**
> Does that contravene the forum policy? :-s

As far as I understand, not quite. Certainly, showing someone how to login as root into a GUI is likely to result in jailed posts and infractions. Telling them how to enable a root password is not as heinous :p but I believe is a disservice to newbies. The Rootsudo link describes the Ubuntu security model which is more than adequate for home desktop use. Subverting that model by enabling the root account muddles the issue for support threads. If someone wants a root terminal, all they need to do is to 'sudo -i' or 'sudo su' as described in the Rootsudo wiki link. You don't need a root password for that.

The wiki link does indeed give the 'sudo passwd' tip, but adds:

> **[SIZE=4]Use at your own risk![/SIZE]**[B]
:wink:
[/B]

---

### Post by PicklePumpers on 2010-11-22
> **Hippytaff said:**
> Point taken, but I didn't advise the op to sudo su, or stay logged in as root, or become root user or disabling root password, I just answered the question about how to change the password.
 
Does that contravene the forum policy? :-s

You did great Hippytaff, thank you!

I **really** hate when people refuse to answer a question and instead send you off to read FAQ's; it's annoying, arrogant, and rude. If they are unable or unwilling to answer then they should remain quite. It annoys me so much I wrote a blog post on [how to answer a question]("http://picklepumpers.com/wordpress/?p=673").

Basically: Answer the question then explain why you think it's a bad idea. If you don't answer the question first people will just ignore you.

Thanks again Hippytaff for answering the question and not just flippantly posting links to FAQ's as if you were the arbitrator of knowledge on the Internet.

---

### Post by PicklePumpers on 2010-11-22
> **coffeecat said:**
> As far as I understand, not quite. Certainly, showing someone how to login as root into a GUI is likely to result in jailed posts and infractions.

If that is so then the board admins need some serious talking to. Telling people how to use the OS is what this forum is supposed to be about. The very fact that you would say this is not only shocking but defies reason.

---

### Post by lisati on 2010-11-22
We seem to be sidetracked here by a discussion of the merits of logging in as root and the kind of assistance in this area that is appropriate in the forum. If I understand the OP correctly, the original question was about "authentication failure"....... (And don't forget that this thread was posted in the "Absolute beginner" section.)

---

### Post by Joeb454 on 2010-11-22
> **PicklePumpers said:**
> If that is so then the board admins need some serious talking to. Telling people how to use the OS is what this forum is supposed to be about. The very fact that you would say this is not only shocking but defies reason.

Please see [this thread]("http://ubuntuforums.org/showthread.php?t=1486138") for our policy on root logins.

In general, most of the users to this forum are new users, and running your entire session as root can have some undesired consequences, especially if you're new to the entire OS.

---

### Post by madcitynative on 2010-12-09
Well, I thought I was going to like Ubuntu.......

I just spent 3 hours trying to change the root password. It will not change.

I've done everything mentioned in this thread. 

None of it works.

At times the password acts as if it is blank but when I try to change the password "blank" does not work.

I opened up the command line and it says it successfully changed the password but it has not. I've rebooted and the new password still will not work.

No sense in putting passwords on accounts if anyone can open the ubuntu account with no password and change all the account info on my other accounts. 

Please someone...just a simple answer regarding this.

---

### Post by ezsit on 2010-12-09
At a terminal prompt, type:

**sudo passwd root**

You will be asked to type your user password and then type a password for root, then retype the password for root. 

You will not see any typed feedback on the screen, so be careful, press the Enter key after each password input. 

At the end you should get the message that root's password was updated successfully.

This process has worked for me on every version of Ubuntu from 5.04 through 10.10 without issue.

This procedure will not enable root logins, only enable you to use "su" in addition to sudo at the command prompt. If you do enable root logins, do so after you have changed the root password so you can then login as root. Also, don't enable root logins, ;-)

---

### Post by anewguy on 2010-12-10
> **PicklePumpers said:**
> You did great Hippytaff, thank you!

I **really** hate when people refuse to answer a question and instead send you off to read FAQ's; it's annoying, arrogant, and rude. If they are unable or unwilling to answer then they should remain quite. It annoys me so much I wrote a blog post on [how to answer a question]("http://picklepumpers.com/wordpress/?p=673").

Basically: Answer the question then explain why you think it's a bad idea. If you don't answer the question first people will just ignore you.

Thanks again Hippytaff for answering the question and not just flippantly posting links to FAQ's as if you were the arbitrator of knowledge on the Internet.

However, there are VERY specific forum rules in place for this and other items, and pointing out that it should not/can not be answered on the forum IS needed.  Nobody is saying don't discuss the information - they're just saying don't discuss it in the forum.  Use another medium - email, etc., but not the forum.  That seems to me to be simpe request - it's not restricting anyones rights or freedoms - just saying excersise them in a different place from the forum.

Things like root are there for people's protection - especially the absolute beginner as the forum is aimed to.  There are other topics that can be of questionable legality, and whether you choose to believe so or not, should not be posted here either.  They can actually result in legal action against the owners of the forum.

So people are really saying - use common sense, not emotion.

Dave

---

