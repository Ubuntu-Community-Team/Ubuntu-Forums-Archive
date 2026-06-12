---
title: "Turning off all this admin security?"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-13
It just gets a bit annoying when I want to copy something somewhere that requires higher permission (sudo)
so then I have to go sudo nautilus and copy the files in.
Is there a way to turn off or automatically authorise everything so I can pretty much do what I want, install what I want without UAC like prompts or errors saying I need sudo access?

---

### Post by shifty_powers on 2009-06-13
yes, but you won't find out on the forums....

---

### Post by hayden92 on 2009-06-13
Hello Gp,

This question gets asked a lot, often by Windows users who are used to having administrative control of the computer all the time.

This is a safety measure to secure Linux, and it works fantastically! Logging in as root is NOT recommended

---

### Post by donkyhotay on 2009-06-13
What you're describing is known as 'running the computer as root' a.k.a. 'windows style security' a.k.a. 'a really @#$%ing bad idea'. Running your computer as root is so dangerous and such a bad idea that it is against the forum rules to explain how to do it. It's assumed that if you don't have the knowledge to figure it out on your own you don't have the knowledge to accept the risks associated with it. On the other hand it's assumed if you do have the knowledge to figure it out on your own then you're knowledgable enough to understand the risks. In my opinion the risks are *NOT* worth the convenience of typing sudo every so often and I agree completely with the forum policy. Security is there to protect you, use it.

---

### Post by H2SO_four on 2009-06-13
doesn't sudo or sudo su last for about 15 min? I can't recall what the default time is.  wouldn't that work fine?

---

### Post by QIII on 2009-06-13
Easy to teach someone to employ a 40lb cratering charge.

Hard to teach him how not to blow himself up.

---

### Post by Gp. on 2009-06-13
What is all this protecting me from exactly though?
Like why is logging in as root dangerous?

---

### Post by loomsen on 2009-06-13
Yep, true.

Usually you don't have to move *something somewhere*. Your path (or more appropriate the path of the current logged in user) will be included for most applications-specific settings. So, if you take a look at your home directory, you'll notice some hidden files and folders. Files ending on *rc are configuration files.

So you won't have to edit the bashrc located in /etc, but rather the one inside your home directory and it will override the default values. This is default for most apps you'd want to change settings of.

Plus, you won't lose anything if you bork up somehow, just remount your home partition (which I assume you have) in case of a reinstall and you'll be set up as before (after installing the respective apps.)

What's even more important, don't place files inside any users home as root. Every created file, no matter where it is, will have root:root ownerships, if you create files as root inside your home folder you are very likely running into related problems, till gnome will refuse your login (if you folders permissions changed, for example)
This is easy to fix, but if you're not 2 experienced it will force you to reinstall your OS most likely. 

So, let it be. You don't need supercow powers (only for very few actions, ubuntus config is pretty permissive anyway)

If you need to change a file you don't have write permissions on, copy it as a normal user to somewhere inside your home and edit/change/<place your action here> it, save it, and then only copy it to where you want it to be as root. Don't stay logged in as root permanently, as it can affect files which aren't obviously affected.

---

### Post by ad_267 on 2009-06-13
> **Gp. said:**
> What is all this protecting me from exactly though?
Like why is logging in as root dangerous?

Because running an application as root gives the application full access to your whole filesystem. Why do you want to copy files outside your home directory anyways? Usually you're doing something wrong if you're doing that a lot.

---

### Post by theozzlives on 2009-06-13
> **Gp. said:**
> What is all this protecting me from exactly though?
Like why is logging in as root dangerous?

People in the cold hard world with malicious intent.

---

### Post by QIII on 2009-06-13
> **theozzlives said:**
> People in the cold hard world with malicious intent.

Or people in front of a computer who sometimes find themselves saying "Ooops!"

---

### Post by loomsen on 2009-06-13
> **Gp. said:**
> What is all this protecting me from exactly though?
Like why is logging in as root dangerous?

You're using a UNIX based operating system now. UNIX has been developed in times when a CPU was the size of a house, and many users (usually in bigger companies) needed access to the central unit. To be able to keep users from damaging the whole computing unit, obviously permissions were needed.

If you want to place your media somewhere outside your home, for example into a folder /media, create a system user/group (a user which cant login, basically only holding permissions) and add your user to this group enabling the permissions you desire.

There are a lot of different ways to handle things. Just don't do to unconsidered things as root, DON'T make roots theme look like yours and so on.

---

### Post by jbruced on 2009-06-13
No offence meant here, but please forgive me if I don't understand why you are asking that question if:

#1, You have made over 200 posts to the Ubuntu forums , and
#2, You have access to the web, and it's wealth of knowledge

Viruses, malware, trojans, etc. unfortunately are part of the modern PC scene.

You may want to read this

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Hope it helps,

GL
Bruce

---

### Post by theozzlives on 2009-06-13
> **QIII said:**
> Or people in front of a computer who sometimes find themselves saying "Ooops!"

I once had to make a service call cause a girl used the DOS command attrib to hide her DOS. She couldn't unhide it because attrib was part of DOS and hidden!

---

### Post by QIII on 2009-06-13
One of the reasons Windows has the security problems it does is that people take their shiney new box home, create their account and run.

That account is an Admin by default.

So, while they are happily running as Admin, everyone and their brother is happily exploiting that vulnerability.

The way one SHOULD use windows:

Don't use the Admin account.  Create an account for a normal user.  Use that account.  Only use the Admin account when necessary.  Log of as Admin as soon as possible.

That is a good security practice in Windows.  

It is more or less enforced in Ubuntu.

---

### Post by Cheesemill on 2009-06-13
Read these:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Cheesemill

---

### Post by donkyhotay on 2009-06-13
Lets compare linux to windows for a moment. Linux has no viruses, windows is swamped with viruses. Why is this? Many people say it's because 'windows has more users therefore it gets targeted more'. While it is true that windows has more users the main reason it gets targeted is because it's easier to hit. Windows gives everyone full administrative access (basically the same thing as running as root) which means if you go to the wrong website or click the wrong link your computer is completely infected. With linux on the other hand if something were to get in it may mess up your personal files (everything within home) but actual core system itself remains safe unless you type in your password. And lets face it, if you go to [www.someshadywebsite.com](www.someshadywebsite.com) and suddenly get asked for your root password to install something you're not going to do it.


//edit: posted a little late, so pretty much what everyone else has said.

---

### Post by theozzlives on 2009-06-13
> **QIII said:**
> One of the reasons Windows has the security problems it does is that people take their shiney new box home, create their account and run.

That account is an Admin by default.

So, while they are happily running as Admin, everyone and their brother is happily exploiting that vulnerability.

The way one SHOULD use windows:

Don't use the Admin account.  Create an account for a normal user.  Use that account.  Only use the Admin account when necessary.  Log of as Admin as soon as possible.

That is a good security practice in Windows.  

It is more or less enforced in Ubuntu.

In Windows, it helps to rename the Administrator account, and disable Guest.

---

### Post by QIII on 2009-06-13
Usually not a good idea to create an account actually named "Admin".  That's like putting a bullseye on yourself.

But just creating your "Jane" account to begin with is Admin by default.

Create your initial Admin account with a somewhat secure name and a really secure password.

Create your "Jane" account as a normal user.  Use that account.

Definitely disable Guest.

Stupid idea from the start.

---

### Post by theozzlives on 2009-06-13
> **QIII said:**
> Usually not a good idea to create an account actually named "Admin".  That's like putting a bullseye on yourself.

But just creating your "Jane" account to begin with is Admin by default.

Create your initial Admin account with a somewhat secure name and a really secure password.

Create your "Jane" account as a normal user.  Use that account.

Definitely disable Guest.

Stupid idea from the start.

Oh well, I don't have to worry about editing security policies in Windows, cause I have it with Ubuntu.

---

### Post by scorp123 on 2009-06-13
> **Gp. said:**
>  Like why is logging in as root dangerous? root's powers are unlimited and GOD-like. That's simply too much power. And Unix-like OS are perfectly aware that they are just tools, and not supposed to tell the human in front of the system what to do or what not to do. So when the human in front of the system tells a Unix-like OS "wipe all my files, destroy all disks ... " then the OS will assume that this is precisely what you wanted and will execute that command without hesitation, without questioning your decision, without complaining .... Too bad if it was an accident. :D

So with root's God-like powers ... one stupid drag & drop over the wrong locations, one badly executed changing of user and file permissions (check the forums ... too many out there hosed their systems by executing commands as "root" they did not yet fully understand ...), one accidentally deleted file .....  And your system is hosed.

So that's why it is a bad idea to work as "root". You're only supposed to be "root" if you have something really important to do, like installing packages, installing updates, rebooting the system ... But you'er definitely not supposed to be in that account all the time.

---

### Post by presence1960 on 2009-06-13
by the way > sudo nautilus is not the way to run nautilus. Any graphical apllications should be run with gksu, i.e. > gksu nautilus

---

### Post by xavierp94 on 2009-06-13
> **H2SO_four said:**
> doesn't sudo or sudo su last for about 15 min? I can't recall what the default time is.  wouldn't that work fine?
Yes, it should

---

### Post by QIII on 2009-06-13
> **theozzlives said:**
> Oh well, I don't have to worry about editing security policies in Windows, cause I have it with Ubuntu.

Nice, ain't it?

Unfortunately, most of my clients use Windoze.

I make middleware and design database back-ends for secure web applications that handle literally billions of dollars of regular peoples' money.

I have actually found my self flabbergasted when I find that their DBAs use SQL Server username/login pairs like "sa"/"sa123456".

Why, oh why have I spent so much time creating a secure application for you when you just open the back door like that?

---

### Post by doas777 on 2009-06-13
> **Gp. said:**
> It just gets a bit annoying when I want to copy something somewhere that requires higher permission (sudo)
so then I have to go sudo nautilus and copy the files in.
Is there a way to turn off or automatically authorise everything so I can pretty much do what I want, install what I want without UAC like prompts or errors saying I need sudo access?

you shouldn't have to request admin elevation regularly. only when performing administrative tasks. mounting a disk is administrative. copying files and folders are not. if you are getting many prompts for access, then you are either trying to mess with file locations you should not be (except when performing administrative tasks, of course) or there is a problem with the ownership/permissions on the locations you are trying to access. 

I soooooo perfer sudo/gksu over UAC.

---

### Post by doas777 on 2009-06-13
> **xavierp94 said:**
> Yes, it should
but only for commands given from with the same shell context

---

### Post by donkyhotay on 2009-06-13
> **doas777 said:**
> I soooooo perfer sudo/gksu over UAC.

Agreed

---

### Post by H2SO_four on 2009-06-13
> **doas777 said:**
> but only for commands given from with the same shell context
I meant that the time provided for access to sudo permissions should be sufficient to do what you need, then your permissions go back to user.  I didn't mean in the sense of specific command for a situation.

---

### Post by aysiu on 2009-06-13
> **Cheesemill said:**
> Read these:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Cheesemill
Yes, especially the first link. Thread closed.

---

