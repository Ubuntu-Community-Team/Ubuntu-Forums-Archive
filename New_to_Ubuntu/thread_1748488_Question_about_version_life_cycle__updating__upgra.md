---
title: "Question about version life cycle / updating / upgrading"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-05-03
Hi All,

I've got a couple of questions I hope someone will be kind enough to answer.

I'm using 10.10.  I tried 11.04 for a couple of days and tried to like it.  I really did.  I just really prefer Gnome and I have 10.10 tweaked so nicely. (Remastersys made it very easy to go back to 10.10).

I know I could use Gnome classic in 11.04, but I don't see the point. (Plus a few programs didn't *seem* to work as well as they do in 10.10.) 

My question is, how long will I be able to receive updates for 10.10?  At some point will I just be out of luck?  Will all updates cease to be offered or just the core of the OS?
How does it work?

---

### Post by andrewthomas on 2011-05-03
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Maverick EOL April 2012

---

### Post by GrouchyGaijin on 2011-05-03
> **andrewthomas said:**
> [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Maverick EOL April 2012

Thanks

---

### Post by eldiabolosk on 2012-03-07
It is March 7th 2012 and since March 5 I am getting and error message that repositories are no longer available. I thought that they would be available at least for few more weeks or a month +. Anybody has any idea why?

---

### Post by plucky on 2012-03-07
> **eldiabolosk said:**
> It is March 7th 2012 and since March 5 I am getting and error message that repositories are no longer available. I thought that they would be available at least for few more weeks or a month +. Anybody has any idea why?

It could be your repository is down.Open Software Sources and change your server to MAIN and see if it now updates.

What error do you get?

---

### Post by jerome1232 on 2012-03-07
A copy/paste of the output from the code below would be useful```
sudo apt-get update
```

---

### Post by eldiabolosk on 2012-03-07
sudo apt-get update:

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by eldiabolosk on 2012-03-07
Does end support April 2012  mean beginning or end of April?

---

### Post by snowpine on 2012-03-07
> **eldiabolosk said:**
> sudo apt-get update:

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

These are not official Ubuntu repositories, you'll have to go on Launchpad and see what's what with these PPA's (or just remove them from your software sources).

---

### Post by eldiabolosk on 2012-03-07
Thank you.  done that and it worked. 

My main concern is that Since I don't like Unity and 11.10 (upgrading to due to soon EOL of 11.04 makes no sense) does not has Synaptic by default (They say you can still install it) How a situation like this one is this going to be addressed? 

Deo anybody know about a stable no pain pure GNOME distro? I may say GB to Ubuntu after 6 or 7 years.

---

### Post by eldiabolosk on 2012-03-07
> **snowpine said:**
> These are not official Ubuntu repositories, you'll have to go on Launchpad and see what's what with these PPA's (or just remove them from your software sources).

Removed.
sudo apt-get clean
sudo apt-get update

 Worked.


Thanks guys

---

### Post by eldiabolosk on 2012-03-07
> **GrouchyGaijin said:**
> Hi All,

I've got a couple of questions I hope someone will be kind enough to answer.

I'm using 10.10.  I tried 11.04 for a couple of days and tried to like it.  I really did.  I just really prefer Gnome and I have 10.10 tweaked so nicely. (Remastersys made it very easy to go back to 10.10).

I know I could use Gnome classic in 11.04, but I don't see the point. (Plus a few programs didn't *seem* to work as well as they do in 10.10.) 

My question is, how long will I be able to receive updates for 10.10?  At some point will I just be out of luck?  Will all updates cease to be offered or just the core of the OS?
How does it work?


Did you find a solid GNOME based distro? Tried many so far including Debian and did not like any.

Will appreciate your reply.

Ed.

---

### Post by snowpine on 2012-03-07
> **eldiabolosk said:**
> Thank you.  done that and it worked. 

My main concern is that Since I don't like Unity and 11.10 (upgrading to due to soon EOL of 11.04 makes no sense) does not has Synaptic by default (They say you can still install it) How a situation like this one is this going to be addressed? 

Deo anybody know about a stable no pain pure GNOME distro? I may say GB to Ubuntu after 6 or 7 years.

Unity is unique to Ubuntu and is 100% optional. You can install "pure GNOME" in any distro (including Ubuntu).

---

### Post by eldiabolosk on 2012-03-07
> **snowpine said:**
> Unity is unique to Ubuntu and is 100% optional. You can install "pure GNOME" in any distro (including Ubuntu).

Is that right? The link from this thread: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases) does not indicate that for 11.10.

---

### Post by jerome1232 on 2012-03-07
You can install gnome-shell right along with unity, you can also install a gnome-fallback mode that's very similar to gnome 2

---

### Post by yetiman64 on 2012-03-07
> **eldiabolosk said:**
> ...My main concern is that Since I don't like Unity and 11.10 (upgrading to due to soon EOL of 11.04 makes no sense) does not has Synaptic by default (They say you can still install it) How a situation like this one is this going to be addressed? ....

If you want to install synaptic, after doing the new install (including updates and hardware drivers if needed etc), open a terminal (use the keyboard combination, CTRL + ALT + T, to open the terminal) and put in the command,

```
sudo apt-get install synaptic
```Put in your user password when asked, the terminal won't show anything but it is going in (a security measure), press enter and let the terminal do its work. Once finished you can open synaptic from the Dash search function. Type "synaptic" in, without the quotes, and click on the icon for it when it shows up.

Cheers, yetiman64

---

### Post by jerome1232 on 2012-03-07
Synaptic is installed by default, I never installed it yet it is here on my system ;)

---

### Post by yetiman64 on 2012-03-07
> **jerome1232 said:**
> Synaptic is installed by default, I never installed it yet it is here on my system ;)
Are you sure it was 11.10 your installing? :)  It wasn't on at least 3 installs I've done so far. Will look into this some more, I know I definitely had to install it.

Yep, there it is,

> **[SIZE=2]Note for 11.10 release and above[/SIZE]**

 **Synaptic** is no longer installed by default in Ubuntu 11.10, however it is still useful in some situations. From [[COLOR=Blue]--here--[/COLOR]]("https://help.ubuntu.com/community/SynapticHowto").

Regards, yetiman64

---

### Post by jerome1232 on 2012-03-07
> **yetiman64 said:**
> Are you sure it was 11.10 your installing? :)  It wasn't on at least 3 installs I've done so far. Will look into this some more, I know I definitely had to install it.

Yep, there it is,

From [[COLOR=Blue]--here--[/COLOR]]("https://help.ubuntu.com/community/SynapticHowto").

Regards, yetiman64

I stand corrected, I guess I must have installed it without thinking about it.

---

### Post by ixtok on 2012-03-07
> **eldiabolosk said:**
> Thank you.  done that and it worked. 

My main concern is that Since I don't like Unity and 11.10 (upgrading to due to soon EOL of 11.04 makes no sense) does not has Synaptic by default (They say you can still install it) How a situation like this one is this going to be addressed? 

Deo anybody know about a stable no pain pure GNOME distro? I may say GB to Ubuntu after 6 or 7 years.

You might like "linux mint", there has been quite a bit of migration to it from ubuntu since the appearance of Unity.

---

