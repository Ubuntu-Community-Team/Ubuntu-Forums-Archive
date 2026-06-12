---
title: "how to upgrade software?"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by sallam on 2010-12-08
Greetings

I just checked and found that Transmission has a new version (2.12) while the one I have is 2.04
Somehow ubuntu doesn't update this program.
How do I go about updating it? should I download the latest release and install it myself? or is there  better way?
And, in general. how do you guys update your software?
is there any automatic update tool for software that ubuntu doesn't auto-update?
or can we add them manually somehow to ubuntu updating system?

---

### Post by philinux on 2010-12-08
> **sallam said:**
> Greetings

I just checked and found that Transmission has a new version (2.12) while the one I have is 2.04
Somehow ubuntu doesn't update this program.
How do I go about updating it? should I download the latest release and install it myself? or is there  better way?
And, in general. how do you guys update your software?
is there any automatic update tool for software that ubuntu doesn't auto-update?
or can we add them manually somehow to ubuntu updating system?

Personally I cant be bothered with the latest and greatest. I'm happy to stick with the repo version. If you enable the backports repo some newer stuff does come through. If you really want the latest then ppa's are the way to go for now. [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

[http://www.omgubuntu.co.uk/2010/11/transmission-2-12-release-ppa/](http://www.omgubuntu.co.uk/2010/11/transmission-2-12-release-ppa/)

---

### Post by gdonwallace on 2010-12-08
Depending on how long that update has been available, it may not be in the repositories yet.  Before anything gets put into the repo's it has to go through testing to ensure that the update does not break anything or have any additional file requirements.  Once the testing is done, it will be pushed into the repos and the update will come down.

You can update it yourself, but that pulls you out of the testing / update cycle for that program from Ubuntu.  Any potential issues would be on You to solve at that point.  Although that should be fairly easy with google and the forums.

---

### Post by sallam on 2010-12-08
Thanks for your reply.
My English is not that good, so could you help me understand words like: "repo" an "backports" please?

---

### Post by sallam on 2010-12-08
gdonwallace, Many thanks for the info. Wow, I didn't know that about the ubuntu repositories. Then one should better wait and not try to upgrade himself. But, how do I know if a specific program is maintained by the repositories or not? is there a way to know what ubuntu auto-updates and what it doesn't? does Transmission eventually gets auto-updated without doing anything from my side?

---

### Post by philinux on 2010-12-08
> **sallam said:**
> Thanks for your reply.
My English is not that good, so could you help me understand words like: "repo" an "backports" please?

For backports see this. Your English is very good by the way.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Toxicbits on 2010-12-08
The Ubuntu repository usually doesnt contain the latest versions of application, if you want to use them its the easiest way to add an additional PPA (repository) in your software center. You should find the address on the project page.

---

### Post by gdonwallace on 2010-12-08
The easiest way to tell if a program is maintained by Ubuntu is through the Software Store.

Any program that can be installed through that will tell You if it is maintained or not.  Just look at the description of the program, the last thing in the description will tell you if it is maintained or how long it will be maintained by Ubuntu.

FYI - Your English is just fine. ;)

---

