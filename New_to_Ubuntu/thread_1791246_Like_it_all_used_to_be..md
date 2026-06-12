---
title: "Like it all used to be."
date: 2011-06-26
forum: New to Ubuntu
---

### Post by OmegaForte on 2011-06-26
I'm gonna be very brief about this, as I fear if I get into it, I'll come off a bit more terse than I intend to.

How do I disable the SUDO prompt for every little change I make to programs, and how do I disable the caution launcher? I'm tired of fighting this stuff.

---

### Post by snowpine on 2011-06-26
Welcome to the forums! When you use "sudo" just type your (user) password. It'll take you 2 seconds. You've heard "Linux is more secure than Windows" and the password requirements are a big reason why. We are not allowed to help you disable security features on this forum, sorry. :)

---

### Post by wolfen69 on 2011-06-26
Once you are done setting up your computer, there should be very little need to use sudo.

---

### Post by Gone fishing on 2011-06-26
If you want a temporarily have root in a terminal sudo -i will give it you.

---

### Post by oldos2er on 2011-06-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by OmegaForte on 2011-06-26
Right. Okay.

So removing the annoying sudo prompt. What about that? And about caution launcher?

I'm not an idiot. I know how to run programs from terminal with sudo. I'm not going to run background applications with sudo. I'm not going to run network applications with sudo. I'm not going to run anything that has to do with client services or system management with sudo.

So, I guess the better question would be "How do I turn ubuntu into something I can use without being pestered to sudo for every little I make?"

The program that inspired my fury today is moblock, an ip filter for linux. I'm not going to sudo anything that has to do with networking out of practice, but I'm constantly having to sudo the damned thing so it can write to it's own config file, and restart itself. That's twice in five seconds I have to type that password in. And it's not a short password, either.

Then, there's caution launcher. You know, that annoying little box that comes up every time you try to run something and then blathers on about executable bit, which was handled on a hardware level three years ago? Yeah, about that.

This is my system. Why the hell can't I use it?

And don't give me that "more secure than windows" line. A system is as secure as the person makes it. Not saying linux isn't secure, I'm saying that most of the people running linux NEED the security, so they look harder for solutions.

---

### Post by haqking on 2011-06-26
this has been discussed over and over.

see this thread [http://ubuntuforums.org/showthread.php?t=1788308](http://ubuntuforums.org/showthread.php?t=1788308)

and it says in the thread, the security model exists for a reason, it can be circumvented but it is done at your own risk.

The real fact is that if you dont know how to do it, it probably shouldnt be done ;-)

good luck

---

### Post by Gone fishing on 2011-06-26
So what's the problem with sudo -i you can run a as many commands as you want without using sudo after?

---

### Post by Paqman on 2011-06-26
> **OmegaForte said:**
> That's twice in five seconds I have to type that password in.

Have you set your sudo timeout to less than five seconds? Just set it back to something more sensible.

> Then, there's caution launcher. You know, that annoying little box that comes up every time you try to run something and then blathers on about executable bit

You mean the dialogue that comes up asking if you'd like to either display or execute a file that's a executable? You can tell Nautilus to just open them instead, Edit > Prefs > Behaviour > View/Run executable text files when opened.

> 
This is my system. Why the hell can't I use it?


Remember, you're not the only user on your system. Now that computers are connected to the internet your machine has countless millions of people and other machines able to access it. Your system needs to be a able to tell you from them.

---

### Post by OmegaForte on 2011-06-26
> **Paqman said:**
> Have you set your sudo timeout to less than five seconds? Just set it back to something more sensible.



You mean the dialogue that comes up asking if you'd like to either display or execute a file that's a executable? You can tell Nautilus to just open them instead, Edit > Prefs > Behaviour > View/Run executable text files when opened.



Remember, you're not the only user on your system. Now that computers are connected to the internet your machine has countless millions of people and other machines able to access it. Your system needs to be a able to tell you from them.

THIS is what I was looking for. A knowledgeable person who answered my questions. Thanks man. I owe ya one.

Caution launcher. You know, that annoying little bugger that always blocks programs if you haven't set the permission to be executed? While this may be good to prevent people from launching malware, this is very, very very bad for people who are trying to turn ubunutu into a working system. Like trying to run a program that has a huge library of junk that it has to have in specific places, that are bigger than your EXT4 partition, so you have to run it from the read only medium (Or NTFS, with no intention to chmod it due to it being a foreign drive), so you can't set the permissions.

---

### Post by snowpine on 2011-06-26
Never mind; Good luck! :)

---

### Post by OmegaForte on 2011-06-26
Thanks. I guess I'm boned. 

Maybe I should install pine...

---

### Post by uRock on 2011-06-26
> **oldos2er said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This explains everything. :P

---

### Post by dFlyer on 2011-06-26
An OS is a personal choice, install whatever you want and modify it what ever way you want. If you use the forum search you will find your answer. No one here thinks you're dumb, it's just too many times someone trashes there system, blames ubuntu and moves on. Ubuntu is very functional, I've been using it since 2006 as my only OS. Linux is general is very stable, I've been using it since the mid 90's in various distro's. There are many distros that allow you to login and run as root, which isn't very smart, as that exposes you just like windows to the outside world, but than again that is ones choice. Again search the archive here, or do a google search and you will find your answer. sudo is just  a security feature.

---

### Post by jtarin on 2011-06-26
> **OmegaForte said:**
> 
The program that inspired my fury today is moblock, an ip filter for linux. I'm not going to sudo anything that has to do with networking out of practice, but I'm constantly having to sudo the damned thing so it can write to it's own config file, and restart itself. That's twice in five seconds I have to type that password in. And it's not a short password, either.
There is a root terminal hiding in the menu....open it and use it.

---

### Post by jre on 2011-06-28
Sounds as if you were using the GUI mobloquer. Right?

Make sure that you have specified the correct sudo app in the configurations dialog. Either gksu or kdesudo, depending on your desktop. Then "remember" your password and you'll never be pestered again. (Please note that I haven't used mobloquer recently, but I think that is how it worked.)

Generally network operations need to be authorized by root, but not a user, because they apply to the whole system, not just the currently logged in user (This is just to explain the design concept of moblock. I know/guess that in your case there is no difference because you are on a single user system.)

Sidenote: Once we have it ready, the pgl-gui (successor of mobloquer) will use policykit, plus it won't require the restart to apply changes.

---

