---
title: "Update Manger not updating 8.04LTS kernel"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by jivabill on 2010-11-10
Friends of mine bought a new Dell 530 desktop.  It has 8.04LTS loaded on it.  After some months they are having trouble with Adobe Flash.  On investigation I find that their system is still running the same version of the Linux kernel as when the machine was delivered.  

Their Dell 530 running 2.6.24-16
My 8.04LTS machine is now running 2.6.24-28

How can I make their machine start updating the kernel?

thanks any help
bill

---

### Post by Hippytaff on 2010-11-10
you can do
```

sudo apt-get dist-upgrade

```
but I'm not sure if this will attempt to upgrade the version of ubuntu as well as the kernel

---

### Post by spiky001 on 2010-11-10
Have a look here [http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/](http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/)

---

### Post by snowpine on 2010-11-10
This has always worked for me:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot
```

---

### Post by spiky001 on 2010-11-10
Just a Q, I have karmic can I update to the latest meerkat kernal will this cause problems? will all old distros upgrade to latest kernal  without problems?

---

### Post by theozzlives on 2010-11-10
8.04's life ends in April of 2011. You might consider an upgrade to 10.04 (the current LTS).

---

### Post by Hippytaff on 2010-11-10
> **theozzlives said:**
> 8.04's life ends in April of 2011. You might consider an upgrade to 10.04 (the current LTS).

I'll second that :-)

---

### Post by jivabill on 2010-11-10
Hello to all and thank you for your replies.

My friends do not at the time want to upgrade to 10.04LTS.  They just want the update manager to be updating their kernel.  One of my machines is running 8.04LTS and it is updating the kernel along with other updates just fine.  Something is wrong with the settings or something in their machine.  Seems like it may have something to do with the machine having been pre-loaded with the OS by Dell.

I tried to find out how to check the configuration settings for update manager and got nowhere, the help file seems to be empty on that subject.  Googling on the net and searching these forums was not productive either.

One other thing:  I have one of my machines running 10.04 and  I am not at all pleased with 10.04 because the developers left out a number functionalities that, for example, 8.04 had.  Also the later version of Thunderbird Mail has two bugs in it that the developers there have not seen fit to fix and they are annoying bugs.

So for my friends part they are happy with 8.04LTS except for this kernel update problem.  They will cross the upgrade bridge when they come to it.  Hence the desire to fix the update manager problem.

That is the whole story, thanks again for your inputs.
Bill

---

### Post by jivabill on 2010-11-10
Hi Spiky001,  Thanks for your suggestion.  I had already looked at the repository using Synaptic and see all the Linux Images there.  

I can install the latest version of 8.04LTS of course as you suggest.  But that likely will not fix the underlying problem that Update Manager is not doing the regular updates of the kernel.

So I was trying to find out how to change the settings (if they are wrong) on Update Manager so it work correctly.

Anyway, that is my dilemma. Thank you again for your help.
bill

---

### Post by jivabill on 2010-11-29
Well, after much discussion with the friends they agreed to installing 10.04LTS which, of course, fixed the updating problem.  I note that Update Manager in 10.04LTS has various features that can be tweaked to suit one's preferences about updates.  So that is a good improvement.  So the problem is solved, or rather avoided by the move to 10.04LTS.

Thanks everyone for the input, suggestions, and help.

---

