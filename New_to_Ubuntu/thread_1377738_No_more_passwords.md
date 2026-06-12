---
title: "No more passwords"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by jermza on 2010-01-10
Well, not completely.  But I'm the only one using my PC.  Surely, I don't have to be asked for a password every time I open, say, Empathy?

I have to enter a password for just about anything I do.  Is there a way I can remove the prompts?  It gets a bit annoying...

---

### Post by nothingspecial on 2010-01-10
> **jermza said:**
> I have to enter a password for just about anything I do.  Is there a way I can remove the prompts?

Yes, but then your computer would be vulnerable and you will almost definitely break it.

Trust me, stick with the password.

---

### Post by jermza on 2010-01-10
> **nothingspecial said:**
> Yes, but then your computer would be vulnerable and you will almost definitely break it.

Trust me, stick with the password.
Thank you, but I'm not asking for a nanny.  

Again, is there a way to regulate the amount of times I have to enter my password?  (If I want the password option back, I'll at least know where to find it.)

---

### Post by marco123 on 2010-01-10
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by nothingspecial on 2010-01-10
I am not allowed to tell you.

See [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

and [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=716201")

In a nutshell - if you know how to disable the password you don`t need to ask; if you don`t know how, you probably shouldn`t.

Don`t take this the wrong way, it`s just the Ubuntu way :D

---

### Post by Enigmapond on 2010-01-10
> **jermza said:**
> Thank you, but I'm not asking for a nanny.  

Again, is there a way to regulate the amount of times I have to enter my password?  (If I want the password option back, I'll at least know where to find it.)

Wow...that was pretty harsh. He wasn't offering to be your nanny...to eliminate the passwords not only makes it easier for YOU to make a mistake,,,believe it or not but it DOES happen, but it also opens your computer up to be more vulnerable and not just from people in the room but people that you connect to....as the tutorial will tell you. Again, he was only giving sound advise.....

---

### Post by oldos2er on 2010-01-10
> **jermza said:**
> Again, is there a way to regulate the amount of times I have to enter my password?  (If I want the password option back, I'll at least know where to find it.)

You can tweak /etc/sudoers to, for example, increase the time period the system remembers your password.

Or open an admin session with **sudo -i**, which you can keep open as long as you like.

---

### Post by jermza on 2010-01-10
> **nothingspecial said:**
> I am not allowed to tell you.

See [[COLOR=Magenta]here[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

and [[COLOR=Magenta]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=716201")

In a nutshell - if you know how to disable the password you don`t need to ask; if you don`t know how, you probably shouldn`t.

Don`t take this the wrong way, it`s just the Ubuntu way :D

Then the "Ubuntu way" is somewhat snotty and elitist.  Good god, it's not like I'm asking for much; I'm not exactly attempting to hack into my own computer.  

I simply don't want to type in a password when I open my instant messenger.

---

### Post by nothingspecial on 2010-01-10
Then go and install a system that gives you root access by default.

Like I said, that is not the Ubuntu way.

If you are happy, to be vulnerable, then go ahead. You can even ask on these forums for help to fix what ever mess you get yourself into.

But, no one is allowed to tell you so ask elsewhere.

---

### Post by Vaphell on 2010-01-10
you've heard that it's the official policy on ubuntuforums. It would be too tempting for any fresh ex-windows convert to do things windows (unsafe) way - users on admin accounts is the main factor of the malware problem plaguing the windows world.

You are free to ask google though, there will be plenty of information.

---

### Post by nothingspecial on 2010-01-10
Oh, and take note of my sig ...... not the bit about the washing machine ;)

---

### Post by jermza on 2010-01-10
Okay, so if I set, say, Empathy as a startup application, will it still request a password when Ubuntu boots up?

Essentially, having the IM automatically starting is optimal.

---

### Post by running_rabbit07 on 2010-01-10
> **oldos2er said:**
> you can tweak /etc/sudoers to, for example, increase the time period the system remembers your password.

Or open an admin session with **sudo -i**, which you can keep open as long as you like.

+1

---

### Post by nothingspecial on 2010-01-10
> **jermza said:**
> Okay, so if I set, say, Empathy as a startup application, will it still request a password when Ubuntu boots up?

Essentially, having the IM automatically starting is optimal.

I have no idea because I don`t use it.

What I`m trying to say, is get used to typing your password.

That`s why you don`t have to pay for anti-virus etc :D

I must type my password 50 times a day, but then I have a lightening fast, virus immune system.

What do you want?

---

### Post by running_rabbit07 on 2010-01-10
Where's that Linux isn't Windows link?

---

### Post by jermza on 2010-01-10
> **nothingspecial said:**
> I have no idea because I don`t use it.

What I`m trying to say, is get used to typing your password.

That`s why you don`t have to pay for anti-virus etc :D

I must type my password 50 times a day, but then I have a lightening fast, virus immune system.

What do you want?
Yes, I get it.  Passwords, like, totally rock, dude.  On Apple, there are lots of passwords too.  And Apple is also pretty secure.

I just didn't realise that something as mundane as an IM is a matter of national security.  Just to see what happens, I'll type in my password and then enter "bomb the White House" a few times.  Maybe Big Brother will come after me.

That aside, to clarify, to chat via IM to my friends, I have to type in my password: is this correct?  Also, what is a "key ring"?

---

### Post by running_rabbit07 on 2010-01-10
> **jermza said:**
> Yes, I get it.  Passwords, like, totally rock, dude.  On Apple, there are lots of passwords too.  And Apple is also pretty secure.

I just didn't realise that something as mundane as an IM is a matter of national security.  Just to see what happens, I'll type in my password and then enter "bomb the White House" a few times.  Maybe Big Brother will come after me.

That aside, to clarify, to chat via IM to my friends, I have to type in my password: is this correct?  Also, what is a "key ring"?

Dump Empathy for Pidgin and that problem will go away.

---

### Post by jermza on 2010-01-10
I see that Ubuntu prompts for the password when it boots up, if I've Empathy running as a startup application.

---

### Post by running_rabbit07 on 2010-01-10
I use pidgin instead, it doesn't ask for any passwords. Having to use a password for that is ridiculous, I agree. You can easily remove it from the startup applications list.

---

### Post by running_rabbit07 on 2010-01-10
AppArmor, once properly set for the application, idiot proofs the PC.

---

### Post by blackened on 2010-01-10
> **jermza said:**
> Yes, I get it.  Passwords, like, totally rock, dude.  On Apple, there are lots of passwords too.  And Apple is also pretty secure.

I just didn't realise that something as mundane as an IM is a matter of national security.  Just to see what happens, I'll type in my password and then enter "bomb the White House" a few times.  Maybe Big Brother will come after me.

That aside, to clarify, to chat via IM to my friends, I have to type in my password: is this correct?  Also, what is a "key ring"?

I think this thread has gotten quite a ways off track. I think the OP's intent was more to get rid of having to enter a password when starting Empathy as opposed to removing them system-wide. 

Like others here, I don't use Empathy, but I did set up a google talk account just for the sake of testing. As far as I can tell, the password behavior that you're experiencing is not normal: empathy never prompted me for any passwords after initial account setup. You may think about filing a bug over on launchpad.

I can't explain why it's acting this way, have you tried completely removing empathy via synaptic and reinstalling it? Not sure if it's linked to the ubuntu-desktop meta-package or not. It's worth a shot though.

---

### Post by Joeb454 on 2010-01-10
I imagine the password it asks for is to unlock your keyring (it will tell you)

Do you have the PC set to auto-log you in?

---

### Post by nothingspecial on 2010-01-10
I appologise if you saw my unedited previous post.

Linux is secure for a reason.

It is one of linuxes great advantages.

Yes, it may seem silly to have to type a password in to launch an instant messenger.

But that`s the way it is. Like the rabbit said, use pidgin.

---

### Post by jermza on 2010-01-10
> **Joeb454 said:**
> I imagine the password it asks for is to unlock your keyring (it will tell you)

Do you have the PC set to auto-log you in?
I do have it set to auto-login.  Should I change that to password protected?  If so, then do you think that might alter things a bit?

Also, when Empathy asks for a password, it's a "key ring", whatever they may be.

---

### Post by nothingspecial on 2010-01-10
@jermza

My fault entirely.

I misinterpreted your question and as a result, I have behaved inappropriately.

Yes, it is stupid that you are asked for your password to start an instant messenger.

Is it the keyring password you are being asked for because this can be disabled.

Again, I`m sorry, having reread the thread, in particular your original post, I can see, I got this totally wrong.

:D

---

### Post by jermza on 2010-01-10
> **nothingspecial said:**
> @jermza

My fault entirely.

I misinterpreted your question and as a result, I have behaved inappropriately.

Yes, it is stupid that you are asked for your password to start an instant messenger.

Is it the keyring password you are being asked for because this can be disabled.

Again, I`m sorry, having reread the thread, in particular your original post, I can see, I got this totally wrong.

:D

Don't apologise.  I'm just not explaining myself properly.  It's all good.

Yes, it IS asking for a key ring (whatever that is).  And yes, I also have Ubuntu set to auto log me in.  If I changed this, then would it make a difference?

---

### Post by JackRock on 2010-01-10
> **jermza said:**
> I do have it set to auto-login.  Should I change that to password protected?  If so, then do you think that might alter things a bit?

Also, when Empathy asks for a password, it's a "key ring", whatever they may be.

I don't use Empathy, but it's installed because it's part of the build.  Pidgin doesn't have this problem.

But  tried to open Empathy again, and it asked me for my password for the keyring.

The keyring has to do with your security certificates for encryption.  Not sure why Empathy's using it, as I see no way to encrypt the data over the IM.  And even if it did, you'd have to go through hoops to ensure the other party had the appropriate private key to decrypt the data.  Then the same in reverse so you could see their responses.

Pidgin is, IMHO, a better IM client.  But I can understand sticking with the default as it's not a bad client at all.  I think, though, the problem lies with the program, not Ubuntu.  So let's focus there.

---

### Post by cariboo on 2010-01-10
> **jermza said:**
> Don't apologise.  I'm just not explaining myself properly.  It's all good.

Yes, it IS asking for a key ring (whatever that is).  And yes, I also have Ubuntu set to auto log me in.  If I changed this, then would it make a difference?


It is because you are using auto-login that the key-ring is asking you for a password. If you go to Applications--> Accessories-->Passwords and Encryption Keys, you will see that Passwords are set to login. If I remember correctly, you can delete that setting, and it won't ask for a key-ring password anymore.

---

### Post by Joeb454 on 2010-01-10
> **jermza said:**
> Yes, it IS asking for a key ring (whatever that is).  And yes, I also have Ubuntu set to auto log me in.  If I changed this, then would it make a difference?

I think it will. I had a friend who had to unlock his keyring to access wireless, we changed it to passworded login, the issue went away.

It's worth a try :)

And as for the keyring - essentially it stores passwords, so saved passwords for IM clients, wireless key's, etc.

---

### Post by nothingspecial on 2010-01-10
In the gui way,

to turn off the keyring.

In your menus go places > home folder.

Press Ctrl+H

This will display all your hidden config files.

Find .gnome2

Find keyrings (within that folder)

delete it

reboot (or just logout and log back in)

It will probably ask you for a network password, if you use wireless. Then ask you for a keyring password.

If it does ask you for a keyring password just leave both boxes empty.

Hopefully, problem solved.

---

### Post by erniej on 2010-01-10
I'm with Jerzma on this. I junked Win 7 because of the incessant need to give approvals, permissions, authentications, etc, etc, only to discover Ubuntu is, if anything, worse. As a new convert (my join date is actually November, 2009, but I can't find a way to change that, either), I'm mystified by why I have to keep authenticating myself and giving myself permissions over and over again when I'm the owner and only user. I have assigned myself every privilege I can find, to no avail. In the course of an hour I have to give myself permissions 15+ times, and for what--to protect me from myself?

You give a teaser response that, yes, you can tweak /etc/sudoers/ but HOW? I've been working with computer systems for 20 years and I trust myself implicitly not to do evil things to my computer, and if I DO screw up, I can fix it. I'm behind a router and a firewall and encryption and I do not seriously believe that all the world's evildoers are poised to pounce on my collection of Victoria calling cards, family photos or 9 years of e-mails.

As much as I enjoy using Karmic and Ubuntu in general, the endless pestering will be what drives me away.

---

### Post by sgosnell on 2010-01-10
If you don't want to type your password every time you run an app which may need the keyring, set your PC to require a password at login.  That password can be stored in the keyring and used by apps to get the password to store your password for that app.  In order to prevent malware from harming your machine, a password is required in order to make any changes to the system.  You can enter a password at login, or you can enter a password every time it is required by an app.  Your choice.

---

### Post by egalvan on 2010-01-10
> **erniej said:**
> 
I'm behind a router and a firewall and encryption and I do not seriously believe that all the world's evildoers are poised to pounce on my collection of Victoria calling cards, family photos or 9 years of e-mails.


The evildoers may not be interested in your personal stuff,
but they WILL be interested in turning your machine into part of their zombie-net, or a spambot, or a DDoS-bot... etc, etc, etc. :D

---

### Post by sgosnell on 2010-01-10
Duplicate.

---

### Post by Mickser_52 on 2010-01-10
I am experiencing a little deja vu reading this thread as I have been asking similar questions on the security forum today

---

### Post by oldos2er on 2010-01-10
> **erniej said:**
> You give a teaser response that, yes, you can tweak /etc/sudoers/ but HOW? 

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

### Post by Methuselah on 2010-01-10
If you want an operating system where the world runs as administrator by default there is always windows Xp.
As many have learned, even Microsoft has become a bit more responsible these days.
So options are becoming limited for those who have become used to lax security.
Some of who switch to Ubuntu/Linux partly because they hear it is more secure yet complain about all the features that made it so from inception.
That makes no sense.

BTW, this is a help section not the complain and moan section.
Ubuntuforums has one of those too.

---

### Post by jermza on 2010-01-11
> **sgosnell said:**
> If you don't want to type your password every time you run an app which may need the keyring, set your PC to require a password at login. 
Okay great.  How do I do that?  (Currently, I have auto log-in set.)

---

### Post by jermza on 2010-01-11
> **jermza said:**
> Okay great.  How do I do that?  (Currently, I have auto log-in set.)
Don't worry.  I found it.  After I logged in, Ubuntu didn't ask for any passwords for Empathy (or Evolution), which is great.  However, it did prompt me for one key ring - something to do with "telepathy" / "applications manager".  Any idea what that is?

---

### Post by erniej on 2010-01-11
BLESS YOU! That was the key. I didn't understand the whole keyring business, although other responders have referred to it. Logging on once I don't mind, the relentless nags were what was puzzling me.

---

### Post by sgosnell on 2010-01-11
The keyring is your list of passwords, which seahorse stores encrypted.  You have to allow the passwords to be stored there, and you'll be asked for each new one.  If you allow the app to access the keyring, it can get and use the password it needs.  If you don't, you'll have to enter the password each time, your choice.

---

