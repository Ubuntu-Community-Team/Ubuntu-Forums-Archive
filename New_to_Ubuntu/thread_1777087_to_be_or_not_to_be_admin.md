---
title: "to be or not to be admin"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by mkornig on 2011-06-07
Hello everybody,

I'm the only person who uses my computer.

By default Ubuntu creates a first user account who has admin privileges (useful for installing updates and printer drivers, creating/deleting other users, etc.).

I've created a second account which does **not **have admin privileges. I login on this account when I want to do ordinary things (surfing, playing sudoko, etc.).

[B]Questions :
[/B]
[LIST]
[*]Do you have to have a second account for ordinary work?
[*]If you don't, what are the advantages/disadvantages?
[*]Why aren't there two accounts by default?
[/LIST]

---

### Post by iclestu on 2011-06-07
> **mkornig said:**
> Hello everybody,

I'm the only person who uses my computer.

By de fault Ubuntu creates a first user account who has admin privileges (useful for installing updates and printer drivers, creating/deleting other users, etc.).

I've created a second accound which does **not **have admin privileges. I login on this account when I want to do ordinary things (surfing, playing sudoko, etc.).

[B]Questions :
[/B]
[LIST]
[*]Do you have to have a second account for ordinary work?
[*]If you don't, what are the advantages/disadvantages?
[*]Why aren't there two accounts by default?
[/LIST]


I dont have a separate account.

I think that as long as your not loging in as root then the system prompts you for passwords everytime you do a 'sudo' command. Similarly for anything in the gui that needs admin rights. To me, so long as your password is sensible then a second account is overkill....

---

### Post by nothingspecial on 2011-06-07
Ubuntu uses sudo which avoids having a user account and using the root account.

You just elevate yourself when you need to.

---

### Post by mcduck on 2011-06-07
Even the admin account is, for pretty much everything, just a normal, unprivileged user account. the only difference is that admin accounts are allowed to *temporarily* gain higher permissions (thorugh the use of sudo and password confirmation).

So using an admin account for your day-to-day computing tasks should work just fine, it definitely isn't the same as using a Windows system as Administartor or Linux system as root (which would both mean having full permissions todo anything, all the time, and launching all your programs with same full permissions)

---

### Post by mkornig on 2011-06-07
Interesting. Thanks for sharing your opinions and experience, guys.

So it seems that I overkilled security a bit. Since the split works all right for me, I think I'll leave it that way.

Cheers

---

