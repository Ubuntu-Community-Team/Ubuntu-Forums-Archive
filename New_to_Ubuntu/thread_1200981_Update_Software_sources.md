---
title: "Update Software sources"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-30
In system>admininstration>software sources tab, can someone tell me what the default is for the first 3 tabs(Ubuntu software, Third party and Updates).

Also in the Updates tab, what are the 3rd and 4th options - pre-released updates (jaunty proposed) and unsupported updates (jaunty-backports). What does it mean to us as end users?

Thanks

---

### Post by drs305 on 2009-06-30
> **Andy06 said:**
> In system>admininstration>software sources tab, can someone tell me what the default is for the first 3 tabs(Ubuntu software, Third party and Updates).

Also in the Updates tab, what are the 3rd and 4th options - pre-released updates (jaunty proposed) and unsupported updates (jaunty-backports). What does it mean to us as end users?

Thanks

Here is the ubuntu wiki I updated a few months ago:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

In Jaunty all are enabled in Ubuntu Software and updates and security on the updates tab. In earlier editions, main, restricted and source were enabled in the Ubuntu Software tab.

The wiki lists/shows the defaults and also explains the ones you are asking about.

---

### Post by kukibird1 on 2009-06-30
> **Andy06 said:**
> In system>admininstration>software sources tab, can someone tell me what the default is for the first 3 tabs(Ubuntu software, Third party and Updates).

Also in the Updates tab, what are the 3rd and 4th options - pre-released updates (jaunty proposed) and unsupported updates (jaunty-backports). What does it mean to us as end users?

Thanks

[https://help.ubuntu.com/community/UbuntuUpdates]("https://help.ubuntu.com/community/UbuntuUpdates")

---

### Post by Andy06 on 2009-07-01
Hi, I read the links given and had read the Help file within Ubuntu Help and support before posting. I understand the differences better now and just need some more minor clarifications :) :

1. In the updates tab, the unsupported updates (backports) are for newer versions of programs on ONLY older than current Ubuntu OS releases or also for newer versions on current releases? I mean Ubuntu only provides bugfix and security patches right? If I have FFv3.0.10 installed, it will update it to v3.0.11 but will not move onto FF v3.5 correct? So will enabling this then auto update to v3.5?
Or is it for new versions of program included with 9.04 which might also be desirable to people who are still on say, 8.04? 

I ask because the help files seem to sort of conflict each other.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) seems to suggest that you should enable backports if you want completely newer version of software (as opposed to bugfixes and security updates).:

> Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available.

This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system. 

Also, [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates) seems to suggest that enabling these is a good idea if you want new software but not instability.

> Backported updates are pieces of software which come from a newer major release. Thus, they can contain new features, but may also break compatibility with their older version. However, they are compiled specifically for your version of Ubuntu. In effect it saves you the hassle of broken dependencies and major downloads.

Enabling this is reasonable if you want new features but don't want your system to be unstable. 

However, Ubuntu's desktop help file (in section 7.2)suggests 

> These backports are unsupported, may cause problems when installed and should only be used by people who are in desperate need of a new version of a software package which they know has been backported.

So which is right? What do backports do exactly? If someone can sum it up for me in more noob language, that would be great.

As an example which of these will happen/not happen with backports enabled/disabled:
Update from Pidgin 2.5.7 to 2.5.8
Update from Firefox v3.0.10 to v3.0.11
Update from Firefox v3.0.11 to v3.5
Update from VLC 0.99 to 1.00

The OS will have to decide what constitutes a major update, for some programs that is easy (like FF) but others iterate much faster with less obvious discrete releases even when major features are included.

---

### Post by Andy06 on 2009-07-01
Ok last post was about update options, this one is about the repos themselves. On the Ubuntu software tab in software sources, two of the options are universe and mutiverse. What is the difference between these and enabling the Jaunty partner repos ([http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner) in the second tab (third-party software)?

Aren't universe and multiverse third party themselves? What would be an examples of some software from:
1.The Universe
2.The Multiverse 
3.The third party partner repos

and what would be the basis of this difference. It would be obvious to me if the second third party tab did not exist (then universe would be all open source apps and multiverse would include those that aren't necessarily open), but the fact that a third party partner repo exists independent of these, confuses me. Sorry if they sound like useless queries. Just trying to understand how Ubuntu is organised and works behind the scenes based on its philosophies :)

Thanks a lot.

---

### Post by Andy06 on 2009-07-05
*bump*

---

### Post by drs305 on 2009-07-05
Andy, 

The multiverse repository contains "non-free" apps or apps that don't meet the Ubuntu licensing policy. The universe repository carries apps that have been tested to some degree but are not not officially supported. 

Third party repositories carry no official or unofficial endorsement from Ubuntu. The 'partner' repositories I can't comment on - obviously they are not on par with true third-party apps, since the 'partner' repositories include canonical.

Here is a link to the official explanation of the different "Ubuntu Software" repositories:
[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

Here is the community wiki, which mostly restates the above:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by Andy06 on 2009-07-05
I got that.

I'm just confused with the difference between third party on the second tab and universe/multiverse which are obviously also third party.

The other question is regarding updates, specifically Jaunty backports, the one I posted 3 posts above with this:

> As an example which of these will happen/not happen with backports enabled/disabled:

Update from Pidgin 2.5.7 to 2.5.8
Update from Firefox v3.0.10 to v3.0.11
Update from Firefox v3.0.11 to v3.5
Update from VLC 0.99 to 1.00

Can you shed some light on that.

Thanks a million

---

### Post by drs305 on 2009-07-05
Andy06,

The entries in multiverse and universe have been tested by the Ubuntu members and have been demonstrated to work reasonably well with ubuntu. They are more or less 'safe' to use but may be restricted by legal or other reasons, but not really compatablility. Think of them as "vouched for" by the ubuntu staff. I don't believe there is *any* truly commercial software located in these repositories.

The third party tab contains anything the user adds there, in addition to the 'partner' repositories. As for the Canonical partner repositories, here is one description from a company that had software accepted into the repository:

> 
Canonical offers the opt-in "partner" repository in Ubuntu to provide users with easy access to proprietary and closed-source software. The partner repository has traditionally included the Opera web browser and other free-as-in-beer software applications that are popular on the Linux platform.


As to what would be installed from your list, my guess is "all of them". I expect both FF are listed because you have two separate installs. You can see what will be updated by running the following command:
```

sudo apt-get upgrade -s

```

---

### Post by Andy06 on 2009-07-05
Hi drs305,

I asked because that is exactly what I am confused about. I had to manually add opera and could not find any single program that I would classify as being "third party" but not universe and multiverse. Having read all of the help documentation, I think I have a good understanding now of what is in Universe and Multiverse.

I *think* third party might include apps and software from these guys?:

[http://www.ubuntu.com/products/softwarecatalogue](http://www.ubuntu.com/products/softwarecatalogue)

which would perhaps explain why they are rarely encountered, the list is small and does not contain anything that can be considered very popular. A lot of it is enterprise software. Actually going to the website of the repo source turned up a lot of nothing for me.

---

### Post by Andy06 on 2009-07-05
As for the updates, I was wondering whether the unsupported updates (jaunty-backports) is for those using older then current release of Ubuntu (Intrepid, Hardy, Gutsy etc) or for those wanting newest major versions of software. 

On many threads, people have pointed out that Ubuntu only offers you security and bugfix updates for the program versions currently installed, but not for major new version.

So in theory, FFv3.0.10 will be updated to FFv3.0.11 but then FFv3.0.11 will not be updated to FFv3.5 automatically. Does enabling backports change this behaviour? 

The help documentation at:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

and the desktop help which I quoted earlier seem to sort of conflict each other, that is why I ask since all are official help sources so I don't know which one is right :D

The update cases I asked are hypothetical, not my own, it will really help in figuring out what changes.

> As an example which of these will happen/not happen with backports enabled/disabled:

Update from Pidgin 2.5.7 to 2.5.8
Update from Firefox v3.0.10 to v3.0.11
Update from Firefox v3.0.11 to v3.5
Update from VLC 0.99 to 1.00 

Of those, Pidgin never actually seems to update by default with or without backports. Firefox updates all normal version. Major version I don't know.
And apps like VLC do not increase in major version numbers despite adding major changes in some new versions, so how does Ubuntu decide wether it will update it or not?

Thanks a lot

---

