---
title: "What happened to root?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Pfredpfudpucker on 2009-02-24
When I installed Umbuntu, I was not asked to provide a root password.  Instead, I was asked my name, and was also asked for a password for that name.  After the installation was complete, and I looked around in Umbuntu for the first time, I also discovered that I could su into root mode when root authority was required.  My previous experience had been that root could be accessed by su/sudo, but I could also log in as root using a different password, if I was going to spend some time working as root.

I liked that arrangement.  How can I set up the root account so that it can be accessed directly, with the "root" username, and with a different, more secure password?

---

### Post by taurus on 2009-02-24
There is a root account but it is locked by default.  Therefore, you use sudo to gain root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But if you really want to assign a password to root, there is a way but I believe we are not allowed to discuss it here!

---

### Post by roccivic on 2009-02-24
System > Administration > Users and groups

Unlock the app with your username and password, then you can assign a password to user "root". Keep in mind that you cannot login into X as root.

Peace

---

### Post by roccivic on 2009-02-24
> **taurus said:**
> But if you really want to assign a password to root, there is a way but I believe we are not allowed to discuss it here!

And why not?

---

### Post by hansdown on 2009-02-24
Hi Pfredpfudpucker.

Your password is also your root password.

I can't help with the other part of your question though.

---

### Post by kellemes on 2009-02-24
> **roccivic said:**
> And why not?

[http://ubuntuforums.org/showthread.php?t=716201]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by redseventyseven on 2009-02-24
> **Pfredpfudpucker said:**
> When I installed Umbuntu, I was not asked to provide a root password.  Instead, I was asked my name, and was also asked for a password for that name.  After the installation was complete, and I looked around in Umbuntu for the first time, I also discovered that I could su into root mode when root authority was required.  My previous experience had been that root could be accessed by su/sudo, but I could also log in as root using a different password, if I was going to spend some time working as root.

I liked that arrangement.  How can I set up the root account so that it can be accessed directly, with the "root" username, and with a different, more secure password?

Use a different distribution. Ubuntu have made a definite choice not to allow user accounts in their distribution (this is because it is seen, with good reason, as a security risk).

Other distributions have chosen not to go down that path, for their own reasons. That's the beauty of Linux - you can choose what you like!

For example, Linux Mint is Ubuntu-based, and gives you the option of creating a root account (though they don't recommend it).

EDIT: However, I would recommend reading the notice posted by kellemes first.

---

### Post by kellemes on 2009-02-24
> **redseventyseven said:**
> 
For example, Linux Mint is Ubuntu-based, and gives you the option of creating a root account (though they don't recommend it).

So does Ubuntu, it's just you can't talk about it in here..

---

### Post by redseventyseven on 2009-02-24
> **kellemes said:**
> So does Ubuntu, it's just you can't talk about it in here..

Well, yes, technically, but that's not the comparison I was trying to make. Rather I meant that Mint prompts the user (with a GUI) to choose whether you want to enable the root account or not the first time you run the distro. This is compared with the necessity to search on the internet for the right terminal command, as with Ubuntu.

Point taken though.

---

### Post by Pfredpfudpucker on 2009-02-25
Ooooooooohhhhhhhh.   I see!  Just because I have botched several attempts to get totem to play wmv and avi video, and have had to re-install Umbuntu three different times (finding out along the way that I needed to re-format in NTFS, and then start a clean install with another format into Linux because if I install over the old Linux partition some of the botched up files re-appear and the GUI won't come up and there I am staring at that darned command line) and have lost my audio when I get totem to play the unsupported video and can't remember just exactly to enter to get my GUI back so I won't be completely lost!  Just because of that you think I must be dangerous to my PC if left unfettered as root.

You're right!

Anyway, I think Umbuntu is the best distribution out there, and so I'll just sudo away.

Thanks for all the responses.

Pfred

---

### Post by Hobgoblin on 2009-02-25
> **Pfredpfudpucker said:**
> I could also log in as root using a different password, if I was going to spend some time working as root.


If you *really* want to do that then you can **sudo su** which will leave you as root until you exit.

---

### Post by egalvan on 2009-02-25
> **Pfredpfudpucker said:**
> Ooooooooohhhhhhhh.   I see! Just because of that you think I must be dangerous to my PC if left unfettered as root.

Pfred

Short story... yes.
If you access the root account, you own the computer.
You can do most anything. Including damaging/erasing/changing files.

And now, the rest of the story.
If someone accesses the root account, they own the computer.
They can do most anything. Including damaging/erasing/changing files.

A root account is the "Holy Grail" for a cracker.
In Ubuntu, this is not as easy to access.

The thing is, you have a CHOICE.
If you don't like Ubuntu's security choices, then you can try another distro.
Or look around, and fine the process by which you can by-pass that security.

Different distros have different philosophies.
For example, Debian does not allow closed source/proprietary software. You can install it, but it's not included in the original distro. It's discouraged.

---

### Post by RetchingRabbit on 2009-02-25
> **egalvan said:**
> 
A root account is the "Holy Grail" for a cracker.
In Ubuntu, this is not as easy to access.


Not wishing to be argumentative, but this is a singularly ridiculous statement.
What damage could be done with root access that could not be done with sudo or sudo su?
To my way of thinking, a root account improves security by requiring a different (second!) password. How eliminating that second password increases security is a bit of a mind job, i think.
:p

---

### Post by Temposs on 2009-02-25
> **RetchingRabbit said:**
> Not wishing to be argumentative, but this is a singularly ridiculous statement.
What damage could be done with root access that could not be done with sudo or sudo su?
To my way of thinking, a root account improves security by requiring a different (second!) password. How eliminating that second password increases security is a bit of a mind job, i think.
:p

It improves security because it more or less forces a user of an Ubuntu computer to use an account that has just user-level access by default. Most of the security issues that a typical user comes across occur because of code that the user himself initiates(clicking on executables, running javascript, etc). If there is a root account, many typical computer users may be tempted to simply log into the root account for normal usage(see Win XP) which completely undoes the protection of root privelege, if the user unknowingly executes malware on their system. 

With Ubuntu's system, a typical user runs code at user level and will be alerted when some code wants to do something that requires root level access. That means each time a root operation is done, the user is alerted and can make a decision whether the code running should indeed deserve that access or not. It is much safer from the user perspective. Also, it stops the user from immediately deleting their whole filesystem without having to type their password and such. It just puts a layer of security in front of all system-level operations.

See this page for a list of advantages and disadvantages to this approach:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

