---
title: "WTF who is root and why does he own my computer"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by clay woodruff on 2009-11-19
ok i installed linux 9.10 and after downloading my nvidia drivers i cant set my resolution higher than 640x480. after searching for the fix i try and access my root files and i get a error message that i'm not the owner some **** named root is. so who the **** is root and how did he get in my computer, i'm almost ready to dump this piece of **** OS and go back to widows. ****** OS has more bugs than a whores snatch

---

### Post by bodhi.zazen on 2009-11-19
[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by NoaHall on 2009-11-19
> **clay woodruff said:**
> ok i installed linux 9.10 and after downloading my nvidia drivers i cant set my resolution higher than 640x480. after searching for the fix i try and access my root files and i get a error message that i'm not the owner some **** named root is. so who the **** is root and how did he get in my computer, i'm almost ready to dump this piece of **** OS and go back to widows. ****** OS has more bugs than a whores snatch

I know the answer to your "problem", but I'm not going to help you due to the way you spoke. Please address your problems in more decent manner in the future.

---

### Post by juancarlospaco on 2009-11-19
The problem is Layer 8 on the OSI model.

---

### Post by wojox on 2009-11-19
+1 NoaHall

NO Help For You!!!

---

### Post by herbertportillo on 2009-11-19
'Root' is the superuser which has the privileges to access all the components of the operating system. The reason the operating system is designed that way is because it's a security issue and protects against viruses and adware/malware/spyware infecting the computer. It's actually a much more practical system than Windows.

But to change any setting that you are not allowed to change as a regular user and not the superuser, use the 'sudo' command in the terminal. Or, if you're in the GUI and you need permission to perform a task or change a setting, type in your system password.

---

### Post by Shhnap on 2009-11-19
> **juancarlospaco said:**
> The problem is Layer 8 on the OSI model.

Lol.

I'm pretty sure that he's trolling too. Somebodies probably already reported him. And, should he not be trolling, I wish I was there when he figures out that he himself is infact root. Just one of those priceless moments.

---

### Post by openuniverse on 2009-11-19
> **clay woodruff said:**
> ok i installed linux 9.10 and after downloading my nvidia drivers i cant set my resolution higher than 640x480. after searching for the fix i try and access my root files and i get a error message that i'm not the owner some **** named root is. so who the **** is root and how did he get in my computer...

the onion makes money from stuff like this. if there's any chance he's serious (no one will ever manage to convince me he is) i honestly sympathize, despite the rudeness. if he read the onion or enc. dramatica, and understood the answer, he'd have to appreciate how funny this is. i was just saying that windows isn't a fix for anything, and i meant it. this guy needs a mac. (i like macs. won't buy one, but they're as nice as proprietary anything else.)

---

### Post by clay woodruff on 2009-11-19
to the admin. i'm sorry i spazzed out but this is driving me crazy. its one thing after another. so i apologise. i beg your forgiveness. ok so juan i have no clue as to what that means i'am a totally new to all this and rather ignorant when it comes to anything other than pressing the start button. i build houses and probably fell on my head one to many times

---

### Post by blueridgedog on 2009-11-19
Linux is very different that Windows and little of your experiences will translate over.  You have picked a good version (distro) of Linux to learn on though.  The OS and its roll in true freedom and equal access to computing technology around the globe is outstanding.

One thing you will need to do is bring a willingness to learn and participate in that learning.  Your post (language and tone included) is either indicative of an attempt to troll these forums or of a small amount of patience for the process. It the later, then you are in for a rough time.

For now, I suggest some light reading:

[http://linuxmafia.com/faq/Essays/smart-questions.html](http://linuxmafia.com/faq/Essays/smart-questions.html)

---

### Post by NoaHall on 2009-11-19
Right, okay. Thank you for being polite. 

Now, are you running 9.10 (karmic) or 9.04(jaunty)?
If jaunty, can you post the output of "cat /etc/X11/xorg.conf"

Are you using the driver from System -> Admin -> Hardware Drivers?
If not, use the one from there.

---

### Post by openuniverse on 2009-11-19
> **blueridgedog said:**
> Linux is very different that Windows and little of your experiences will translate over.

especially at first. when you're an experienced user, you'll be able to start using a lot of that knowledge again- well, at least the parts of it you still care about.

---

### Post by bodhi.zazen on 2009-11-19
> **clay woodruff said:**
> to the admin. i'm sorry i spazzed out but this is driving me crazy. its one thing after another. so i apologise. i beg your forgiveness. ok so juan i have no clue as to what that means i'am a totally new to all this and rather ignorant when it comes to anything other than pressing the start button. i build houses and probably fell on my head one to many times

The link I gave you will explain how root works in detail.

You are otherwise forgiven, I understand it is easy to become frustrated when your OS is not working. Please take care in the future.

I am going to close this thread now so as to reduce the flames. Feel free to start a new one if you have questions after reviewing the link and hopefully the new thread will go better for you as I am sure you learned a lesson on this thread as well ;)

---

