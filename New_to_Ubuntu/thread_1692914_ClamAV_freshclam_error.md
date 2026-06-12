---
title: "ClamAV freshclam error"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by stookin on 2011-02-22
hi

I just installed clamav
Like in the tutorial described here [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

However when I use the command "freshclam" in terminal, it says:
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

wtf man

can anyone help?

I tried chmodding /var/log/clamav to 640 using the below command:
sudo chmod 640 /var/log/clamav

also I tried
sudo chmod 640 /var/log/clamav/freshclam.log

halp

edit: I am running Ubuntu 10.10

---

### Post by An Sanct on 2011-02-22
Have you opened the folder and checked the permissions on files?

try
sudo chmod 640 /var/log/clamav/freshclam.log

---

### Post by stookin on 2011-02-22
> **An Sanct said:**
> Have you opened the folder and checked the permissions on files?

try
sudo chmod 640 /var/log/clamav/freshclam.log


I have to do that.

I am now back on a windows computer because I crashed ubuntu two times in one day, the first day I tried it.

Also it does not boot at all anymore :s
When I start it gives multiple errors after logging in. one of them as I remember said something about Nautilus ? :s

whatever, windows ftw.

---

### Post by sydbat on 2011-02-22
Two questions...

1) How did you install Ubuntu? Was it a full installation in its own, separate partition? Was it a WUBI installation (as a "program" inside Windows)?

2) Why do you need a virus scanner in Linux? Are you running a mail or file server for Windows clients?

---

### Post by stookin on 2011-02-22
It's my old pc from 2004. It used to run windows, but it got slow and windows got rigged with malware and ****.

so I heard linux was good, gave ubuntu a try.
Downloaded the newest iso from the website, version 10.10. downloaded pendrive linux and made a USB bootable.

I installed it, worked perfectly however (im accustomed to windows) so I wanted to install a firewall and virusscanner just in case. I know linux ppl say how it's not necessary but I figured it couldn't hurt.

also I downloaded a shitload of add ons for firefox, to make it even more safe.
also I was ******* around in ubuntu cuz I was curious how it all worked. I got annoyed because everything I wanted to install was such a hassle (eg, sudo blabla for everything and every ******* minute it asked for my 24 character password. It kinda felt like in order to install a simple program like moblock, you need a ton of other programs like aptitude for example :s and not even that, you must also know how to configure it in the terminal plus you must know what **** is before I even ******* heard about it.
so basically I was googling the whole time while installing something simple.
in windows you just download something, press next a few times, and it works.
in ubuntu you must follow a ******* tutorial in order to install even the simplest ****.

It srsly ****** me off man.

other than that it worked pretty neat. also I have the impression it's a little more stable than windows and maybe even a little faster.
but everything is such a hassle man. I hear a lot of linux people say hur dur im lazy so i just do sudo 93u42kwj09i32

but i dont think linux is for lazy people. I think linux is for people who love puzzling and figuring **** out.
in my opinion that's a waste of time, Id rather spend my time outside or something.

feel free to hate me.


also I think I know how I ****** ubuntu up. When i installed it asked if i wanted to make an autologin?
so I said no, but the last time I booted ubuntu I was looking around in my profile and I could see that I could still change the setting to "not ask for password when booting" or something liek that
so I did that, without entering a password. and basically I could boot ubuntu, click on my username and it would boot with a shitload of errors and eventually it just didn't do anything (couldnt even see a menu or anything)
the only thing that worked was to see that purple background (yay) and ctrl+alt+delete with all it's functions (hibernate, restart, shutdown etc.)

anyone know how to fix that?

also hope to have answered your questions sufficiently

best regards

edit: I did a full install and a format. So only ubuntu was running on that machine, windows was formatted.
edit: I have another question, is there a safe mode option in ubuntu? I tried F8 and F7 while booting in ubuntu. Bot other than flickering the screen it did nothing.
just curious

edit: also why does it say I have 3 beans on this forum when I can see I already have 5 (green ones)
something doesn't make sense yo :s
also whatsup with the beans anyway man?

---

### Post by sydbat on 2011-02-22
> **stookin said:**
> <snip>Please watch your language. As you can tell, most of  your swearing has been ***'d. If you continue, two things will happen - 1) No one will help you. 2) You will be banned.

Now, if you would like to interact in a civil manner, we can try and help you. Please rewrite your post.

---

### Post by stookin on 2011-02-22
> **sydbat said:**
> Please watch your language. As you can tell, most of  your swearing has been ***'d. If you continue, two things will happen - 1) No one will help you. 2) You will be banned.

Now, if you would like to interact in a civil manner, we can try and help you. Please rewrite your post.

oh ok thanx

---

### Post by jre on 2011-02-23
About you having to type your password frequently for sudo:
In Linux normal users don't have the rights to change your whole system. That's a policy and that is good. And this is why sudo exists and asks for your password.

But sudo remembers when you have typed your password for a certain time amount. So just use the same terminal in that you typed your password, and you won't have to type the password for every sudo.

Furthermore I'd suggest you read something like a beginners guide for Linux user

---

