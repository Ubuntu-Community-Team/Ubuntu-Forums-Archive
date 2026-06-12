---
title: "Life after backports"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Nosferatu1 on 2008-12-16
What happens to the security status of all the Backported software? 
Does the Backporting team supply security fixes for backported versions of the Gimp, etc, for the lifetime of your *ubuntu version?

---

### Post by Michael.Godawski on 2008-12-16
hi Nosferatu1,
for comprehensive info have a look at:


[LIST]
[*][https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
[/LIST]

---

### Post by Nosferatu1 on 2008-12-16
Thanks Michael

I have already been to the page you suggested, and it mentions nothing about security issues with backported programs.

I'll give an example scenario:

I am running Kubuntu 8.04. I have added "unsupported updates" (backports) in my apt sources.
A new backported version of Gimp appears in backports so it is auto installed.

Now, what happens if a security advisory is issued by say Debian, for that particular version and a fixed version made available? Does the backports team put the fixed version into the backports repos as a replacement?
If so, how long will they continue to do this. In our example 8.04 is LTS, so it will be around for 3 years. Will security updated versions of the backports be provided for the whole period?

---

### Post by matthew on 2008-12-17
The quick answer is that there will most likely *not* be security updates to software in the backports repo. There *might* be, but there are no guarantees, so I recommend that you do not count on them.

This is why backports are not enabled by default, and are recommended primarily for more advanced users.

---

### Post by Nosferatu1 on 2008-12-19
Can't anyone from the backports team give me a definite answer?

It says on the documentation page (Link above)

> Backports is an official Ubuntu repository and maintained by knowledgeable Ubuntu developers who are often present on IRC and other communications media. But note that software in backports will not receive review or updates from the Ubuntu security team itself. 

So can we assume that the backports team  will take care of security issues?

---

### Post by matthew on 2008-12-19
> **Nosferatu1 said:**
> So can we assume that the backports team  will take care of security issues?
No. You can assume that IF security issues are dealt with, they will ONLY be dealt with by the backports team. In other words, there are no guarantees that security updates will be made for backported software. They might, but they are not promised.

I use backports often, but with the understanding that I am doing so at my own risk from a security standpoint. As such, I would never do so on a server or machine with sensitive data.

---

### Post by Nosferatu1 on 2008-12-19
> **matthew said:**
> ...IF security issues are dealt with, they will ONLY be dealt with by the backports team

I understand that. But the backports repo is official. So what do they really mean when they say "maintained" by the backports team

> **matthew said:**
> ...I use backports often, but with the understanding that I am doing so at my own risk from a security standpoint.

Would his also be the case with universe and multiverse from MOTU?

I would think that "maintained" implies a definite ongoing commitment by the person/group/team supplying the software, where security fixes etc., would be passed on. I just find it difficult to comprehend that software would be supplied, and not reviewed any further.

---

### Post by matthew on 2008-12-19
> **Nosferatu1 said:**
> I understand that. But the backports repo is official. So what do they really mean when they say "maintained" by the backports teamThey mean that the packages are made by people who know what they are doing and that the packages available in backports will be put together to the same high standards as the packages in the other Ubuntu repositories.

> **Nosferatu1 said:**
> Would his also be the case with universe and multiverse from MOTU?No. At least I do not believe so. Those packages should receive security updates. This is why I think so.

Here is a list of the official repositories, cleaned up to be more easily readable.

```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
# deb-src http:/.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

 deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
 # deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
```Notice that the security repo includes all four main categories; main, restricted, universe, and multiverse.

So does backports, but these packages will be higher in number than the packages in the security repo, so if you have backports enabled and have installed packages from there, you cannot count on packages that are placed in the security repo to be noted or installed.

> **Nosferatu1 said:**
> I would think that "maintained" implies a definite ongoing commitment by the person/group/team supplying the software, where security fixes etc., would be passed on. I just find it difficult to comprehend that software would be supplied, and not reviewed any further.

The backports repo is for people with special needs, who ***have*** to have the latest version of a piece of software and who can't wait until the next Ubuntu release to get it. It is not intended to be enabled all the time. Some do so, but at their own peril. 

The overwhelming majority of us can use the regular repos with great success and receive security updates on everything we install.

---

### Post by Nosferatu1 on 2008-12-19
> **matthew said:**
> The backports repo is for people with special needs, who have to have the latest version of a piece of software and who can't wait until the next Ubuntu release to get it. It is not intended to be enabled all the time. Some do so, but at their own peril.

An official statement like this from the backports team on the docs page would clear things up a great deal, as would a statement on their security/updating policy.

Thanks for pointing out the the universe multiverse situation in the apt-sources, that helped a great deal. 

Is there any way to request clarification from the backports team?

---

### Post by matthew on 2008-12-19
> **Nosferatu1 said:**
> Is there any way to request clarification from the backports team?
They have a mailing list here: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-backports](https://lists.ubuntu.com/mailman/listinfo/ubuntu-backports)

Please update us if you get in contact and hear anything.

---

