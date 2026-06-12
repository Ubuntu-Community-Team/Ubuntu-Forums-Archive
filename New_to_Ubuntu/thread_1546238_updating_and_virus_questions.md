---
title: "updating and virus questions"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Proto_Blaze on 2010-08-05
every 6 months or so a new ubuntu is released... do i have to download the iso and re-install ubuntu? or is there an update feature?
and why is it that linux is so immune to viruses?

---

### Post by Proto_Blaze on 2010-08-05
bump

---

### Post by ron999 on 2010-08-05
Hi
There's an update feature if you don't want to do a clean install.
You'll get a reminder in your Update Manager.
It will say 'New Ubuntu release --- is available'.

> and why is it that linux is so immune to viruses?

That's because most computers use Windows so the virus writers concentrate on them.

---

### Post by Nerflander on 2010-08-05
most of time there is a command so you can upgrade to the newer ubuntu. Search for the main website of ubuntu for that. furthermore Ubuntu doesnt got alot of virusses caus they mostly are all written for windows this makes ubuntu pretty much virus resistent. 

Windows is far out the most populair OS. Virusmakers know this and thats why you will mostly encounter virusses on windows


edit: didt see the other post there:)

---

### Post by amauk on 2010-08-05
No, you do not have to reinstall

To update, open up
System > Administration > Update Manager

If there is a new version of Ubuntu out, a button will appear on the update manager allowing you to upgrade

Ubuntu has two release cycles
- One every 6 months
- An LTS (long term support) release every 2 years

You can configure whether you wish to upgrade every 6 months or stick with LTS releases in
System > Administration > Software Sources
Under the "Updates" tab

As for the second question
[http://ubuntuforums.org/showpost.php?p=8424962&postcount=13](http://ubuntuforums.org/showpost.php?p=8424962&postcount=13)

---

### Post by Proto_Blaze on 2010-08-05
whats the difference between the 6 month and LTS?

---

### Post by amauk on 2010-08-05
> **Proto_Blaze said:**
> whats the difference between the 6 month and LTS?
Purely the length of time it is supported

The "normal" releases are suitable for everyone
Every 6 months, all the software gets updated to later versions

The LTS versions, released every 2 years, are suitable for businesses or other large scale deployments where it is not important to always have the latest versions of software

It's personal preference
Do you want to upgrade every 6 months, or every 2 years?

---

### Post by Paddy Landau on 2010-08-05
> **amauk said:**
> It's personal preference
Do you want to upgrade every 6 months, or every 2 years?
Personally, I've stuck to LTS and been very happy with it. I don't have to go through the bother of upgrading every six months; every upgrade comes with its own set of teething problems, so mine are once every two years. Some people are luckier than others, but I rather just don't take the risk.

---

### Post by Jazzy_Jeff on 2010-08-05
> **amauk said:**
> 

As for the second question
[http://ubuntuforums.org/showpost.php?p=8424962&postcount=13](http://ubuntuforums.org/showpost.php?p=8424962&postcount=13)


Here is the info from this post:


Low level executable code that is tacked onto an innocent file.
When the file is loaded into memory (opened), these low level instructions get executed.
The executed code will copy itself (or a variation of itself) to other innocent files currently loaded into memory.

The reason viruses can exist on Windows, is because the operating system has no security model for in-memory file interaction.
Unix and Unix-like systems (often just called *nix systems) *do* have a security model for in-memory file interaction.

Viruses do not exist on *nix operating systems.
Well, they do exist, I mean anyone can write a virus (it's not hard), but the thing is under *nix viruses won't propagate to other files without the root user giving *express* permission for the interaction to happen.

The root user can do anything, including damaging / destroying the system (or allowing something else to damage it). 
This is why people should never login to a system as root.
Always use su (or sudo) to elevate your privileges, should you need to.
Never run an 'untrusted' binary as root.

As stated above, the root user has the authority to destroy the system, a normal user does not.
A normal user, using a computer in a normal manner, is immune to viruses under *nix

---

### Post by Proto_Blaze on 2010-08-05
sweet, now i know i dont have to do a complete reinstall every 6 months... thank you

---

### Post by sadaruwan12 on 2010-08-05
> **Proto_Blaze said:**
> sweet, now i know i dont have to do a complete reinstall every 6 months... thank you

If your problem has been solved please mark it as solved.

---

