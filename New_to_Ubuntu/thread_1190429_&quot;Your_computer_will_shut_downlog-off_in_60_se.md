---
title: "&quot;Your computer will shut down/log-off in 60 seconds&quot;"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by kickwin on 2009-06-17
Whenever I click Shut Down I see a dialog saying the post title. Is it okay to just click shut down now option? Why is that 60 second wait there?

---

### Post by jenkinbr on 2009-06-17
just click it.

I think it's there to give you a bit of extra time to close apps or something.

Annoying if you ask me.

---

### Post by wpshooter on 2009-06-17
Hmmmmmmmmmmmmmm.  I have been wondering the same thing.  Perhaps it is there just in case the user might be too lazy to click on shutdown again !!!

But more likely it is there in case you intended to shutdown and then got distracted just after you initially clicked on the shutdown choice and say walked await from the computer or maybe for those of us that are getting senile.

---

### Post by powel212 on 2009-06-17
If you right click the shutdown, (power button), top right, you can select preferences then uncheck "show confirm dialogs..." then when you hit shutdown it won't wait the 60 seconds.

Powel

---

### Post by jenkinbr on 2009-06-17
Dang, I'm stupid!

(now for the system beep that annoys the hell out of me...)

---

### Post by ad_267 on 2009-06-17
It's there in case you accidentally cilcked shut down, and don't actually want to shut down. That's what I thought anyways.

---

### Post by Cheesemill on 2009-06-17
It's probably also there in case you click on it by accident....

---

### Post by jangari on 2009-06-17
It's also handy to write a couple of aliases into your .profile:
off='sudo shutdown -p $1'
restart='sudo shutdown -r $1'

The variable is there so I can command 'off now' if I want the machine to shut down immediately, or, for instance, 'off 30' if I'm doing something that will take around 25 minutes to finish, after which I want the machine to switch off.

I find shutting down on the command line is *much* quicker than using the shut down dialogue.

---

### Post by sailthesea on 2009-06-17
Or you could turn it off
 Right click the shutdown icon and in preferences uncheck the shutdown dialogue
 Boom!8 second shutdown;)

---

### Post by jenkinbr on 2009-06-17
aliasing doesn't accept variables.  fortunatly, for you, aliasing does accept additional parameters that get passed to the aliased command

I have 'sudo apt-get install' aliased on my system.  'install <package> works just fine.

---

### Post by H2SO_four on 2009-06-17
Always wondered that, didn't annoy me too much though.  Just turned it off.  THANKS!

---

### Post by kickwin on 2009-06-17
> **jenkinbr said:**
> 
(now for the system beep that annoys the hell out of me...)

I very much second that :D

---

### Post by ptviperz on 2009-06-18
> **kickwin said:**
> I very much second that :D

sudo modprobe -r pcspkr
sudo su -c 'echo blacklist pcspkr >> /etc/modprobe.d/blacklist'

---

### Post by jenkinbr on 2009-06-18
That will remove the pc speaker entirely, which is not what I want to do.

I just want it gone from the shutdown sequence.

---

### Post by CJ Master on 2009-06-19
> **ptviperz said:**
> sudo modprobe -r pcspkr
sudo su -c 'echo blacklist pcspkr >> /etc/modprobe.d/blacklist'

You may want to warn people that this could cause some trouble. The PC Speaker is important.

---

### Post by CJ Master on 2009-06-19
> **jenkinbr said:**
> That will remove the pc speaker entirely, which is not what I want to do.

I just want it gone from the shutdown sequence.

You think you got it bad? When I run GNOME on arch it beeps about 10 times!!

---

### Post by wpshooter on 2009-06-19
> **CJ Master said:**
> You may want to warn people that this could cause some trouble. The PC Speaker is important.

Can someone tell me the meaning and signifiance of the PC speaker beeping twice when the shutdown command is given ?

Thanks.

---

### Post by H2SO_four on 2009-06-19
That was bugging me up until about a week ago also. :)

---

### Post by t0p on 2009-06-19
> **wpshooter said:**
> Can someone tell me the meaning and signifiance of the PC speaker beeping twice when the shutdown command is given ?


Probably to draw your attention that the machine is shutting down.  In case you "accidently" clicked on shutdown and haven't noticed the countdown on the screen.

---

### Post by jenkinbr on 2009-06-19
> **t0p said:**
> Probably to draw your attention that the machine is shutting down.  In case you "accidently" clicked on shutdown and haven't noticed the countdown on the screen.
But it's too late by then anyways - if you had open and unsaved documents, they are now hosed.

I shut down my computer at night, when most of the house is sleeping.  Those beeps tend to wake people up.

until this is fixed, I've been running 'sudo telinit 0' from the command line, or 'gksudo telinit 0' from the 'Run' dialog.

---

