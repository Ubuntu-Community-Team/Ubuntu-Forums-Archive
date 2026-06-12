---
title: "extreme NOOB question about Roots"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by cannon3fearless on 2010-01-17
I am extremely new to linux and ubuntu so please excuse my noob question but i just wanted to see if some body could give me some clarification....I understand that the root is supposed to be the admin user in linux and most time that is not your day to day account....now when i set up my ubuntu operating system i make a user name and account...is that my root account and should i make another user ...or is root made by default...if it is then how do i log in to it....if some body could explain it to me in simple terms i would GREATLY APPRECIATE IT as it will probably help me as well as any other noobies that are confused about it going into the future

---

### Post by forsaken_pariah on 2010-01-17
Yes, root is the "admin user", or what we call a superuser account. Default Ubuntu doesn't actually have a root account that you can log into. The account you create when you install Ubuntu is your everyday user account. To do anything as root, you need to use the sudo command.

---

### Post by audiomick on 2010-01-17
Hi. You don't need to do anything.
You are right that in Linux the root user (super user, root or whatever) is the only one who can do administrative tasks.

In Ubuntu, the root account is disabled by default.

Sounds illogical, but it isn't. There is a mechanism called "sudo"
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)
that Ubuntu invokes to take care of the root tasks.

What that means for your daily use is that when you try and do something that needs root privileges via the GUI, for instance start synaptic package manager, you will be asked for a password. 

The first user that is installed on a Ubuntu system is allowed to invoke this mechanism. Further users can be allowed to or not.

---

### Post by florus on 2010-01-17
Any command you need to run as root is entered into Terminal. Preceding the command with the command 'sudo' (short for superuser do) will cause Terminal to prompt for your password. Type your password in (which is not visible), and hit enter. Do read up on Terminal - it looks daunting, but is straightforward and a very useful and powerful tool.

---

### Post by quik_lives on 2010-01-17
How/where can we "read up on Terminal"? I'd really like to learn more about what can be done with command line.

---

### Post by SuperSonic4 on 2010-01-17
I'd use a search engine because there are thousands, if not millions, of things that can be done with the command line.

```
find ~/Music -name *.mp3
```

---

### Post by cannon3fearless on 2010-01-17
thanks a lot guys you cleared it up for me i got the pocket guide and im just walking through it with ubuntu so i can learn the basics b4 i learn command lines and stuff but i know wht that sude your talking about is and it makes sense the pocket guide didnt do alot as far as making it up...so basically ubuntu has simplified the root user so that you cant really mess anything up inless you know what your doing

---

### Post by teward on 2010-01-17
But be careful with the terminal, because while it is useful, you can do serious damage to your system if you use the wrong command.

---

### Post by SuperSonic4 on 2010-01-17
> **cannon3fearless said:**
> thanks a lot guys you cleared it up for me i got the pocket guide and im just walking through it with ubuntu so i can learn the basics b4 i learn command lines and stuff but i know wht that sude your talking about is and it makes sense the pocket guide didnt do alot as far as making it up...so basically ubuntu has simplified the root user so that you cant really mess anything up inless you know what your doing

No, it is still very easy to mess up by the user - it's security aspect comes from Joe Bloggs on the internet not being able to hack into the root account.

You can still bork your system using sudo and it's frighteningly easy - especially if you don't question what you're using sudo for. For example do you know what ```
sudo ln -s /home/user/script /usr/bin/script
``` does? (FYI: it places a symlink in /usr/bin of a script in your home directory).

The moral of the story is when using double check that you know why you're using it :p

---

### Post by cannon3fearless on 2010-01-17
thanks for the insight super sonic...that leads me 2 another question in ubuntu do they have a function where you can some how save a current setting or like how windows has where you can save a restore point just in case for some reason you mess somethin big up using sudo u can restore it to another restore point??

---

### Post by SuperSonic4 on 2010-01-17
I don't believe there is an automatic system restore by default but you can use *rsync* from the repos which backs up periodically to know knowledge. Since I'm lazy I simply cp files to another location when I remember

---

### Post by audiomick on 2010-01-17
This is true,
> **florus said:**
> Preceding the command with the command 'sudo' (short for superuser do) will cause Terminal to prompt for your password.

but this
> **florus said:**
> Any command you need to run as root is entered into Terminal. 
is not.

As I already mentioned, there are a number of functions in system> administration , like the synaptic packet manager, that invoke the sudo function. In these instances it is actually "gksu", which is a form of sudo appropriate for graphical applications.
You should always use "gksu", or "gksudo", which appears to be the same, for graphical applications.
Here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
is an explanation.
One example is using
```
gksu nautilus
```
to start the file manager to do file manipulations for which you need root privileges, or
```
gksu gedit
```
to start the editor to edit config files that belong to root.

As as already been mentioned, be very sure you know what you are doing with this stuff. You can kill your system. My motto is, if you get asked for a password, take 2 breaths and think before you go on.

---

