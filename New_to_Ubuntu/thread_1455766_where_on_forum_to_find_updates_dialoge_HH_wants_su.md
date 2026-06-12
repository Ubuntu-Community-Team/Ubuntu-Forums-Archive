---
title: "where on forum to find updates dialoge? HH wants sudo update.."
date: 2010-04-16
forum: New to Ubuntu
---

### Post by neophyte_of_linux on 2010-04-16
My updates notifier says there is an important security update and when I checked it is for the "sudo" part of the OS. 

Since I know that having access to sudo command is a security key, I wanted to find out more information on what this update is...

I was a little suspicious that the details have "CVE-2010-XXX" and this link goes nowhere.

How do I know this update can be trusted? And my machine isn't infected or something?  Do I just blindly click update because I trust the repository is safe?

---

### Post by e4uforums on 2010-04-16
I received this update yesterday.  I downloaded it and have yet to see any problems.  I don't have any special repos enabled so I assumed it was coming from a trusted source...  so far so good...

---

### Post by DM was on fire! on 2010-04-16
There really isn't any way to get an "infection" on Linux. While there are viruses for Linux, they're rare. No one ever really bothers with Linux viruses because there's so many different desktop environments and there aren't a lot of Linux users, compared to the mass of Windows users.

If the update is coming from Canonical/Ubuntu and is coming to you via the updates dialog, I'm sure it's safe to install.

I would wait for an admin to respond just to be sure though.

---

### Post by doas777 on 2010-04-16
CVE stands for "Common Vulnerability and Exposures". when a security bug is responsibly reported, a CVE is created for it (a lot like a bug on launchpad) and all the security and software vendors use the CVE to refer to the specific vuln. helps them keep track of which thing they are discussing. having a CVE is more an indication that the information can be trusted, than that it can't.

---

### Post by Zill on 2010-04-16
neophyte_of_linux:  You can always verify a security update with the following link:
[URL="http://www.ubuntu.com/usn"]
http://www.ubuntu.com/usn[/URL]

It looks to me like your update relates to [USN-928-1: Sudo vulnerability]("http://www.ubuntu.com/usn/USN-928-1")

---

### Post by neophyte_of_linux on 2010-04-16
> **Zill said:**
> neophyte_of_linux:  You can always verify a security update with the following link:
[URL="http://www.ubuntu.com/usn"]
http://www.ubuntu.com/usn[/URL]

It looks to me like your update relates to [USN-928-1: Sudo vulnerability]("http://www.ubuntu.com/usn/USN-928-1")


Thank you. That /usn link was kind of what I was looking for on the forumus. I've bookmarked it now.

The description matches what the dialoge box is saying in the autoupdates thingo....  having a "." in a file path, etc.

Thanks everyone, if it weren't for the forum I don't think I would have been able to "happily" have converted from XP to Ubuntu.

---

