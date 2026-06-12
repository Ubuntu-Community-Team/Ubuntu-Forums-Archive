---
title: "Can not authenticate."
date: 2011-06-03
forum: New to Ubuntu
---

### Post by L Campbell on 2011-06-03
I have just done a fresh, clean install of 11.04 and when I try to install the Updates my password keeps being rejected.

 "Your authentication attempt was unsuccessful. Please try again."

When I was preparing to install 11.04 my password was deemed 'short' but it is the same password I have used for several years (and versions)

Is this a known problem?

TIA

---

### Post by collisionystm on 2011-06-03
> **L Campbell said:**
> I have just done a fresh, clean install of 11.04 and when I try to install the Updates my password keeps being rejected.

 "Your authentication attempt was unsuccessful. Please try again."

When I was preparing to install 11.04 my password was deemed 'short' but it is the same password I have used for several years (and versions)

Is this a known problem?

TIA


I am not sure. Sounds like a glitch.

Open terminal

sudo passwd your.username

set a new passcode

now do your update

---

### Post by L Campbell on 2011-06-03
> **collisionystm said:**
> I am not sure. Sounds like a glitch.

Open terminal

sudo passwd your.username

set a new passcode

now do your update

Thanks. Unfortunately it doesn't seem to like my password either.

qwer@qwer-P9852A-ABA-753N:~$ sudo passwd qwer
[sudo] password for qwer: 
Sorry, try again.

---

### Post by irv on 2011-06-03
Check the cap lock key. Did you you have it on when you set your password? In Linux the caps are impotent. There is a difference between a and A. I was having trouble logging on one day, and I noticed the cap lock was on. I turn it off and got log on.

I know when you do an install it always ask you to verify your pass code so it should work.

---

