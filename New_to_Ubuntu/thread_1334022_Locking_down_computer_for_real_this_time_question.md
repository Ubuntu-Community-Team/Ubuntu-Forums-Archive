---
title: "Locking down computer for real this time question"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by mjp29 on 2009-11-22
I was only locking down my email [sent and received] in thundermail; however, I now feel a need to lock down my computer from minors unless I'm supervising.

When I installed Ubuntu from live cd [that I actually downloaded to an old mac os x box and burned the image - that's wild], I chose to allow the cpu to boot up without a password.

Now I feel the need to password protect the Ubuntu cpu upon boot.  Tell me how to do that.


Thanks so much for anyones time to reply to this post -  I know time is life.

---

### Post by quinnten83 on 2009-11-22
you can set that up in "System > Administration > Login screen".
Select to have a user select their name to log in.

---

### Post by mjp29 on 2009-11-22
> **quinnten83 said:**
> you can set that up in "System > Administration > Login screen".
Select to have a user select their name to log in.

That's the info i needed.  thanks so much!  marking this thread as solved.

---

### Post by mjp29 on 2009-11-22
ok did that,

but I also feel a need to change the password upon boot

?

---

### Post by danill2008 on 2009-11-22
> **mjp29 said:**
> ok did that,

but I also feel a need to change the password upon boot

?

You can set a password in the BIOS if you want to...

---

### Post by mjp29 on 2009-11-22
yes indeed, that is what i want to do

please guide me the way

---

### Post by danill2008 on 2009-11-22
Ok, when you start your computer, press F2 or any key that is displayed for "Enter Setup". This lets you boot into the BIOS. Here you can set a password.

---

### Post by mjp29 on 2009-11-22
I actually only need a password upon boot.

The previous poster thought System->Administration->Login screen would allow me to change the login password.  

But i can't see where i can there

i will do bios password if neceasary,

but i only need to change normal GUI ubnutu bootup password at this time

---

### Post by danill2008 on 2009-11-22
Ok, what version of ubuntu are you running? Also you must have made a password when you installed ubuntu...did you select "Log in automatically" when installed? Otherwise you can just disable it....

---

### Post by quinnten83 on 2009-11-22
well, you can change your own password as a user. I don't think there is a setting to allow you to change your password everytime before you log in though, because you need to authenticate in order to be allowed to change your password.
I don't think any operating system does it the way I think you want.
In "System > preferences > about me" you can change your password. It's in the upper right corner on the "About me" application screen.

EDIT: my info is for Ubuntu 9.10

---

### Post by mjp29 on 2009-11-22
Actually, I just re-thought everything.

I re-thought everything because of your post.

I actually did change the password in BIOS.

Is my thinking correct when I say below:

That you telling me and I did change BIOS password that not even a person could try to boot with Ubuntu Live cd or Windows boot cd to format my HD?

If so, then I much love that [aweseome!] - AWESOME in my opinion, as that is truly LOCKING the damn box down for F'ing sure!

Please reply

---

### Post by quinnten83 on 2009-11-22
Bios setup happens before you can enter the computer, so yes, it is quite locked down. Nobody can do anything on that computer, be it with Windows, Linux, or BSD. Unless they steal it and run bios hacking tools on it, but the chances are minimal.

---

### Post by danill2008 on 2009-11-22
> **mjp29 said:**
> Actually, I just re-thought everything.

I re-thought everything because of your post.

I actually did change the password in BIOS.

Is my thinking correct when I say below:

That you telling me and I did change BIOS password that not even a person could try to boot with Ubuntu Live cd or Windows boot cd to format my HD?

If so, then I much love that [aweseome!] - AWESOME in my opinion, as that is truly LOCKING the damn box down for F'ing sure!

Please reply

Yes that is infact what it does....glad you got it working;)

> **quinnten83 said:**
> Bios setup happens before you can enter the computer, so yes, it is quite locked down. Nobody can do anything on that computer, be it with Windows, Linux, or BSD. Unless they steal it and run bios hacking tools on it, but the chances are minimal.

You don't necessarily need hacking tools, there are other ways....but yes it would be rather hard for anyone to do anything without a password

---

### Post by mjp29 on 2009-11-22
LOL - Ubuntu forum self censors.  LOL. ROFLMAO!!!!!!!!!!!!!!!!!

I've been saved by a script - !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Like on IRC, warned or kicked by a BOT !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

This is too much - ROFLMAO !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by danill2008 on 2009-11-22
> **mjp29 said:**
> LOL - Ubuntu forum self censors.  LOL. ROFLMAO!!!!!!!!!!!!!!!!!

I've been saved by a script - !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Like on IRC, warned or kicked by a BOT !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

This is too much - ROFLMAO !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Im glad that you got it working....;) Also you can't remove the login password, but I think you meant to say "Log in automatically". This can be found under System > Administration. Click on unlock, enter your password and select "Log in as xxxxxxx automatically"

---

