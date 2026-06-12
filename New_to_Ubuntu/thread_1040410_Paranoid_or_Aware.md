---
title: "Paranoid or Aware?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by duds2008 on 2009-01-15
Hello!:) I am curious to know if there is a root p/w prior to a user changing it? How is the installer of the system able to change such a powerful users password so easily? Is this not something all users of ubuntu should be made aware of. I always make sure root has a password that I know. I accept the fact that people trying to gain access to a system can use username root as an advantage (man sudo_root), but shouldnt we at least know how they go about setting up this absent or anonymous password? Is it some sort of way that certain people can take advantage (later on) of simple users, to pose security issues i.e: viruses etc? Then try the windo$e thing of selling antivirus? Call me paranoid...but take BG as an example. I support RMS all the way as far as freedom is concerned!! :)

---

### Post by LowSky on 2009-01-15
root is disable in Ubuntu. in otherwords you cant sign in as root. If you want root access it has to be configured. To configure it you need you sudo password. for the most part sudo=root

side note what is BG and RMS?

---

### Post by duds2008 on 2009-01-15
[QUOTE=LowSky;6554571]root is disable in Ubuntu. in otherwords you cant sign in as root. If you want root access it has to be configured. To configure it you need you sudo password. for the most part sudo=root

 I know about sudo passwd...but HOW is the root p/w disabled? BG= bill gates RMS=Richard Mark Stallman. lol :0

---

### Post by duds2008 on 2009-01-15
> **duds2008 said:**
> [QUOTE=LowSky;6554571]root is disable in Ubuntu. in otherwords you cant sign in as root. If you want root access it has to be configured. To configure it you need you sudo password. for the most part sudo=root

 I know about sudo passwd...but HOW is the root p/w disabled? BG= bill gates RMS=Richard Mark Stallman. lol :0
Are there any other distros that use this method of disabling the password? I havent come across any.

---

### Post by stchman on 2009-01-15
> **duds2008 said:**
> Hello!:) I am curious to know if there is a root p/w prior to a user changing it? How is the installer of the system able to change such a powerful users password so easily? Is this not something all users of ubuntu should be made aware of. I always make sure root has a password that I know. I accept the fact that people trying to gain access to a system can use username root as an advantage (man sudo_root), but shouldnt we at least know how they go about setting up this absent or anonymous password? Is it some sort of way that certain people can take advantage (later on) of simple users, to pose security issues i.e: viruses etc? Then try the windo$e thing of selling antivirus? Call me paranoid...but take BG as an example. I support RMS all the way as far as freedom is concerned!! :)

I been using Ubuntu for nearly two years and have never had a need to login as root.  This is an especially dangerous thing as you will bypass all the security features of Ubuntu.  If you need to use an app as root put sudo or gksudo in front of it.

---

### Post by duds2008 on 2009-01-15
> **stchman said:**
> I been using Ubuntu for nearly two years and have never had a need to login as root.  This is an especially dangerous thing as you will bypass all the security features of Ubuntu.  If you need to use an app as root put sudo or gksudo in front of it.

Sorry guys! I think you missing the point. You all seem to know quite a bit about GNU/LINUX and have obviously been using it a while. All I am saying is that there may be some sort of user limitations being implemented (right now in its initial stages), of taking control of the future market? I do not believe that every person running ubuntu is even aware of a user called root.
PS: Thanx for the link:)
V=viruses
I=intruders
T=trojans
S=spyware
A=adware

---

### Post by LowSky on 2009-01-15
> I know about sudo passwd...but HOW is the root p/w disabled? BG= bill gates RMS=Richard Mark Stallman. lol :0

Root is disabled, not by someone turning it off, but by it never being configured. In other words its a user that does exists but has no rights. It can only be set up by the person with simular rights, like the SUDO user. This way no one has a secrete way in or anything like that.

Hope that makes more sense...

---

### Post by bodhi.zazen on 2009-01-15
> **duds2008 said:**
> I know about sudo passwd...but HOW is the root p/w disabled?

Same as any other distro :twisted:

In Ubuntu, by default, the root account is locked.

In Ubuntu , if you set a root password, use

> sudo usermod --lock rootIn general use

sudo passwd root -l

but that second command *may* cause breakage

[https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755)

See also [http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/disabling-user-accounts.html](http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/disabling-user-accounts.html)

You can also set the shell to /bin/nologin or /bin/false

sudo is patched to allow the root account to be locked.

Edit: I see you are asking also about limiting users. In general users are limited by permissions. If you need something beyond permissions take a look at Apparmor or SELinux.

[https://wiki.ubuntu.com/FilePermissions](https://wiki.ubuntu.com/FilePermissions)

---

### Post by LowSky on 2009-01-15
> **duds2008 said:**
> Sorry guys! I think you missing the point. You all seem to know quite a bit about GNU/LINUX and have obviously been using it a while. All I am saying is that there may be some sort of user limitations being implemented (right now in its initial stages), of taking control of the future market? I do not believe that every person running ubuntu is even aware of a user called root.

Think of it this way You dont need to even have a user named root. It could named Linus for all purposes of this question. the fact is Root is there in name only. It doesn't work, and it can't work without the Sudo user turning it on. you need to know the Sudoers password to create root access. Its a check and balance if you will.

And what Market? Linux is free and is based on Unix, also free. 

Do you think Root wasn't created so one day when Skynet gets turned on all the computers will cotrol humanity, that simply isn't the case.

Root is in every version of Linux most have access to it from the start some don't. But always the user has to create the password. it isn't supplied to them. It is the basis of the system and like I stated before it doesn't need to be named root. Root was the name taken from Unix for simplifcation of the OS. The idea of root is so the system Admin can effectively control the machine. Ubuntu turns this off as it assumes the normal user doesn't alwys want or need root, as root can mess up files and system setting if you not careful, for example Windows XP, assume the one and only user policy thus you are root in that sense and why the OS is as uggy as it is.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by duds2008 on 2009-01-15
> **LowSky said:**
> I know about sudo passwd...but HOW is the root p/w disabled? BG= bill gates RMS=Richard Mark Stallman. lol :0

Root is disabled, not by someone turning it off, but by it never being configured. In other words its a user that does exists but has no rights. It can only be set up by the person with simular rights, like the SUDO user. This way no one has a secrete way in or anything like that.

Hope that makes more sense...[/QUOTE]

Yes it makes total sense..thanx m8:) but is this for gospel or is there a conspiracy? i.e: a way that they can take control? I just cant accept the totally free concept of ubuntu...ultimately money is involved.( Sorry.....you must be thinking how paranoid I am!...and No!! I am not coming off crack cocaine. I just find it very strange. They have obviously done this to enable normal users not to screw up thier system by logging in as root...which dont make sense as you can do it as easily as a sudoer. Do you know how to disable root when building a Distro? Seems pretty complicated!

---

### Post by LowSky on 2009-01-15
no actually its really easy that hard to disable root.
I did this when install Arch linux from scratch. I like the Ubuntu philosophy, so I brought that over into my Arch system. All you do is modify the user settings simple as that.

As for the money thing, yes money is involved Canonical the company that releases Ubuntu makes money on Support. So if you don't want to listen to us you can buy support from Canonical. Infact if you buy a Dell PC with Ubuntu it comes with Canonical Suppport for the OS.

If you want a Free no one makes a dime OS then use Debian or Arch, or Slackware. No one makes a dime on any of it. Infact Linus Torvalds made no real money off Linux until Red Hat or Novel (I can't remember which) gave hime stock options.

---

### Post by duds2008 on 2009-01-15
> **duds2008 said:**
> Root is disabled, not by someone turning it off, but by it never being configured. In other words its a user that does exists but has no rights. It can only be set up by the person with simular rights, like the SUDO user. This way no one has a secrete way in or anything like that.

Hope that makes more sense...

Yes it makes total sense..thanx m8:) but is this for gospel or is there a conspiracy? i.e: a way that they can take control? I just cant accept the totally free concept of ubuntu...ultimately money is involved.( Sorry.....you must be thinking how paranoid I am!...and No!! I am not coming off crack cocaine. I just find it very strange. They have obviously done this to enable normal users not to screw up thier system by logging in as root...which dont make sense as you can do it as easily as a sudoer. Do you know how to disable root when building a Distro? Seems pretty complicated![/QUOTE]

Hang on............Something just clicked!!! So... its like you are GOD till you create GOD:) Now it makes perfect sense:) The installer of the system is god! Thanks m8...sorry I didnt see it right away:) And most probably if users dont know about root they should stick to windoze! Thanks for making this clear to me!!!

---

### Post by sydbat on 2009-01-15
> **lowsky said:**
> do you think root wasn't created so one day when skynet gets turned on all the computers will cotrol humanity, that simply isn't the case.lmfao!! +1

---

### Post by bodhi.zazen on 2009-01-15
Thread closed.

This whole conversation has gotten so far off topic I am not sure what the topic is.

The OP question, IMO, was answered in my post. 

@duds2008 If , after reviewing the information I provided, you have a technical question, pleas ask (in a new thread).

---

### Post by duds2008 on 2009-01-15
Sorry guys this is not a question...just a Thankyou to Lowsky for making something clear to me ( thread got closed before I could send thanx!) Sorry for doing this by starting new thread:(

---

### Post by mikewhatever on 2009-01-15
Next time send a PM.

---

### Post by bodhi.zazen on 2009-01-15
> **duds2008 said:**
> Sorry guys this is not a question...just a Thankyou to Lowsky for making something clear to me ( thread got closed before I could send thanx!) Sorry for doing this by starting new thread:(

:rolleyes:

Threads merged

> **mikewhatever said:**
> Next time send a PM.

Indeed

---

