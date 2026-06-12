---
title: "[SOLVED] Should I create a limited account?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by ooobooontooo on 2009-01-08
Hi,

So I come from Windows and I'm used to having one admin account to install anything and one limited user account for daily activities. I've done the same setup on Ubuntu as well. However, it's a pain for me to su into the admin account every time I want to do something like iwlist or install new packages... Is it safe to just go with the admin account or should I continue with limited account? I've read some places where it says as long as you don't needlessly run scripts with root power it should be fine. However, the main Ubuntu Security thread located at [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812") says that I should consider getting a limited user account. What do you think? Yes limited account or no limited account? Thanks in advance.

---

### Post by iaculallad on 2009-01-08
Try to use the *limited account* type for security purpose, the very essence of using Unix/Linux OS'es. Providing users both root and user account. Running applications does not always require you to initiate sudo/gksudo. You only need it when running administrative commands or scripts that can do changes on your system configuration.

---

### Post by Paqman on 2009-01-08
I say: no limited account.

Why? Because your admin account is also a limited account.

Your admin account does not have admin powers all the time. The "admin" part of that account is simply the ability to elevate the account's privileges from that of a user to an administrator (or "root" user) as and when required.

That's why you are prompted for a password before opening an admin tool, and why you must prefix certain terminal commands with sudo. The system is authenticating you as being the person who has the rights to do this.

This system is a bit of an Ubuntu oddity. Traditional Linux setups tend to have a single root account that was used for admin tasks, and user accounts with limited privileges.

---

### Post by sdennie on 2009-01-08
I'm of the opinion that a "limited user account" may be a bit overkill for most people.  If you never type "sudo", you have a limited user account.  If every time you want to run sudo, you first su to an account with admin privs, all that you've done is made it so you have to type your password twice to use sudo.  I'm certainly not a security expert but that doesn't seem more secure to me.

---

### Post by ooobooontooo on 2009-01-08
Exactly....to all your responses That's what I'm starting to think... I mean I do protect myself with iptables and stuff and I don't needlessly run sudo...in my opinion. But I do use my limited account for writing up documents and stuff...and I'm definitely more free with my limited account than my admin account, like when I'm browsing. I would never click on a site that I've never heard of with my admin account, while I wouldn't feel so bad about it if I was using my limited user account. So I guess what I'm really asking is confirmation of what sdennie said. Is everything truly like a limited user if you never use sudo in an admin account? Or are there extra risks because it's the admin account?

---

### Post by Paqman on 2009-01-08
> **ooobooontooo said:**
> Is everything truly like a limited user if you never use sudo in an admin account?

Yep. You're only an admin while actually using sudo/gksudo/kdesudo.

---

### Post by ooobooontooo on 2009-01-08
Excellent. One last thing. Is the extra security offered by a limited user really worth it? I mean I'm just getting used to Ubuntu so I use sudo fairly often...at least a couple times a day...to find found about the different functionalities and to customize it to what I like. If the computer is for my own personal use, is the extra limited user worth it? Haha...sorry for asking the same question again, but I would like to know what more knowledgeable security people think. :D

EDIT: I think the question that might help me decide all this is. Would I be just as safe clicking on a sketchy link in the admin account as I would be in the limited user account?

---

### Post by ajcham on 2009-01-08
> **ooobooontooo said:**
> 
EDIT: I think the question that might help me decide all this is. Would I be just as safe clicking on a sketchy link in the admin account as I would be in the limited user account?

You'll be fine - merely clicking a weblink is not sufficient for Ubuntu to try to execute a file.  It would take a very unusual set of circumstances to cause a problem:
[LIST]
[*]You click a link and download a dodgy script.
[*]You yourself then choose to run that script.
[*]The script tries to use sudo.
[*]You have used sudo recently and are still within the timeout period, and so are not prompted for a password.
[/LIST]

As you can appreciate, that is highly unlikely.  However, if you are especially paranoid you can use:
```
sudo visudo
``` to edit the sudoers file. Add the following line to reduce the sudo timeout to a shorter period (replace XX with the number of seconds): ```
Defaults:USER_NAME timestamp_timeout=XX

```

---

### Post by Paqman on 2009-01-08
> **ooobooontooo said:**
> Would I be just as safe clicking on a sketchy link in the admin account as I would be in the limited user account?

Yes. Nothing that isn't root can alter system files without the password. Your browser runs as a user. Running it as root would be a very bad idea.

> **ajcham said:**
> 
[*]You have used sudo recently and are still within the timeout period, and so are not prompted for a password.


AFAIK, even that won't work. The sudo grace period only applies to the terminal that it was run in. As long as you close the terminal after using sudo, there's no risk.

---

### Post by lykwydchykyn on 2009-01-08
I only use limited (non-admin, that is) accounts for my kids.  Such peace of mind!

---

### Post by Paqman on 2009-01-08
> **lykwydchykyn said:**
> I only use limited (non-admin, that is) accounts for my kids.  Such peace of mind!

That's the real advantage of a non-sudo account. It protects the system from the user!

---

### Post by ajcham on 2009-01-08
> **Paqman said:**
> AFAIK, even that won't work. The sudo grace period only applies to the terminal that it was run in. As long as you close the terminal after using sudo, there's no risk.

I've just tested it and, even after closing the terminal, I was able to open another and use sudo without a password.

---

### Post by Paqman on 2009-01-08
> **ajcham said:**
> I've just tested it and, even after closing the terminal, I was able to open another and use sudo without a password.

Ah well, seems i've been misinformed then.

---

### Post by iaculallad on 2009-01-08
> **ajcham said:**
> I've just tested it and, even after closing the terminal, I was able to open another and use sudo without a password.

The only thing you can do is to remove the timestamp of sudo by issuing:

```
sudo -k
```

When you're to execute sudo again, you are required for the privilege password.

---

### Post by ooobooontooo on 2009-01-10
Thanks guys. I feel reassured. I guess no more limited account.

---

