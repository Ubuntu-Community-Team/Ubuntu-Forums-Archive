---
title: "Uninstall and Fresh Install"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Curt1944 on 2011-04-28
I searched for something like this on here but I couldn't find something that really explained how to go about doing what I want to do.

Right now I am still running Ubuntu 10.04 alongside Windows 7.  Ubuntu was originally installed from a DVD (I didn't use the Windows Installer application).

I want to to upgrade my Ubuntu to 11.04, but I want to do a completely fresh install, I don't even want to keep my /home folder (I'm just going to backup the files I want to keep).  I've done a fair bit of messing around with my current installation and I just want a fresh, clean one.

What is the best way to go about completely clearing off Ubuntu (formatting the partition?) and installing the new version.

Sorry if this is has been asked here before, Thanks.

---

### Post by Hedgehog1 on 2011-04-28
Download the new Natty ISO and make a LiveCD/LiveUSB.

Here are your install options (not all will appear depending on the state of your partitions when you run it):

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

You want the 3rd option - to erase Ubuntu and reinstall.


***The Hedge***

:KS

---

### Post by Billabong81 on 2011-04-28
Strange, my options were:
1. Delete 10.10 and fresh install
2. Upgrade to 11.04
3. Format entire hard disk and fresh install

OP, if your options are like mine, you want to select #1, not #3!

---

### Post by Elfy on 2011-04-28
> **Hedgehog1 said:**
> Download the new Natty ISO and make a LiveCD/LiveUSB.

Here are your install options (not all will appear depending on the state of your partitions when you run it):

You want the 3rd option - to erase Ubuntu and reinstall.


***The Hedge***

:KS

Will that particular bit of wizardry note that the OP is using 10.04.

I'm always wary of these new fangled options ... particularly in light of the recent installer faux pas ;)

@ @Curt1944 - what you need to do is look at the options you are given and if you are not sure - ***_ask_***.

Personally I'm a do it manually and tell the installer exactly what I want it to do.

If you have a non-default install - that is one that has more than just / you'd certainly be needing to look at your existing partition setup.

---

### Post by Curt1944 on 2011-04-29
Thanks for the replies.  This are the options I get when I boot from the live DVD and start the install:

[[IMG]http://img594.imageshack.us/img594/8061/screenshotkn.png[/IMG]](http://img594.imageshack.us/i/screenshotkn.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Remember that I am currently running 10.04 and not 10.10.  What should I do from here?

Also (not sure if this is the place to ask this question), when I boot my computer It goes into Windows Boot Manager with the options of either Windows 7 or Ubuntu.  When I select Ubuntu it goes into GRUB4DOS and I have to select Ubuntu from there before it will begin booting.  Is there a way to get rid of GRUB4DOS?

---

### Post by Elfy on 2011-04-29
> **Curt1944 said:**
> Thanks for the replies.  This are the options I get when I boot from the live DVD and start the install:

Remember that I am currently running 10.04 and not 10.10.  What should I do from here?

Also (not sure if this is the place to ask this question), when I boot my computer It goes into Windows Boot Manager with the options of either Windows 7 or Ubuntu.  When I select Ubuntu it goes into GRUB4DOS and I have to select Ubuntu from there before it will begin booting.  Is there a way to get rid of GRUB4DOS?

Pick - something else.

Right click on the existing install partition - edit partition - set moutpoint as / - format

(If you also have a /home partition - edit partition - set mountpoint as /home - format)

If you want ubuntu to control the boot allow it to install bootloader to the default - you shouldn't need to do anything to accomplish that.

Proceed.

---

