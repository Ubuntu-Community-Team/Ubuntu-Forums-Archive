---
title: "Network Services Bug"
date: 2016-01-31
forum: Networking &amp; Wireless
---

### Post by peter228 on 2016-01-31
Ubuntu 14.04 LTS

On Friday Jan 29 my network connection dropped without warning.  I thought it was a failed nic but wrong, investigation showed "The System Network Services Are Not Compatible With This Version".   The effect is that no networking services are supported.  If you execute 'sudo service network-manager start' you get a message that says it is running and a process id is listed.   No network connections at all though and nothing other than network proxy as an option in the Network system settings.

Google says this is no big deal and a range of solutions going back several years are presented.  Sadly they do not work.

So I did a new install having downloaded a fresh iso.  Trouble is that I can now replicate this problem.   The fresh install is no problem.  But if I then install all available updates then the same error message appears again and all network connections are gone.

It is not related to any application since I did not install any on the fresh install.   It appears immediately the system is updated.

To me this sounds like there is a fundamental problem in one of the updates that came out on Friday.  

How do I fix this?   It is not a matter of sudo apt-get upgrade since there is no Internet and from what I can see no further updates .....

---

### Post by howefield on 2016-01-31
> **peter228 said:**
> ...   It appears immediately the system is updated. .....

But not before ?

If you have the proposed repositories enabled read [this thread]("http://ubuntuforums.org/showthread.php?t=2311705").

---

### Post by peter228 on 2016-01-31
Yes, the fresh install worked properly until the updates were installed and the system rebooted.

My original install worked with all updates installed since 14.04 was first released so that is just over 2.5 years.  Something new appeared on Friday it seems .... 

I do not know if proposed items was selected in my original install but it was in the fresh install.  I will try another install and be sure to leave this unchecked.  I will post back when this next install is updated.

---

### Post by peter228 on 2016-01-31
ok so I have just completed another fresh install and then installed the updates the system proposed and then ran sudo apt-get update / upgrade to install anything else.  I left the Proposed updates unchecked.

The result is that the network is still connected.

So the conclusion is that there has to have been something too interesting in the Proposed updates .... 


Thank you for your help.

---

### Post by tobiz on 2016-01-31
This sounds like a similar issue already reported and solved, see [http://ubuntuforums.org/showthread.php?t=2311705]("http://ubuntuforums.org/showthread.php?t=2311705")

---

### Post by peter228 on 2016-01-31
Yes, most certainly sounds similar.   I did not see that thread on google when I first looked though and I wonder now if there are others having the same problem .........  I am now back to normal and rather happy about that.   Pity that this emerged as a problem in the first place though.

---

### Post by howefield on 2016-01-31
> **peter228 said:**
>  Pity that this emerged as a problem in the first place though.

That's the danger of running the proposed repository enabled. Keep it disabled (as per the default setting) for an easier life.

---

