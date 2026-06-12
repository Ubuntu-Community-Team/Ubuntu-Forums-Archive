---
title: "[SOLVED] Sudo visudo change... Not working? :|"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by LtPitt on 2008-12-18
Hello there!
I'm on a dummy foolish useless brand new ubuntu installation and I want to get rid of ALL password requests.
I know it's not correct but let's say I want to do it.

I've tried

sudo visudo

and that's my /etc/sudoers modified:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
%pitto ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root ALL=(ALL) ALL
pitto ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%pitto ALL=(ALL) ALL




As far as I've understood with those settings the user "pitto" should be root-like, right?
So why when I use the user and groups tool in "system" it keeps on asking me to unlock?
Same behavior for btnx (an application used to bing mx revolution buttons)...

I'm going mad :|

---

### Post by Titan8990 on 2008-12-18
Ubuntu (and its variants) is the only distro that follows this practice of sudo.

It sounds like a different distro might be for you. The forums don't support unlocking the root account but IMO, unlocking root is much better than what you are doing from a security standpoint...

This goes along with the Windows mindset of always running the computer as a user that run malicious software that can destroy the OS or worse.

---

### Post by LtPitt on 2008-12-18
I do agree but after using my computer for more than 10 minutes and writing 10000 times the admin password (without any... mmmh real "menace"... I'm at home. No important files. No viruses on linux) I feel that my nerves are going to collapse :D


I also use a lot pc from my bed (I have a bluetooth mouse) for navigation and youtube...
Now and then I use onboard (virtual keyboard) to digit a few things without getting up.
When the focus is on an administrative password request...
The onboard loses focus and functionality :|
It's like...

It's like locking firmly every single door of your house.

It's really safe.
It's really a pain in the ***! :D

So...
If someday I'll need a safe pc I'll respect those security settings.
But now I know that I don't want to.
It's "free" software...
I want to be free to decide to digit passwords or not.
That's all :)

---

### Post by Michael.Godawski on 2008-12-18
Relax.

[http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)

If you are root whole the time, even a simple change of permission (on purpose or by change) can render your system useless. It has nothing to do with your doors in your house. Sudo protects you from your own actions.

I wanted to post a link to the rootsudo page on the
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
but it is down at the moment. 

I cannot give you the desired information (against forum policy), but you will find it there.

The Truth is out there...

---

### Post by bwallum on 2008-12-18
> **LtPitt said:**
> 
So...
If someday I'll need a safe pc I'll respect those security settings.
But now I know that I don't want to.


I agree, you can take the brakes off, disconnect the steering and poke yourself in both eyes much easier with another distro. Exciting isn't it...

---

### Post by LtPitt on 2008-12-18
Aw, come on!
I was just jocking and having a little, stupid fun :)
Check emoticons, mates :D

I understand and appreciate the correct spirit that moves your replies (btw thanks for the hint ;) ) but I have a "dangerous" windows xp fine tuned and defended by a free antivirus that has been up and running for 2 years...

I think I'll be fine with Ubuntu not asking me passwords :)

And this will be a self-teaching installation so...
The more mess I do the more I learn :)

I don't say that you have to remove brakes...
I just like the option to use them or not :)

---

### Post by LtPitt on 2008-12-18
I think this link (found in the page you suggestes) says it all :)

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You can also get single super user permissions for your normal user for a single binary.

Cool :)

Thx!

---

### Post by donkyhotay on 2008-12-18
One of the reasons linux doesn't have viruses is because they can't do any real damage without root access. Be aware that if you choose to run your system as root if you accidently tell linux to shoot itself in the head it will simply smile at you as it fullfills your request. If you don't like having to type in your password so often I would recommend changing your sudo settings. You can change how long sudo grants admin access before requiring the password again. I believe the default on ubuntu is about 5-10 minutes. I don't know exactly how to do this but it would be much easier/safer then trying to run permanently as root.

---

