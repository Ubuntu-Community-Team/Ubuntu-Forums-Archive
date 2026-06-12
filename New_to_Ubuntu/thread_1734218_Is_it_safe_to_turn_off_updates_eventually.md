---
title: "Is it safe to turn off updates eventually?"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-20
One thing that drew me to Linux was that I read that it didn't need as many reboots or updates as Windows, but there do seem to be an awful lot of updates for Ubuntu 10.10.

Can I eventually turn off updates?  Or do they lessen with time?

Or is turning them off just a bad idea?

---

### Post by ashickur.noor on 2011-04-20
If you have a decent Internet speed I recomamd to Update. But update is not essential. You can update the kernel when new kernel come. But you should run > sudo apt-get update once in every week. By this you will come to know about new updates.

---

### Post by beew on 2011-04-20
What is the problem? You don't need to reboot for updates in Ubuntu except for kernel and graphic card updates, even then it doesn't bug you to restart like in Windows.

---

### Post by Learning Linux 2011 on 2011-04-20
> **beew said:**
> What is the problem? You don't need to reboot for updates in Ubuntu except for kernel and graphic card updates, even then it doesn't bug you to restart like in Windows.

Well, I must be getting a ton of Kernel updates, because I have to reboot after updates all the time, it is getting rather annoying.

---

### Post by Learning Linux 2011 on 2011-04-20
In fact, thinking back on it, I *do* get a ton of kernel updates, why is that?  Is it just security fixes?
The kernel is 2.6.35, but then there is like 25, 26, 27, 28, etc. after the 2.6.35 and those seem to occur extremely frequently.

---

### Post by beew on 2011-04-20
> **Learning Linux 2011 said:**
> Well, I must be getting a ton of Kernel updates, because I have to reboot after updates all the time, it is getting rather annoying.

It is strange. I never *have to* reboot, it is just that the update wouldn't be complete until my next reboot. It is not like windows updates which constantly nag you to restart after install.Since I use laptops I eventually turn off my computers anyway. 

I am talking about kernel updates, for most other things the updates would just take place when the computer is on. 

Unless you are one of those people who never turn off their computers that shouldn't be a problem. :)

---

### Post by ikt on 2011-04-20
> **Learning Linux 2011 said:**
> In fact, thinking back on it, I *do* get a ton of kernel updates, why is that?  Is it just security fixes?

Majority of updates are security fixes yeah.

When you muck around with Ubuntu Development releases you notice the difference in updates.

After not using your computer for a week there's over 500MB worth of data to be downloaded, with this in mind regular updates on ubuntu are quite tame, especially since a lot of them don't require a restart.

That said there was a period a month or so ago where ubuntu 10.10 got a lot of 'restart to complete upgrade' updates, which is turning into a habit of mine, I get the 'feeling' I need to reboot to complete updates even if the reboot isn't required.

edit: just to clarify, no it's not safe to turn off updates, updates are the one thing that is absolutely crucial to do across all software and all software platforms.

---

### Post by Elfy on 2011-04-20
Do you have proposed and backport repos enabled? If you do that might be why you get as many as you do. 

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates%20Tab)

---

### Post by ikt on 2011-04-20
> **forestpiskie said:**
> Do you have proposed and backport repos enabled? If you do that might be why you get as many as you do. 

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates%20Tab)

Good call, I had completely forgotten about those!

---

### Post by Rasa1111 on 2011-04-20
> **beew said:**
> What is the problem? You don't need to reboot for updates in Ubuntu except for kernel and graphic card updates, even then it doesn't bug you to restart like in Windows.

Yeah for sure.
I hardly ever have to reboot after updates. 
Just once in a great while for things like you mentioned. 

I also don't get a lot of updates these days. 
Maybe once every couple weeks it seems, lately.

The updates are also very easy, and do what they should and let you get on with it,
unlike windows updates. lol

One selling point for me was also not having those rubbish windows updates constantly, that only seemed to finish once in awhile. 

 Then when I switched to Ubuntu..
i learned that one still should do crucial updates when required,
but it is not at all a P.I.T.A. like windows. 
Not for me anyway.
 I barely notice it. 

But since Ubuntu.. it's weird.. i have learned to actually *like*, and appreciate updates when I get them! :o lol 
:lol:

---

### Post by HermanAB on 2011-04-20
Howdy,

If you have to ask, then you should keep it on...

I hardly ever do updates.  I rather re-install from scratch once in a while.  The choice is yours.  Nobody is forcing you to do updates.

---

### Post by grahammechanical on 2011-04-20
I always choose to restart later and carry on working. I am trying out 11.04 Beta so I am not surprised to get daily updates, some of which do not take affect until a restart is done.

I also wonder if there is a policy to improve 10.10 up to 11.04 quality for those people who will choose not to change to 11.04. I wonder about this because over the last few days there have often been updates for my 10.10 installation. Perhaps it is just the super diligence of the maintainers of the repositories in keeping an outgoing version as up to date as possible. We have a lot to be thankful for. The people doing this work for us are volunteers as far as I know.

Regards.

---

### Post by Locke_99GS on 2011-04-20
The Linux kernel is able to be updated in RAM on-the-fly, concurrently with on-disk updates. See here.
[http://www.ksplice.com/](http://www.ksplice.com/)

Yes this works just fine. I've used it in the past, but I usually turn of my PC while I'm away, so don't use have a real use for it anymore. Perhaps if I suspended my PC, rather than rebooting, then this could still be beneficial to me.

---

### Post by Rasa1111 on 2011-04-20
> **grahammechanical**~I also wonder if there is a policy to improve 10.10 up to 11.04 quality for those people who will choose not to change to 11.04.

I don't know..
But I would really love to get the minor changes made to 11.04's sound menu in my 10.10! lol

It's not much of a change..
But it is one I like very much! <3

---

### Post by Learning Linux 2011 on 2011-04-20
.

---

### Post by Learning Linux 2011 on 2011-04-20
> **forestpiskie said:**
> Do you have proposed and backport repos enabled? If you do that might be why you get as many as you do. 

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates%20Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Updates%20Tab")

No, I don't have those enabled.

The recommended updates are enabled though, maybe those are where most of the ones I am getting are coming from.


I also set the updates to weekly, that should lessen the frequency.  I could also go to two week intervals.

---

### Post by Fraoch on 2011-04-20
> **grahammechanical said:**
> I also wonder if there is a policy to improve 10.10 up to 11.04 quality for those people who will choose not to change to 11.04. I wonder about this because over the last few days there have often been updates for my 10.10 installation. Perhaps it is just the super diligence of the maintainers of the repositories in keeping an outgoing version as up to date as possible. We have a lot to be thankful for. The people doing this work for us are volunteers as far as I know.

10.10 is supposed to be supported until April 2012, so it should still be getting security updates up until that time.  Heck, 9.10 is still supported until the end of this month.

I believe a lot of the updates are not specifically for 10.10, they are system-wide, affecting all supported versions (9.10, 10.04, 10.10 and perhaps for 11.04 where they're not superseded by newer packages).  I've seen a few "backported to Maverick" comments on some of the updates.  Some of these updates might even be coming from Debian, not sure though.

At any rate, lots of updates is a *good* thing.  Developers are keeping on top of security risks and making sure all systems are fully patched against threats.  Bugs are getting squashed and things are generally getting more stable.

And yes, only kernel updates need a restart.  There have been a lot of kernel updates for Maverick.  Also not a bad thing, hardware compatibility improves a little bit each time the kernel is updated.

---

### Post by cmcanulty on 2011-04-20
put this alias in your bash.rc file and run it once a day. All you do is type ud in terminal and then your password when prompted. It even fills out yes options. Very fast and easy. Also cleans up.Much faster than update manager
```
alias ud='sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get clean -y'
```

---

