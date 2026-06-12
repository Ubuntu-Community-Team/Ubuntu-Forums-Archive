---
title: "Directory Service and Deploying Software"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-10-17
Two questions:

1. Does Ubuntu Server come with a Directory Service?

2. Is there a way to deploy software to multiple Ubuntu/Linux clients through Ubuntu Server (or another Distro server)?

---

### Post by Cuco3 on 2009-10-17
please?

---

### Post by sloggerkhan on 2009-10-17
There is a way to deploy software to multiple clients. In fact there are a lot of ways. Depending on the tool you could have a localized apt repo deploy software or something else. Likewise, there is a directory service. Thing is, I don't use either of these things, so while I can tell you unequivocally that they exist, I couldn't remember the details off my head. Some googling ought to help.

---

### Post by Cuco3 on 2009-10-17
I used Google before creating this thread.

It's just that there doesn't appear to be a direct answer or instructions on deploying software or directory services (googled "ubuntu deploy software" and "ubuntu directory service").

All I really needed was a "yes" or "no' answer and I figured someone could get that to me here.

Thanks for the help!

BTW, I don't think there's a Directory Services for Ubuntu Server, at least one that's included with Ubuntu Server. Can someone verify this?

---

### Post by sloggerkhan on 2009-10-18
Try LDAP, it's probably the most obvious set of directory services, and have you used Ubuntu or Linux before? There are really many possibilities for software deployment. The simplist would be a cron script that installed packages from a central server nightly, but there are more comprhensive business type solutions. Likewise, deploying installs of ubuntu can be done with anything from landscape to clonezilla, etc. Likewise, thin client setups are also very possible.

Likewise, ubuntu server isn't going to come bloated out of the box. You are going to have to add your apps to it, though the installer does allow you do choose common options during install. If it came with every single network service preinstalled it would be a security and maintenance nightmare. Rather, it comes with the ability to easily install many network services from the ubuntu repositories or 3rd party sources.

---

