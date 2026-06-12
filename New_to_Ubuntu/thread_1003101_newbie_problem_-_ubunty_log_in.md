---
title: "newbie problem - ubunty log in"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Dee393 on 2008-12-05
Good evening Forum

I am completely new to linux and ubuntu.
yesterday i installed a disk from a computer mag
with linux abuntu onto my laptop.
i have a sony viao running vista.
it is a 160 harddrive and i used 10gb for 
the installation of ubuntu.
(the disk did the partition)

anyway being new to linux and not too great on 
cpmputers anyway i basically didnt really know what
i was doing. lol

I'll get to the point.

1. when i boot up to ubuntu i need to enter my
user name and password.
[I]i dont know my user name!
i remember being asked to enter a password but not a user
name. Is there any way i can find out what my user name is
so i can actually log in???
i have tried using the name i gave to the laptop
incase it choose this automatically
but that does not work and leaving the username blank
doesnt work either![/I]

2. now that i have given ubuntu a section of my hard drive
is there any way to uninstall it so that the partition
is no longer there.
( i am not too worried about this problem if i can 
log into ubuntu as i want to use linux.)

I hope you can understand my these problem.

i would be very greatful for any help that any member
can give me.

many thanks in advance.

Dee.
:)

---

### Post by handydan918 on 2008-12-05
Well, Dee, if a textbox pops up and asks you to enter your name, Dee, what do you input, Dee?

Just a thot.

):P

---

### Post by taurus on 2008-12-05
If you installed Ubuntu on it own partition (instead of within windows), you can try to boot Ubuntu to recovery mode from the GRUB menu.  When you first turn on your computer, you would see a message from your mobo and then you would see the word GRUB.  You have 3 seconds to press the ESC key to bring up the menu.  Move down to recovery mode and hit Enter to boot from it.  Once it's finished booting, look to see what is your username with this command.

```
ls -la /home
```
And if you are not sure about the password, you can change it from there to.  Assuming your login name is dee,

```
passwd dee
```
Now, you can reboot your machine with

```
shutdown -r now
```

p.s.  Remember, Unix/Linux is case sensitive so upper case letter is not the same as lower case letter.

---

### Post by Dee393 on 2008-12-05
[B]thank you Taurus
i will give that a go and see how i get on
thanks for the reply.[/B]



**handydan918** - like i said i dont know the user name
and none i have tried worked!
It was asking for a username entered at installation
not a new user name.!!!
so entering 'Dee' wouldnt have worked.

---

### Post by ash_nug on 2008-12-05
> **Dee393 said:**
> [B]thank you Taurus
i will give that a go and see how i get on
thanks for the reply.[/B]



**handydan918** - like i said i dont know the user name
and none i have tried worked!
It was asking for a username entered at installation
not a new user name.!!!
so entering 'Dee' wouldnt have worked.

I think what handy dan somewhat more articulately explained was that at some point you did indeed type your user name, and there is a strong possibility you entered your 'name as 'dee'.

---

### Post by newbee70 on 2008-12-06
> **Dee393 said:**
> [B]thank you Taurus
i will give that a go and see how i get on
thanks for the reply.[/B]



**handydan918** - like i said i dont know the user name
and none i have tried worked!
It was asking for a username entered at installation
not a new user name.!!!
so entering 'Dee' wouldnt have worked.


Welcome to the forums Dee, it's actually a fun place to hang out and learn about how to use Ubuntu,the many commands there are, and the different ways of using/ combining them.

I'm a noob 2 so I ask my share of questions, and for those that want to poke a little fun at us: let them because at one time they were just like us. Wet behind the ears and wanting help.

---

### Post by Frogbarf on 2008-12-06
It's one of Ubuntu's failings (though not a show-stopper) that when the install process asks you for a user name, it doesn't emphasize that that will be the name of your privileged admin account.

It would be better if lights flashed and bells rang and the screen said in big letters [B]DON'T YOU DARE FORGET THIS USER NAME AND ITS PASSWORD!!!
[/B]
For the benefit of the OP, a further tip. Don't use the admin userid for routine work. Reserve it for system maintenance work.

The first time you log in, the very first thing to do is go into System > Administration > Users & Groups and set up at least one ordinary unprivileged user id (more if others will be using the system), and make it a habit to use that id, not the admin one, for your day to day work.

Also keep in mind that when you see advice that says "Open a terminal window and enter the command *sudo something or other*", you need to be logged in as the admin user for that to work. Sudo doesn't work if you are logged in as an ordinary unprivileged user.

Another tip: Linux is a true multi-user, multi-processing system so if you switch to another id, the previous one is still alive and kicking. I have a friend who stays with me for a few days every six months or so, and I've set up an account for him so his browser & email settings are intact from visit to visit. One time I'd logged on and his session still had the browser open. Surprise, surprise, when Earthlink made the browser play a sound to say a new mail had arrived.

Actually, I thought it was pretty cool. Or kewl if you prefer!:D

Welcome to Ubuntu.

---

