---
title: "log in"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by sanjaypothen on 2010-04-28
Though i type the password correctly i am not able to log in.The password i type is 100% correct .Sometime i can log in,sometimes not able to log in.

---

### Post by xumuk37 on 2010-04-28
be sure caps lock nad num lock are unpressed... once you could log in just set a new password ```
sudo passwd username
```

---

### Post by tica vun on 2010-04-28
Once you're logged in, you could try changing your password, it's under System->Administration->Users and Groups.

---

### Post by sanjaypothen on 2010-04-28
> **xumuk37 said:**
> be sure caps lock nad num lock are unpressed... once you could log in just set a new password ```
sudo passwd username
```

No,i don't want to set a new password! May be i think it is not able to log in due to the time lag in typing the password.So can i know if there is a method to increase the time for typing the password?
             It is difficult to log in. Even if type with the on screen key board it is not log in.
 I got some error message' has it got to do something  with ORBit.What is it.Pl.?

---

### Post by _0R10N on 2010-04-28
Is this happening on the Gnome Log in Screen, or on a terminal, or on both! Other user can log in normally?

Kind regards!

_0R10N >>

---

### Post by sanjaypothen on 2010-04-28
> **_0R10N said:**
> Is this happening on the Gnome Log in Screen, or on a terminal, or on both! Other user can log in normally?

Kind regards!

_0R10N >>
I don't know how to log in from the terminal.But a gnome log in screen pops up and i type my password there.Now i got a error message,the screen shot i will give below.

---

### Post by Silent Warrior on 2010-04-28
Well, I can tell you straight away that evolution-alarm-notify has nothing to do with your logging in. The "stale NFS-locks" due to some crash or other are doubtless more interesting, though. Having no experience of NFS myself, I'll just... vacate the thread before ending up giving bad advice.

---

### Post by _0R10N on 2010-04-28
To log in from a terminal, when the log in screen appears hit Ctrl+Alt+F1 (or f2...) then you'll a enter in text mode. You'll be prompt for your user and password. To get back to graphical mode you must hit Ctrl+Alt+F7.

Well, back to our problem now. I googled it and I've found two alternatives:
First:
```
chmod 700 /tmp/gconfd-$USER/
```
If that doesn't solve the problem, then deleting the following folder should work. I strongly recommend to make a back up of it, so you can easily go back if something goes wrong.
```

cp -r ~/.dbus/session-bus ~/.dbus/session-bus.bak
rm -rf ~/.dbus/session-bus

```

Kind regards!

_0R10N >>

---

### Post by joes7 on 2010-04-28
This has happened to me a couple of times. It is quite easy to fix, though:P!

Go to your log in screen and select log in as another user. Remmember that during the installation process we were asked to add a "root" username? asuming you didn't change the username, simply log in with the following details:

_username:_ root (or whichever way you renamed it -if you did)
_password_: password you specified during installation process.

Clear? Good luck!:)

---

### Post by alfplayer on 2010-04-28
> **joes7 said:**
> This has happened to me a couple of times. It is quite easy to fix, though:P!

Go to your log in screen and select log in as another user. Remmember that during the installation process we were asked to add a "root" username? asuming you didn't change the username, simply log in with the following details:

_username:_ root (or whichever way you renamed it -if you did)
_password_: password you specified during installation process.

Clear? Good luck!:)

It's not possible to do this because root user is not enabled on Ubuntu by default. Besides, enabling the rot account and graphical log in as root user is not recommended. And this wouldn't fix it because, for a start, the regular user's files and settings will not be available.

---

### Post by sanjaypothen on 2010-04-29
> **alfplayer said:**
> It's not possible to do this because root user is not enabled on Ubuntu by default. Besides, enabling the rot account and graphical log in as root user is not recommended. And this wouldn't fix it because, for a start, the regular user's files and settings will not be available.
I am now not able to see the log in screen! it is directly going to my desktop! I think my earlier thread "How do i reduce my font size in windows" in the 'Absolute Beginner' is interconnected! Pl.refer that thread and its posts.
 Some body pl.help?

---

### Post by sanjaypothen on 2010-04-29
> **_0R10N said:**
> To log in from a terminal, when the log in screen appears hit Ctrl+Alt+F1 (or f2...) then you'll a enter in text mode. You'll be prompt for your user and password. To get back to graphical mode you must hit Ctrl+Alt+F7.

Well, back to our problem now. I googled it and I've found two alternatives:
First:
```
chmod 700 /tmp/gconfd-$USER/
```If that doesn't solve the problem, then deleting the following folder should work. I strongly recommend to make a back up of it, so you can easily go back if something goes wrong.
```

cp -r ~/.dbus/session-bus ~/.dbus/session-bus.bak
rm -rf ~/.dbus/session-bus

```Kind regards!

_0R10N >>
Pl. let me know how or what is text mode? though i typed the user name and password in the terminal, i was not able to see the desktop screen. (Please let me know what is meant by "a enter in text mode")

---

### Post by sanjaypothen on 2010-04-29
Somebody pl.help fast.I am not able to log in.

---

### Post by sydbat on 2010-04-29
A stupid question here - how are you getting onto this forum? Are you using another computer? 

If you are powering up your Ubuntu box and getting to the desktop and going into Firefox and asking these questions, I am not sure what you cannot log into. But I might just be missing something...

---

### Post by alfplayer on 2010-04-29
In text mode there is a black screen with white text. You get text like this:

```
Ubuntu 10.04 LTS sanjaypc tty1

sanjay login:
```

That's a username/password prompt.

---

### Post by alfplayer on 2010-04-29
> **sydbat said:**
> A stupid question here - how are you getting onto this forum? Are you using another computer? 

If you are powering up your Ubuntu box and getting to the desktop and going into Firefox and asking these questions, I am not sure what you cannot log into. But I might just be missing something...

Dual-booting? Another PC? It's not really important, is it?

---

### Post by sydbat on 2010-04-29
> **alfplayer said:**
> Dual-booting? Another PC? It's not really important, is it?It might be because he states in one post that:> I am now not able to see the log in screen! it is directly going to my desktop!which is why I asked.

He might be unable to log into his email, for example, but we assume he cannot log into his Ubuntu install.

---

### Post by alfplayer on 2010-04-29
> **sydbat said:**
> He might be unable to log into his email, for example, but we assume he cannot log into his Ubuntu install.

Right. Or he may have set auto-logon to the Gnome desktop.

Sanjay, please clarify.

Can you get past the log in screen? Does it work now?

---

### Post by sanjaypothen on 2010-04-29
> **alfplayer said:**
> Right. Or he may have set auto-logon to the Gnome desktop.

Sanjay, please clarify.

Can you get past the log in screen? Does it work now?

Hi,both of u(Sydbat & Alfplayer)
                             When i installed the ubuntu 9.10 desktop edition as a Dual boot with windows XP ,it was set on auto logon to the Genome desktop.     -------
-----                                           --------------    
In the text mode(CTRL+ALT+F1) and in the graphical mode(CRTL+ALT+F7),i am not able to log in to my Ubuntu install.
                            -----------------
Pl. note as i have posted in my post NO:1 sometimess i can log in,sometimes it doesn't happen.
                       The log in was done in the graphical mode only after 10-13 times trial; it does not log in  at the first attempt.Sometimes the log in doesn't even take place.

                      So i tried the text mode,here also when the user name and password was typed the desktop session did not come.
                      
                       Now here is what i got as the output from the text mode (ie.genome terminal as is commonly called,i suppose)


          Ubuntu 9.10 sanjay-desktop tty1
          sanjay-desktop login:
          password:
          Last login:Thu Apr 29 11:10:09 EDT 2010 on tty1
          Linux -sanjay-desktop 2.6.31-20-generic #58-ubuntu SMP 
          Fri Mar 12 05:23:09 UTC 20 10 i686
          To access official ubuntu documentation,please visit:
          htt://help.ubuntu.com/
          0 packages can be updated.
          0 updates are security dates.
           sanjay@sanjay-desktop:~$_
 
                   This was the out put. Now what should i do in order to log in quickly? Kindly help.

---

### Post by alfplayer on 2010-04-29
You are getting a command prompt in text mode: "sanjay@sanjay-desktop:~$". This implies you have logged in (in text mode). It is now possible to try what _0R10N suggested.

---

### Post by Geoff918 on 2010-04-29
> **sanjaypothen said:**
> Hi,both of u(Sydbat & Alfplayer)
                             When i installed the ubuntu 9.10 desktop edition as a Dual boot with windows XP ,it was set on auto logon to the Genome desktop.     -------
-----                                           --------------    
In the text mode(CTRL+ALT+F1) and in the graphical mode(CRTL+ALT+F7),i am not able to log in to my Ubuntu install.
                            -----------------
Pl. note as i have posted in my post NO:1 sometimess i can log in,sometimes it doesn't happen.
                       The log in was done in the graphical mode only after 10-13 times trial; it does not log in  at the first attempt.Sometimes the log in doesn't even take place.

                      So i tried the text mode,here also when the user name and password was typed the desktop session did not come.
                      
                       Now here is what i got as the output from the text mode (ie.genome terminal as is commonly called,i suppose)


          Ubuntu 9.10 sanjay-desktop tty1
          sanjay-desktop login:
          password:
          Last login:Thu Apr 29 11:10:09 EDT 2010 on tty1
          Linux -sanjay-desktop 2.6.31-20-generic #58-ubuntu SMP 
          Fri Mar 12 05:23:09 UTC 20 10 i686
          To access official ubuntu documentation,please visit:
          htt://help.ubuntu.com/
          0 packages can be updated.
          0 updates are security dates.
           sanjay@sanjay-desktop:~$_
 
                   This was the out put. Now what should i do in order to log in quickly? Kindly help.


Well, what I meant was for you to type

Ctl-Alt-F7 *AFTER* you log in on the text mode Ctl-Alt-F1

I'm sorry for not being more clear. That should work for you? Will it not?

**EDIT**

The system DID log you in on the text mode (I can see that from your output). Simply leave that and go to the graphical again using the Ctl-Alt-F7

---

### Post by sanjaypothen on 2010-04-30
> **Geoff918 said:**
> Well, what I meant was for you to type

Ctl-Alt-F7 *AFTER* you log in on the text mode Ctl-Alt-F1

I'm sorry for not being more clear. That should work for you? Will it not?

**EDIT**

The system DID log you in on the text mode (I can see that from your output). Simply leave that and go to the graphical again using the Ctl-Alt-F7

I did go now like that.(crtl-alt-f1 then went to crtl-alt-f7) But still i could not log in.
 
can anybody help with a correct answer.? please.

---

### Post by sanjaypothen on 2010-04-30
> **_0R10N said:**
> To log in from a terminal, when the log in screen appears hit Ctrl+Alt+F1 (or f2...) then you'll a enter in text mode. You'll be prompt for your user and password. To get back to graphical mode you must hit Ctrl+Alt+F7.

Well, back to our problem now. I googled it and I've found two alternatives:
First:
```
chmod 700 /tmp/gconfd-$USER/
```If that doesn't solve the problem, then deleting the following folder should work. I strongly recommend to make a back up of it, so you can easily go back if something goes wrong.
```

cp -r ~/.dbus/session-bus ~/.dbus/session-bus.bak
rm -rf ~/.dbus/session-bus

```Kind regards!

_0R10N >>

Pl. note that when i gave the input:  chmod 700 /tmp/gcogd-$USER/
the output was: chmod: can't access '/tmp/gcofd-sanjay/' :No such file or directory.

I have typed the second alternative,but no success.
 Input given: cp -r ~/.dbus/session~/.dbus/session-bus.bak
                   rm -rf ~/.dbus/session-bus
Output was:cp:can't stat '/home/sanjay/.dbus/session-bus"/.dbus/session-bus.bak':No such file or directory.
                 cp:can't stat 'rm':No such file or directory. 

Now what should i do? pl, help.

---

### Post by sanjaypothen on 2010-05-01
Somebody pl.help me?

---

### Post by Silent Warrior on 2010-05-02
You seem to have left out a space in the 'cp'-command, but then rm wouldn't complain about it being missing... Did you enter them separately, not just as one single commmand, as written, without && in between?

Difficult... Is your ethernet-cable ok? (Just going off on a tangent - NFS is AFAIK Network File System, designed for remote access. Hence you'd be in trouble, if your HD is remotely accessed and your connection is iffy. Why did you pick NFS over EXT*, anyway?)

---

### Post by sanjaypothen on 2010-05-02
[QUOTE=Silent Warrior;9215657]You seem to have left out a space in the 'cp'-command, but then rm wouldn't complain about it being missing... Did you enter them separately, not just as one single commmand, as written, without && in between?

Difficult... Is your ethernet-cable ok? (Just going off on a tangent - NFS is AFAIK Network File System, designed for remote access. Hence you'd be in trouble, if your HD is remotely accessed and your connection is iffy. Why did you pick NFS over EXT*, anyway?)[/QUOTE
 

I left space between rm and also between rf.The rest is a single command.The cp is as follows.
 cp(space)-r(space~/.dbus/session-bus~/.dbus/session-bus.bak
 rm(space)-rf(space)~/.dbus/session-bus.

I do not understand what you mean by && in between? Your second paragraph also i did not understand.(if you asking if it is networked? then  my answer is: No.My machine is single only; it is not connected remotely  also.I have not connected with anybody.
pl.help me solve this problem.

---

### Post by Silent Warrior on 2010-05-02
For the 'cp'-command to work, it HAS to look like this, EXACTLY:
```
cp -r ~/.dbus/session-bus ~/.dbus/session-bus.bak
```
The command not only takes a file to copy, you also need to specify where to copy it to. This is, however, just a way to back up your .dbus/session-bus. And the && in between is used to separate commands, if you ran them on a single line, then looking like so:
```
cp -r ~/.dbus/session ~/.dbus/session-bus.bak && rm -rf ~/.dbus/session-bus
```
Since your output says that cp can't "stat rm", I'm pretty sure you entered the command wrong. Copy and paste this exact line into your terminal if you can, otherwise type it and double-check that you get all the spaces and &s. (&& in between tells the terminal to run the first command, THEN run the next command. On my update-spree, I sometimes use a command including four &&-separations - near automation, assuming there's no complication.)
And I asked about remote connection because that's the only reason I can think of to use NFS specifically over EXT3/4, but that could be down to personal preference. It shouldn't actually matter, I suppose. Have you looked at any troubleshooting guides for NFS, though?

---

