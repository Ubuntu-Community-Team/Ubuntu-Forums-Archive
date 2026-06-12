---
title: "How do I authenticate? &quot;Authentication is required to perform this action.&quot;"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by JamesR404 on 2010-10-19
How do I best deal with the message "An application is attempting to perform an action that requires privileges. Authentication is required to perform this action."

I'm trying to install a package and I get that message. But if I press authenticate and enter my password it just repeats the message and nothing happens (if I press authenticate again I won't even be bothered for the password, but no package gets installed)

I think it's because I'm not root.

But I'm also warned by other unix users not to enable root as it provides a security risk, should malicious code try to run on my machine.

Anyway, I'd like to hear from you guys what you believe is the best way around this.

Thanks! :KS


A Ubuntu newbie.

---

### Post by bolucpap on 2010-10-19
I think this is a bug, I've come across it a few times, but it's hard to replicate. What happens is I enter my password, the password text box disappears, but the prompt and the authenticate button just stays there. As a workaround I press the ESC key, and that dismisses the prompt and the process goes on, authenticated. Try that and see if it works for you.

---

### Post by Der Ritter on 2010-10-19
> **bolucpap said:**
> I think this is a bug, I've come across it a few  times, but it's hard to replicate. What happens is I enter my password,  the password text box disappears, but the prompt and the authenticate  button just stays there. As a workaround I press the ESC key, and that  dismisses the prompt and the process goes on, authenticated. Try that  and see if it works for you.

Judging by the wording of the question I don't think that's his problem...?

> **JamesR404 said:**
> 

But if I press authenticate and enter my password



You enter your password in the box, *then* press authenticate. When I say "your password" that is of course the password you use to log on.

You're partially right, that it's because you're not root. Actually anyone with administrative rights can install software. I believe your account is an administrator by default, but Ubuntu wants to make sure some nefarious person isn't trying to install software on your account. It does this by asking you to reenter your password.

You've been trained well in not enabling root. It's a huge security risk because if something bad happens to your machine the virus doesn't have to bother guessing your account name, it already knows there is one named "root". You should never need to log in as root in daily Ubuntu usage; just prefix commands with "sudo" or switch to a root terminal with "sudo -i" and you're good to go.

---

### Post by Chameco on 2010-10-19
If you're just trying to install a package, try sudo apt-get install "*packagename*". It will ask for your password, just type the password you use to log in, then press enter. Doesn't involve logging in as root, just authenticates you for the command.

---

### Post by Hippytaff on 2010-10-19
If its apackage you have downloaded you might need to change mode to make it executable
 
```

sudo chmod a+x *filename*

```
 
where file name is the...well...filename :-)

---

### Post by oldos2er on 2010-10-19
"How do I best deal with the message "An application is attempting to perform an action that requires privileges. Authentication is required to perform this action."

I'm trying to install a package and I get that message."

Can you please run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and post the output here?

---

### Post by Old_Man_Unix on 2010-10-19
> **Hippytaff said:**
> If its apackage you have downloaded you might need to change mode to make it executable
 
```

sudo chmod a+x *filename*

```where file name is the...well...filename :-)

If it IS a downloaded .deb package, this is neither necessary nor desirable and I don't think doing this  will solve the problem.  

The .deb package itself is not the executable.  It is the *package installer*, e.g., Gdebi,  that does the executing to install the package.  The package itself is merely the input to the installer. 

The system recognizes .deb packages and automatically launches the installer. 

Of course, the OP did not indicate that this was a .deb package.

---

### Post by azurehi on 2010-10-19
In 10.10, when update manager appears, I start it, enter my password and then Authenticate appears.  I select it and Nothing happens.  I close this box and the update proceeds.  What gives?

---

### Post by Bumbleflea on 2010-10-24
I'm having the same troubles when I try to install Code::Blocks using Synaptic. It says "this would require not authenticated packages.."

Also, when I try to install WxWidgets using Software Sources:

> W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF

---

### Post by mister_playboy on 2010-10-24
> **azurehi said:**
> In 10.10, when update manager appears, I start it, enter my password and then Authenticate appears.  I select it and Nothing happens.  I close this box and the update proceeds.  What gives?

I noticed this behavior when I installed 10.10 on my brother's laptop.  After a few reboots it disappeared... seems like a bug. :confused:

---

### Post by severusd on 2010-10-26
I installed Maverick this week and see the same behaviour.

The second "Authenticate" box (e.g. the one that doesn't prompt for a password) seems to indicate authentication has succeeded. I just close it by hitting the X and carry on.

Think I saw when googling that the bug report for this behaviour was already in, so hopefully there'll be a fix along shortly.

---

### Post by Hippytaff on 2010-10-26
If you add your experience to the launchpad bug thing it might be useful to the devs :-)

---

### Post by rado1 on 2010-10-27
Maybe a stupid question, but is the second box not a " unlock keyring" box?

---

### Post by RicktheBrick on 2010-10-27
When I run sudo apt-get update in a terminal I get
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
When I run update manager I sometimes get the message to install or remove software you need to authenticate but when I click on authenticate nothing happens.  Other times I get applying changes but there is a message about waiting for apt-get to exit.  In both cases I do not get any of the updates.

---

### Post by beew on 2010-10-27
> **RicktheBrick said:**
> When I run sudo apt-get update in a terminal I get
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
When I run update manager I sometimes get the message to install or remove software you need to authenticate but when I click on authenticate nothing happens.  Other times I get applying changes but there is a message about waiting for apt-get to exit.  In both cases I do not get any of the updates.


That is because you have several instances of the software manager opening at the same time. Maybe Synaptic or the Software Center is open while you are using the update manager. Just close all of them but one.

I have experienced the authentication thing on one of my Maverick install, but that only happened after installation and it went away. Maybe there was a bug and it was fixed by the updates.

---

### Post by RicktheBrick on 2010-10-29
I ran system monitor and the only thing I can see is update-notifier.  The only way I can get my system to update now is to run update manager and a terminal at the same time.  I than go through the list of programs one by one and type in the terminal sudo apt-get install program.  It takes a while but after I finish I rerun update manager to see that my computer is up to date.

---

### Post by Hippytaff on 2010-10-30
It's a workaround, but surely there is a fix for this, unless it is a bug after all :-)

---

### Post by bkline on 2011-02-18
It's a bug, sitting idle at [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/656975](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/656975) since last fall.

---

### Post by Hippytaff on 2011-02-18
Thought as much

---

### Post by bkline on 2011-05-17
> **bkline said:**
> It's a bug, sitting idle at [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/656975](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/656975) since last fall.

This appears to have been fixed, with no trace of the fix in the launchpad issue.

---

### Post by wildmanne39 on 2011-05-17
> **Bumbleflea said:**
> I'm having the same troubles when I try to install Code::Blocks using Synaptic. It says "this would require not authenticated packages.."

Also, when I try to install WxWidgets using Software Sources:

W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF

Hi, the no public key available is because before ubuntu lets you download it, it checks to see if there is a key for safety, and if not you have to add it in synaptic package manager before you can download and install it through synaptic.

---

