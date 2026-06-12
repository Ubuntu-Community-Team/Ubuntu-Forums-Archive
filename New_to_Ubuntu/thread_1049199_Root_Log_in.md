---
title: "Root Log in"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by gotvols on 2009-01-24
Re: How do I login as root?
Right, logging in as root is dangerous and quite stupid.
sudo should do fine.
__________________
HP Pavillion a1310y with DVD rom and CD Burner, Intel Pentium 4HT, 1 GB memory, 80 gig HD my testimony
remember kiddies: sudo rm -rf= BAD!, if someone tells you to do this, please ignore them unless YOU WANT YOUR SYSTEM WIPED 

You know what is quite stupid is the fact that someone ask a simple question and this was the response. They didn't answer they just posted their opinion. I've noticed in Linux people are scared to use root. When basically it's just like being the administrator in Windows.  I'm sure people have used windows before on their home computers.  Why would I want to go through entering different commands when if I was root I would only need to use one command.  It's my computer if I want to jack it up than let me I'll just reload it if I mess it up. If someone ask how to log in as root don't reply like the above person did to someone in another tread that got closed.  The tread didn't have the solution to the person's problem.  All it had was reasons why they shouldn't log in as root. Give them the answer.  If you don't know the solution to the question than don't reply.  I want the instructions for logging in as root.  Like stated above if you are going to just whine that I shouldn't log in as root please don't post a response.  I know it can be done I just need the commands.  I'm tired of using 10 commands to do 1 command.

---

### Post by yeats on 2009-01-24
Ubuntu disables root login by default.  You might want to reference this page:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Does that help?

---

### Post by eagle416 on 2009-01-24
if you want root in a particular program (GUI), type "gksudo" before the name of the program. i.e.

```
gksudo nautilus
```

Nautilus will open, and you are superuser in that program. Theoretically you could start the desktop manager this way, which will make you really powerful.

---

### Post by sisco311 on 2009-01-24
We can't help you. It's against the [forum policy]("http://ubuntuforums.org/showthread.php?t=716201").

Google is your friend.;) Good luck.

---

### Post by yeats on 2009-01-24
eagle's right - I was thinking of terminal-based commands, not the graphical interface.

---

### Post by gotvols on 2009-01-24
> **chrissharp123 said:**
> Ubuntu disables root login by default, but if you do 

```
sudo su
```

you will become root within your normal login session.

Does that help?

That gave me root access in terminal.  I know how to do that.  I want to be able to log in as root so I don't have to enter sudo before I try to do something.

---

### Post by KIAaze on 2009-01-24
> **sisco311 said:**
> We can't help you. It's against the [forum policy]("http://ubuntuforums.org/showthread.php?t=716201").

Google is your friend.;) Good luck.
Ah, I was just about to post a link to how to enable graphical root login. I shall respect the forum policy then. ^^

P.S: Don't PM me, use Google.

And sudo + terminal root login really is more than enough. If you need 10 commands to run 1, you're doing something wrong.

---

### Post by The Cog on 2009-01-24
Using the command **sudo su** or **sudo -i** will raise that particular command prompt window to being a root login prompt.

Using the command **gksu nautilus** will give you a file explorer window that has root priviledge over the whole filesystem. 

Between the two of them, they should be all you need. You have the ability to become root whenever you need that power, but it's not automatically there on averything you do.

---

### Post by AndyCooll on 2009-01-24
While I do not condone such comments, for folk should put their point across in a more constructive manner, you might want to read [this]("https://help.ubuntu.com/community/RootSudo") for the reasons why Ubuntu takes the approach it does, and hence why you get the type of comment you quoted. 

:cool:

---

### Post by gotvols on 2009-01-24
> **sisco311 said:**
> We can't help you. It's against the [forum policy]("http://ubuntuforums.org/showthread.php?t=716201").

Google is your friend.;) Good luck.


Really. WoW.  Against the policy to help someone login to a free open source system as the "Administrator". In which that is all root is.

---

### Post by yeats on 2009-01-24
gotvols -

I understand your frustration, and it sounds like you have enough to get things done, but this is the way the forums choose to address the issue and the way Ubuntu handles security.  Perhaps Debian, or another Linux distro with a more permissive scheme in this regard will serve you better. :-)

---

### Post by KIAaze on 2009-01-24
There are a lot of other GNU/Linux forums out there, you know...
Some distributions even default to a root login.
ex: [http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)
edit: about backtrack as OS:
[http://carnal0wnage.blogspot.com/2007/08/backtrack2-is-not-operating-system.html](http://carnal0wnage.blogspot.com/2007/08/backtrack2-is-not-operating-system.html)
[http://www.cutawaysecurity.com/blog/archives/category/backtrack](http://www.cutawaysecurity.com/blog/archives/category/backtrack)

Perhaps if you could tell us what you are trying to do that requires lots of commands when not running as root, we might help you simplify the process.
ex: Put all commands into a script and run the script as root.

---

### Post by sisco311 on 2009-01-24
> **gotvols said:**
> Really. WoW.  Against the policy to help someone login to a free open source system as the "Administrator". In which that is all root is.

The first account created on the system is the "Admin" account.
You can use sudo/gksudo to run apps as root.

> **[SIZE="4"]Rationale[/SIZE]**
We believe in and offer technical support for Ubuntu's default security model, which uses sudo for temporary privilege escalation on particular tasks for particular users with a password authentication. Generally speaking, those who desire a graphical root login fall into one of three categories:
Users new to Linux who receive an error message telling them they need to be root in order to execute a certain command or who are trying to follow a tutorial for a non-Ubuntu Linux distribution in which they are instructed to log in as root.
Users new to Ubuntu who have experience with other *nix systems in which they are used to logging in as root.
*nix experts who have very specialized tasks that can be accomplished only through a root login.
The first group (users new to Linux) simply needs to be educated about how Ubuntu works, since all they want to do is accomplish a certain task they believe requires a root login. Once they realize the task can be accomplished more simply with Ubuntu's sudo, they should have no reason to still want a root login.

The second group (Linux vets new to Ubuntu) may theoretically know about sudo but is acculturated to logging in as root. Many of our forum staff and forum members started out this way as well and disliked sudo at first. However, once we got used to sudo, we liked it better than the traditional root/user model, and realized there were both security and usability benefits to Ubuntu's security model. In other words, give Ubuntu a fair chance.

The third group (experts who know of special situations that require a root login) definitely does not need a root login tutorial. If they're really experts, they can easily figure out on their own how to enable a root login. And if they can't figure it out, perhaps they're not the experts they think they are.

To sum it up, if you can't figure out how to log in as root in Ubuntu, then you should be educated on how to use Ubuntu's sudo security model properly; and if you can figure out how to log in as root in Ubuntu and want to, then you certainly don't need a tutorial on how to do it.

Variations on the second and third groups are those who falsely believe sudo security model to be less secure than the traditional root/user model. You can find out more about Ubuntu's reasons for using sudo and the pros and cons of both security models here:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by krzysz00 on 2009-01-24
even though you SHOULDN'T log in as root if you REALLY want to here's what you do

First open a terminal and type:
```
sudo passwd root
```
and set a root password.
If you just want to be able to login to a virtual console (Control+Alt+F*n*)
If you want a desktop session at root (very, very, very bad idea the login window will even warn you about it) you must:
1. Go to System->Administration->Login Window
2. Type your password
3. go to the "Security" tab
4. Check "Allow local system Administrator ligon"
5. Hot OK

Of cource if you're looking to set the root password to ```
su root
``` just use Ubuntu's ```
sudo -i
``` and type **your** password

---

### Post by sisco311 on 2009-01-24
krzysz00 please read the [forum policy]("http://ubuntuforums.org/showthread.php?t=716201") and edit your post.

---

### Post by diablo75 on 2009-01-24
:popcorn:

---

### Post by damis648 on 2009-01-24
I'm sorry you are frustrated with your problem, however root is quite different from administrator in Windows in a few ways. Administrator is what owns the system files, which is correct, however it still does not have the power to delete important system files. Try it, it will simply tell you that you cannot delete it because it is in use. Root has that power, and has all power to do anything. People have logged into the root account for two minutes and royally screwed up their systems. I should know, I am one of them. Please just stick to sudo and gksudo.


> **sisco311 said:**
> krzysz00 please read the [forum policy]("http://ubuntuforums.org/showthread.php?t=716201") and edit your post.

That would be wise.

---

### Post by yeats on 2009-01-24
I agree with damis - I think it would be better to view this from the "What do I need to actually get done as root?" perspective rather than the "My rights are being violated" one.  Of course, it looks like you're getting an awful lot of unsolicited advice here :-).

---

### Post by boof1988 on 2009-01-24
> **chrissharp123 said:**
> gotvols -

I understand your frustration, and it sounds like you have enough to get things done, but this is the way the forums choose to address the issue and the way Ubuntu handles security.  Perhaps Debian, or another Linux distro with a more permissive scheme in this regard will serve you better. :-)

This is the funny thing...

I am playing around with Debian... to install any software or updates etc., it seems that I *HAVE* to log in as root.  In-Other-Words I have to log out of normal user and log in as root.

That is the big benefit (IMHO) of using sudo etc. (Ubuntu security scheme).  I get security of daily/routine use as a normal user so it's hard to break stuff.  And the handiness of root access without logging out to install applications.

---

### Post by yeats on 2009-01-24
> I am playing around with Debian... to install any software or updates etc., it seems that I HAVE to log in as root.

Yes - Debian does not have sudo configured by default, though you can set it up that way (which is essentially what Ubuntu is - Debian "sid" with a more restrictive permission scheme) :-).

---

### Post by Coder543 on 2009-01-24
> You know what is quite stupid is the fact that someone ask a simple question and this was the response. They didn't answer they just posted their opinion. I've noticed in Linux people are scared to use root. When basically it's just like being the administrator in Windows. I'm sure people have used windows before on their home computers. Why would I want to go through entering different commands when if I was root I would only need to use one command. It's my computer if I want to jack it up than let me I'll just reload it if I mess it up. If someone ask how to log in as root don't reply like the above person did to someone in another tread that got closed. The tread didn't have the solution to the person's problem. All it had was reasons why they shouldn't log in as root. Give them the answer. If you don't know the solution to the question than don't reply. I want the instructions for logging in as root. Like stated above if you are going to just whine that I shouldn't log in as root please don't post a response. I know it can be done I just need the commands. I'm tired of using 10 commands to do 1 command.Running as root is not like running as administrator in windows. The account you first created when you installed ubuntu is like running as administrator in windows. Running as root in ubuntu is like *being* windows. It is *extremely* risky and holds few if any benefits. That is why it is disabled by default. You have infinite power and zero limitations. Not only that, but any programs you run have that same power. Which means any mistakes you make will directly affect the entire system without any warning or authentication. Running as root in a terminal is about as far as you should go. Logging into root is not advised for any reason that I can think of. Just because you can doesn't mean you should. Seriously, you have google if you are so inclined to be Mr. All-Powerful on your computer but I don't recommend it. And I must say that someone must seriously be lacking in intelligence to say "I'm tired of using 10 commands to do 1." let's count *"sudo COMMAND"* that sounds like 1 command to do 1 command.

---

### Post by boof1988 on 2009-01-24
> **chrissharp123 said:**
> Yes - Debian does not have sudo configured by default, though you can set it up that way (which is essentially what Ubuntu is - Debian "sid" with a more restrictive permission scheme) :-).

Thanks for the info... will investigate further...

...And now back to you regularly scheduled thread...

---

### Post by sisco311 on 2009-01-24
> **boof1988 said:**
> This is the funny thing...

I am playing around with Debian... to install any software or updates etc., it seems that I *HAVE* to log in as root.  In-Other-Words I have to log out of normal user and log in as root.

That is the big benefit (IMHO) of using sudo etc. (Ubuntu security scheme).  I get security of daily/routine use as a normal user so it's hard to break stuff.  And the handiness of root access without logging out to install applications.

EDIT: I'm super slow today :)

Well, it's a little off topic, but anyway...

You can use su/gksu on Debian in the same way you use sudo/gksudo in Ubuntu.

To run a command as root:
```
su -c command
```
To start a root shell:
```
su -
```

And of course, if you want, you can install sudo on debian.

in:
```
gksu-properties
```you can set the Authentication Mode to su or sudo

---

### Post by boof1988 on 2009-01-24
> **sisco311 said:**
> EDIT: I'm super slow today :)

Well, it's a little off topic, but anyway...

You can use su/gksu on Debian in the same way you use sudo/gksudo in Ubuntu.

To run a command as root:
```
su -c command
```
To start a root shell:
```
su -
```

And of course, if you want, you can install sudo on debian.

in:
```
gksu-properties
```you can set the Authentication Mode to su or sudo

Thanks for the info.

I find it very difficult to find the information needed (by searching/googling etc).  So I really appreciate help like this.

Thanks Again.  :p

---

