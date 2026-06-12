---
title: "Login as root and installing Java"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by izacboy_123 on 2011-06-21
Hi guys,

I decided to download Ubuntu 10.04 Maverick Server version and use it for hosting servers on my LAN. I'm having two different problems:

**One.:**

How do I login as root? When installing Ubuntu, I was able to create a user account and password for none adminstrators, but how do I login as the root? I wasn't given the option to set a password for root, and I wasn't given a default password for the root.

**Two.:**

How the heck do you install Java runtime? I've tried various tutorials and they just will not work! I've managed to do other apt-get commands and install other stuff, but Java just will not install!

-

Any help is much appreciated, guys, thanks!

---

### Post by snowpine on 2011-06-21
Welcome to the forums!

1. No need to log in as root in Ubuntu, we use "sudo" instead:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

2. You may find this helpful:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I'll also throw in a recommendation for this helpful document to get you started, good luck!

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by izacboy_123 on 2011-06-21
> **snowpine said:**
> Welcome to the forums!

1. No need to log in as root in Ubuntu, we use "sudo" instead:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

2. You may find this helpful:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I'll also throw in a recommendation for this helpful document to get you started, good luck!

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Brilliant, thanks! I've used sudo to add a repository and can now succesfully use: **sudo apt-get install sun-java6-jre sun-java6-plugin** - and it seems to be working :-)

The only annoying thing about using Sudo, is that it asks me for my password. I'd still like to be able to login as the root, how can I do this?

Thanks!

---

### Post by dFlyer on 2011-06-21
It's not wise to login as root. You place you whole system at risk. You might as well be using windows. Now to answer your question. You can log in as root, but you will have to search the internet/ubuntu forum for the answer as I don't want the responsibility for such actions.

---

### Post by nothingspecial on 2011-06-21
> **dFlyer said:**
> It's not wise to login as root. You place you whole system at risk. You might as well be using windows. Now to answer your question. You can log in as root, but you will have to search the internet/ubuntu forum for the answer as I don't want the responsibility for such actions.

You don't need too, just type

```
sudo -i
```

and away you go

---

### Post by izacboy_123 on 2011-06-21
> **dFlyer said:**
> It's not wise to login as root. You place you whole system at risk. You might as well be using windows. Now to answer your question. You can log in as root, but you will have to search the internet/ubuntu forum for the answer as I don't want the responsibility for such actions.

(?) I don't see how it can be a problem logging in as the root. Do you mean me being logged in as root is dangerous because of what I can do, or someone being able to gain access to my computer as root?

Thanks

---

### Post by snowpine on 2011-06-21
It is not "dangerous" to log in to the console as root. The Root/Sudo page I linked to in post #2 explains how. (short answer: "sudo -i")

Logging in to the GUI (Unity, Gnome, KDE, etc.) as root is discouraged because Linux simply isn't designed or tested to work that way, therefore you might run into all kinds of unexpected bugs, security risks, and generally weird behavior. :)

---

### Post by crispy_420 on 2011-06-21
If you insist on setting up root and using it:

1) Switch to root: sudo su
2) Add/Change root password: passwd

It will ask for the standard new password then confirmation. And you are done.

As far as risk factor both are potentials. It saves you from yourself I guess but you could just sudo yourself into trouble too. Also it can protect you from external threats too since root is the default login (like Administrator in Windows which you should disable too). But if you are not externally facing and it is not a production server (tinkering right?), I say go for it.

---

### Post by jtarin on 2011-06-21
> **crispy_420 said:**
> 
As far as risk factor both are potentials. It saves you from yourself I guess but you could just sudo yourself into trouble too. Also it can protect you from external threats too since root is the default login (like Administrator in Windows which you should disable too). But if you are not externally facing and it is not a production server (tinkering right?), I say go for it.It saves you from yourself and coming to the forum and telling us you hosed your system.....like he says.....go for it.:p

---

