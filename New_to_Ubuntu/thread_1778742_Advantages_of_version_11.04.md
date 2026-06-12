---
title: "Advantages of version 11.04"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by rng on 2011-06-09
What are main advantages of using ubuntu version 11.04 over version 10.10 and 10.04LTS ?

---

### Post by TenPlus1 on 2011-06-09
Newer kernel, updated drivers, bug fixes...

---

### Post by Paqman on 2011-06-09
[LIST]
[*]Newer versions of lots of software
[*]It's supported for longer than 10.10
[*]New features (Unity, new bits in Software Centre and Ubuntu One, etc)
[*]Narwhals!
[*]Nattiness!
[/LIST]

---

### Post by rng on 2011-06-09
I thought these were already being done with regular updates.

I tried 11.04 livecd and I was expecting Unity interface with taskbar on left side as I had seen in images, but I got the usual gnome interface. I cannot understand this. Am I missing something simple?

---

### Post by Paqman on 2011-06-09
> **rng said:**
> I thought these were already being done with regular updates.

Nope. You get security updates and major bugfixes, but apart from that the Ubuntu repositories are pretty much set in stone. If you want new and shiny then you update every six months, if you want stable you stay with LTS and update every two or three years.

> **rng said:**
> 
I tried 11.04 livecd and I was expecting Unity interface with taskbar on left side as I had seen in images, but I got the usual gnome interface. I cannot understand this. Am I missing something simple?

If your graphics card can't do the 3D needed for Unity then it falls back on the old Gnome 2 interface. depending on what your GPU is you might find it handled Unity fine once it was installed with the graphics drivers enabled.

---

### Post by beew on 2011-06-09
> **Paqman said:**
>  If you want new and shiny then you update every six months, if you want stable you stay with LTS and update every two or three years.

No, you can install many softwares through ppa and you get pretty much the latest version. It is insane to have to either reinstall your whole OS every 6 months or use softwares fit for museum,--some don't even work.  I don't really care for "long term support" if they support craps that don't work or have important features missing.

In any case while the Ubuntu repos have a lot of softwares, many of them are crippled or outdated especially the multimedia stuffs. You get the feature complete up to date versions only from ppas (or you can compile them yourself). If it weren't for ppas I would have left Ubuntu screaming long time ago.

---

### Post by Paqman on 2011-06-09
> **beew said:**
> No, you can install many softwares through ppa and you get pretty much the latest version. 

Indeed you can.

> 
It is insane to have to either reinstall your whole OS every 6 months or use softwares fit for museum.

Well, that's how Ubuntu is. If you don't like it there are what's called "rolling release" distros, where new versions are introduced into the repos all the time.

---

### Post by rng on 2011-06-09
I have a reasonably recent computer (i3) with 4gb ram and a nvidia card. I just now read somewhere else that I should try this command to check support: /usr/lib/nux/unity_support_test -p

---

### Post by beew on 2011-06-09
> **rng said:**
> I have a reasonably recent computer (i3) with 4gb ram and a nvidia card. I just now read somewhere else that I should try this command to check support: /usr/lib/nux/unity_support_test -p

You need to install the Nvidia driver (or the Nouveau 3d experimental drivers) through Additional Drivers to get Unity working. Unity will not work out of the box if you have a Nvidia card.

---

### Post by ppv on 2011-06-09
> **rng said:**
> I have a reasonably recent computer (i3) with 4gb ram and a nvidia card. I just now read somewhere else that I should try this command to check support: /usr/lib/nux/unity_support_test -p

You might want to install the graphics driver for your nvidia. You may try the additional drivers from within Ubuntu itself or get them from the nvidia website.

---

### Post by beew on 2011-06-09
> **Paqman said:**
> Indeed you can.



Well, that's how Ubuntu is. If you don't like it there are what's called "rolling release" distros, where new versions are introduced into the repos all the time.

Perhaps, but I don't want things like Linux kernel to be "rolling". Also, I am not sure about the legality of things, it is possible that even with the newest version the softwares are still deliberately crippled for say copyright reasons, that seems to be the case with a lot of Ubuntu multimedia softwares even right after a new Ubuntu release. You can always find the uncrippled svn versions from ppas though. In any case if you use the computer for playing video and audio you'll need to at least get the medibuntu ppa for the codecs or most content simply won't play.

---

### Post by rng on 2011-06-09
So that is where the problem lies: unity does not start if nvidia card is present.

Please tell me exactly how to get and install nvidia package and use it while running livecd of 11.04.

---

### Post by beew on 2011-06-09
> **ppv said:**
> You might want to install the graphics driver for your nvidia. You may try the additional drivers from within Ubuntu itself or get them from the nvidia website.

I won't get it from Nvidia's website if I were OP. It is a pain to install and do you still need to reinstall everytime you get a kernel upgrade?

---

### Post by wolfen69 on 2011-06-09
> **beew said:**
> 
In any case while the Ubuntu repos have a lot of softwares, many of them are crippled or outdated especially the multimedia stuffs.

Give me an example of stuff in 10.04 that no longer works.

---

### Post by tgalati4 on 2011-06-09
One definite advantage:

The time you spent installing and debugging Natty meant that you were not out on the streets causing mayhem.

---

### Post by rng on 2011-06-09
I was trying to find out about ppa install and about natty. I am getting security errors for following sites: 

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)
[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)

The server's security certificate is revoked!
You attempted to reach wiki.ubuntu.com, but the certificate that the server presented has been revoked by its issuer. This means that the security credentials the server presented absolutely should not be trusted. You may be communicating with an attacker. You should not proceed.

---

### Post by beew on 2011-06-09
> **rng said:**
> So that is where the problem lies: unity does not start if nvidia card is present.

Please tell me exactly how to get and install nvidia package and use it while running livecd of 11.04.

Since Unity doesn't start you are in the classic desktop. Go to the top panel, click System > Administration > Additional Drivers. It will start and do a bit of scanning and then it will offer you the choice of activating the Nvidia driver, choose the driver and activate (and there is another choice for nouveau 3d driver, don't activate that one) It will download the driver and install it for you.

---

### Post by beew on 2011-06-09
> **wolfen69 said:**
> Give me an example of stuff in 10.04 that no longer works.

Try minitube. How about gDesklet? VLC never works in 10.04 for me. Go full screen and it freezes. Octave also does not work, have to install it from the Lucid bleed ppa. Evince was slow like molasses, it was a very old version and never got updated, finally fixed it by installing from Maverick's repo (no ppa for that) and the difference in speed and rendering is startling, got into a few dependencies problems but managed to fix them all.

---

### Post by rng on 2011-06-09
I think the driver will last only the live session. Can I download deb/package file so that I can use it after I do a proper hard disk install. Or is it a small file that can again be downloaded?

---

### Post by beew on 2011-06-09
> **rng said:**
> I think the driver will last only the live session. Can I download deb/package file so that I can use it after I do a proper hard disk install. Or is it a small file that can again be downloaded?

So you are using a live CD?

If you want the driver to stay use a live usb with persistence (in any case you need to reboot after installing the driver, so live CD is no good, after rebooting the driver is gone!)

However, if you are in a live session "Additinal Drivers" would only offer the Nouveau 3d experimental driver rather than the Nvidia closed source one. Nouveau is good enough for Unity, though not for other things that the closed source driver can do.

Once you have installed into hard disk, just run Additional Drivers like I said before, this time you will get to install the Nvidia driver.

To get  driver update add this ppa afterwards. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by rng on 2011-06-09
Coming to think of it, I have not installed driver in my current ubuntu installation of 10.10 regarding nvidia card. The video and sound are running alright but is the system taking advantage of nvidia card? How can I find this out?

---

### Post by mikewhatever on 2011-06-09
If you haven't installed the proprietary driver, it must be working with the open source one, aka nouveau. To find out if it does, look at the screen. See anything?;)

---

### Post by rng on 2011-06-09
Can you please clarify one point. Do kernel upgrades happen during regular upgrades or they occur only with new releases?

---

### Post by rng on 2011-06-09
> **mikewhatever said:**
> If you haven't installed the proprietary driver, it must be working with the open source one, aka nouveau. To find out if it does, look at the screen. See anything?;)

I see the regular desktop background.

---

### Post by mikewhatever on 2011-06-09
> **rng said:**
> I see the regular desktop background.

Darn, I was hoping for some fireworks.
The kernel gets updates, but not upgrades, same as most of the other packages. Thus 11.04 has 2.6.38, and will not get 2.6.39 which is out already.

---

### Post by beew on 2011-06-09
> **mikewhatever said:**
> Darn, I was hoping for some fireworks.
The kernel gets updates, but not upgrades, same as most of the other packages. Thus 11.04 has 2.6.38, and will not get 2.6.39 which is out already.

But you can get that from ppa. I have tried installed 2.6.38 in Maverick, didn't have any advantage on my system but sound kind of screwed up, so I logged into an older Kernel version and removed 2.6.38.

So that means even if you want kernel upgrade, there is still little reason why you must go the route of reinstalling the OS every 6 months.

---

### Post by rng on 2011-06-09
> **beew said:**
> But you can get that from ppa. I have tried installed 2.6.38 in Maverick, didn't have any advantage on my system but sound kind of screwed up, so I logged into an older Kernel version and removed 2.6.38.

So that means even if you want kernel upgrade, there is still little reason why you must go the route of reinstalling the OS every 6 months.

Can you give me idea about how to install newer kernel from ppa?

---

