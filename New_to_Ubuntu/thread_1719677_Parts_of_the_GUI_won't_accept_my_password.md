---
title: "Parts of the GUI won't accept my password"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by TruePurple on 2011-04-02
This has happened with a few different times with different things. A GUI window asking for a password, yet rejecting my password I know I have correct.

System->administration-> Update-manager

Update manager loads without problem. When I click on settings though, it asks for a password. No matter how many times I certainly type in the correct password, it rejects it.

If I open a terminal and type in gksudo update-manager. It asks for a password before loading update manager, accepts that password, and does not ask for a password to get into settings.

System->administration-> synaptic package manager Also asks for a password but won't accept mine.

System-> administration-> login screen had this issue, but since then has changed and accepts my password.

Could it be this?
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/90324](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/90324)

Someone suggested something like "sudo passwd root", is that a good idea? How does that work?

---

### Post by matt_symes on 2011-04-02
Hi

> **TruePurple said:**
> This has happened with a few different times with different things. A GUI window asking for a password, yet rejecting my password I know I have correct.

System->administration-> Update-manager

Update manager loads without problem. When I click on settings though, it asks for a password. No matter how many times I certainly type in the correct password, it rejects it.

If I open a terminal and type in gksudo update-manager. It asks for a password before loading update manager, accepts that password, and does not ask for a password to get into settings.

System->administration-> synaptic package manager Also asks for a password but won't accept mine.

System-> administration-> login screen had this issue, but since then has changed and accepts my password.

Could it be this?
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/90324](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/90324)

Someone suggested something like "sudo passwd root", is that a good idea? How does that work?

From that bug report. What do you get when you type (at a terminal)

```
gconftool-2 --get /apps/gksu/sudo-mode
```

Post back results.

IMHO, enabling the root account is not a good idea.

Kind regards

---

### Post by TruePurple on 2011-04-02
Heh. what timing, someone in chat suggested I use the same command a short bit ago, except with out the "-2".

Either way, all it does is say "false".

What are the implications for enabling root account?

---

### Post by Dutch70 on 2011-04-02
> **TruePurple said:**
> What are the implications for enabling root account?

 In short, You would be overriding Ubuntu's main security feature. It's a really, really bad idea.

---

### Post by matt_symes on 2011-04-02
Hi

Set it to true.

```
gconftool-2 --set --type boolean /apps/gksu/sudo-mode true
```

Kind regards

---

### Post by TruePurple on 2011-04-02
I got help from chat and forum at the same time, I will enter some of what was said in chat for my and others future information.

oCeans solution: (different path to the same solution)
gconf-editor
click the (+) sign next to Apps, then from the list select gksu
Check box next to "sudo-mode"

oCeans: What you now actually did, is tell the gui backend to use the same method for authentication as you do on the commandline.

soreau: You can also re-own all files in .gconf by running as your normal user: sudo chown -R $USER $HOME/.gconf

 soreau: It will only not ask for password if you have entered it recently

oCeans: there's no need to chown the gconf files, since we edited as user, not as root

soreau:
ie. in case you ran gconf-editor with escalated permissions (with sudo, gksu or gksudo) and changed any setting (it will write the file as root and subsequently own it to root) then you can recursively (that is what -R means here) re-own the permissions to your normal user with the aforementioned command

The underlying message is, never run anything as root unless you know why you need to

Running as root means you used gksu, gksudo or sudo, or if you are logged in as root at your terminal, the last character will be a #. For user, the last char for your prompt is $

Me: Administrator and user are the same to me, being the only person who uses this PC

 That is the mistake most people make. They are entirely not the same thing

p.s. ohsix was also helpful.

Thankyou for all the help guys BTW! :guitar:

---

### Post by JustinForce on 2011-08-14
> **matt_symes said:**
> Hi

Set it to true.

```
gconftool-2 --set --type boolean /apps/gksu/sudo-mode true
```

Kind regards

This worked for me! Thanks. I think that my problem arose from installing Ubuntu Server, then installing the ubuntu-desktop metapackage.

---

### Post by brunolabs on 2011-09-01
That didn't work for me. Are there any other ways to fix this?

Thanks.

---

### Post by fudolove on 2011-10-31
Hello forum,
I recently installed ubuntu 11.10 and I am now having this same problem right after I updated 
and the computer ask me to reboot.
I rebboted and the computer keeps on  getting stuck at " checking battery"
So I read at another post  I need to install "lightdm"  but every time
I Try to do this at the terminal  all I get is a "login incorrect"
message.   Even though I am putting I'm my correct password.

Is thier a fix for this or do I have to reinstall buntu and don't upgrade?

Thank you in advance :(

---

### Post by tetzauh on 2011-12-07
got a similar problem. I'm in ubuntu 11.10 and the sowtware installer, the system unlock and all that won't accept my password. Funny thing: update does not ask for password! typed the command recommended above

gconftool-2 --get /apps/gksu/sudo-mode

and got true. 

Any thoughts?

---

