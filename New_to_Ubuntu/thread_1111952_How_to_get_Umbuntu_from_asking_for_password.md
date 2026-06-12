---
title: "How to get Umbuntu from asking for password"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Zanara on 2009-03-31
What is the easiest way to get Ubuntu to stop asking for my password so often? It reminds me of Vista's "allow/deny" thing. Very annoying. 
Thank you.

---

### Post by finer recliner on 2009-03-31
you are usually only prompted for your password when installing software or editing system files...what else are you doing that gives you a prompt for your password?

---

### Post by ibuclaw on 2009-03-31
I agree with finer recliner, you are never asked for a password unless you are persistently wanting to do administrative tasks.

The default timeout is 3 minutes before you are asked for a password again (that is, 3 minutes of inactivity from you performing root tasks). This could be extended, but I think the greater issue is your computing habits.

I, myself, never have to enter my password for days unless a security update comes through.

So why are you always wanting to run things as root?


Regards
Iain

---

### Post by mikechant on 2009-03-31
As per comments above, normally you would only be getting prompted when installing software or updating critical system settings, which typically wouldn't be that often.

It's possible that you are either storing things in inappropriate places, so you need sudo to update them, or that your permissions are not set correctly. If you list some of the typical things you are attempting to do when you need to supply a password then it will be easier to advise.

If you are (say) using this as test box with no critical data and doing a lot of mucking about with system stuff, then it may be appropriate for you to do one or more of the following:
a) Increase sudo time limit as per above
b) Remove requirement for password when using sudo
c) Activate the root account ** and use it for the duration of the superuser activities only.

** I believe there's a rule on this board about not mentioning how to do this (can't find it in the code of conduct though). I hope it's OK to mention that you *can* do it! 

If you were just doing a specific thing like installing software a lot, you can set up rules for sudo (in the 'sudoers' file) to allow particular commands for this purpose to be used without supplying a password, with other commands still requiring a password.

---

### Post by tarps87 on 2009-03-31
> **mikechant said:**
> 
** I believe there's a rule on this board about not mentioning how to do this (can't find it in the code of conduct though). I hope it's OK to mention that you *can* do it! 

I believe that you can say that it is possible (I can't see why not) but you can not say how to do it and should advise new users against it. It goes along the belief that if you don't know how to do it then you shouldn't do it.

@Zanara if you are asking about the network passwords that is different and you should look at using the keyring functionality, if you need any help with this just post back

---

### Post by kpatz on 2009-03-31
> **mikechant said:**
> c) Activate the root account ** and use it for the duration of the superuser activities only.No need to do this... just run "sudo -i" from a terminal, and you'll get a root prompt.

---

### Post by ibuclaw on 2009-03-31
> **mikechant said:**
> 
a) Increase sudo time limit as per above

```
sudo visudo
```
Then:
```
Defaults:ALL timestamp_timeout=10
```
A slightly more reasonable timeout, but I still don't agree with the use of it.


> **mikechant said:**
> 
b) Remove requirement for password when using sudo

BAD BAD BAD BAD BAD.
If anything malicious runs under your username, you are way ahead of yourself if you wish to seek a broken system, a hacked system, **or** loss of data.

But, on the brighter side, you can allow **certain applications** to run as root without a password, so it isn't all that bad, just as long as you
[LIST]
[*] Don't Abuse it
[*] Restrict Access like the devil
[/LIST]


> **kpatz said:**
> No need to do this... just run "sudo -i" from a terminal, and you'll get a root prompt.
Again, BAD BAD BAD BAD BAD.
```
sudo -s
```
Is better, but only slightly. I really don't see the need for anyone to run a shell as root ever. There is plenty in place that can be setup without it.


> **mikechant said:**
> 
c) Activate the root account ** and use it for the duration of the superuser activities only.

It could be done, but you will break Ubuntu's Security paradigm in the process. It's taboo for you do to this, so expect a lot of flames and shocked faces if you brag about it :)

Regards
Iain

---

### Post by 1clue on 2009-03-31
Zanara,

First, let me say that if you are new at this whole Linux thing, then you are probably doing something in a way that is not proper for a secure system.  You don't need to stop doing that thing so much as start doing it a different way.

Those guys above have hopped on the super-user bandwagon, but really what they want is for you to describe what you do that causes the password to be required, and then we'll tell you how to do it without that sort of thing.

Now, let me hop on that same wagon:  Days, weeks or months should go by before you need to type that password at a time when you are not logging in.  That depends on how stable your system is, how exposed your system is and what you do on it.

If you do figure out how to do the permanent-superuser thing, then be warned:

Linux/Unix is pretty secure when you use it as intended.  However, if you do everything as root (or ANYTHING you don't absolutely have to do) then you are playing with fire.  Root user on a Linux box has even fewer restrictions than Administrator on a Windows box.  The assumption is that if you are root, you know what you are doing and probably won't even be asked before the system lets you do something profoundly stupid.

Linux doesn't get viruses like Windows, at least not ones that can do much harm, but that's only because the normal user is locked down as well as it is.  If you run as root and opened a file infected with a virus your system can run, then you are totally unprotected.  It's not as improbable as you might think, either.  A lot of scripting languages out there are available in Linux and Windows and Mac.  Linux users have a mental block when thinking about viruses, but intrusions of some form or another are very common.  A virus is a very specific form of intrusion, but there is as much malicious software out there for Unix variants as there is for Windows.

The last thing you should do is give your user access to a whole lot of extra junk.  Don't play with the permissions, and don't run as root.  There is absolutely no reason why the owner of the box needs to have any more than stock permissions for more than 4 days a month once the system has been set up.

---

### Post by Paddy Landau on 2009-03-31
> **1clue said:**
>  Days, weeks or months should go by before you need to type that password at a time when you are not logging in.  That depends on how stable your system is, how exposed your system is and what you do on it.
But if you need regular access, you may need it more often. I use [TrueCrypt]("http://www.truecrypt.org/"), and it needs the password whenever I start it up.

---

