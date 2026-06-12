---
title: "What if I gave my root password to anyone?"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by madmax.santana on 2009-12-21
Can someone hack into my system if I gave him my root password? And how would I know if anyone has been stealing anything from my system using my root password? The system stores the log of last login by root, but how to retrieve the log file?

---

### Post by Grenage on 2009-12-21
Yes they could, although it wouldn't really be hacking - you gave them the password.  Change your password.

/var/log/auth.log

---

### Post by presence1960 on 2009-12-21
> **madmax.santana said:**
> Can someone hack into my system if I gave him my root password? And how would I know if anyone has been stealing anything from my system using my root password? The system stores the log of last login by root, but how to retrieve the log file?

Giving someone your password defeats the whole purpose of a password. Change your password. See this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by snowpine on 2009-12-21
Ubuntu does not have a "root password" by default -- see here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Anyone with physical access to your computer can steal your data without leaving a trace. (For example, they could boot using an Ubuntu Live CD and copy your files to a thumb drive.) They do not need your password to do this. Or, they could boot into "recovery mode" and change your password. They could also just smash your computer with a hammer!

Physical access to your computer **is** root access. Lock your doors. :)

---

### Post by juancarlospaco on 2009-12-21
Then you give your PC to anyone...

---

### Post by fromthehill on 2009-12-21
[IMG]http://www.macrochan.org/images/R/B/RB55PJGLTZ7UXB3L5CN7LKEO436R7XFJ.jpeg[/IMG]

if you have installed anything that allows remote access you are screwed

---

### Post by Rex Bouwense on 2009-12-21
Once you give your password to someone, all they have to do is log onto your computer and copy your files to a flash drive.  Change your password, especially if you have confidential information such as bank statements or passwords to other accounts contained on it.  If you are concerned change all of your passwords.

---

### Post by snowpine on 2009-12-21
> **Rex Bouwense said:**
> Once you give your password to someone, all they have to do is log onto your computer and copy your files to a flash drive.  Change your password, especially if you have confidential information such as bank statements or passwords to other accounts contained on it.  If you are concerned change all of your passwords.

They don't need your password to boot with a Live CD and copy your files to a flash drive. They also [don't need your password to change your password]("http://www.psychocats.net/ubuntu/resetpassword"). :)

Don't store your passwords or banking information on a public computer, ever. If you are paranoid about this stuff, do your online banking from a Live CD... that way when you power down the computer, there is no trace.

---

### Post by sdpiowa on 2009-12-21
The only real way to prevent someone from stealing your data with a Live CD is to encrypt your file-system (which you can do, by the way).

---

### Post by madmax.santana on 2009-12-21
Oh man!!! Such a storm. I didn't give my password to anyone, noooope!!!
I was just asking buddies... Just for the prospect of security... Hahahaha!!!
Anyway, I agree with** snowpine**, root access is not "only" the password. It's a cocked gun (maybe virtual, see I am a James Bond fan :D) under your pillow and your vigilance.  ;)

And by the way, I don't have any CIA Confidential Records on my PC. What I have is a bunch of videos and images and fun stuff and my academic work. Anyone can ask me for those and I would give them copies and they don't have to labor for hacking into my system :D 
 However I am keeping some pictures of my[COLOR=Yellow] [COLOR=SeaGreen]secret sweetheart[/COLOR][/COLOR] in my PC and I would be really interested in keeping that from everyone!!! Hehehehehe ROFL

Thanks for the help. And also @**fromthehill**, I loved the image you posted... LOL Have a nice time guys...

_**P.S. I think I should have posted this in Community Cafe. Could an admin do that for me please?**_

---

### Post by madmax.santana on 2009-12-21
@**sdpiowa**
I was interested in encrypting but it was a bit tricky for me and I did not have time to learn details. I am studying Communication Systems Engineering so I have a background knowledge of encryption and stuff, but I shall go deep into it some time later. Thanks and TC

---

