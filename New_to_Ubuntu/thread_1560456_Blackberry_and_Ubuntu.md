---
title: "Blackberry and Ubuntu"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-08-24
I have been using Ubuntu for over 6 months now and I love it and cannot think of switching back to Winblows. However, often we find ourselves forced to do so due to software and apps that simply aren't available in Linux versions.

I am a hooked Blackberry user and a real bane for me is the inability to run Blackberry Desktop Software on Ubuntu. Of course, a Linux version does not exist. The frustrating part is that it won't run under Wine either.

So how do we make it work.

For starters, there is a way to satisfy the most basic, most important need of Blackberry users - CHARGING & BACKUP.

Charging is pretty simple. Just hook your Blackberry up to the USB port. In Ubuntu 10.04, it just charges automatically. In case you find that the Blackberry is not charging:

Open up Synaptic Package Manager and run a search for "barry". Amongst the list that pops up, install the "barry-util" and "barrybackup-gui" packages.

Open a terminal window (CTRL+ALT+T) and type in "bcharge". Your device should start charging.

BACKUP & RESTORE:

Another very simple process. Earlier, you installed the "barrybackup-gui" package. Chances are this application does not show up in your "Applications" menu. Don't worry, it's there.

You can either add it to the menu manually, the custom command being "barrybackup", or you can run the application by opening up a terminal window and typing in "barrybackup".

The program will detect your Blackberry automatically, and will backup important information such as contacts, messages, preferences etc with the click of a button. You can delve a little deeper by exploring the settings options to customize a backup directory and preferences as to what you want to include/exclude from the backup and restore.

Restoring is equally easy and can be done with the click of a button.

Another way to backup contacts is using Ubuntu One. Go to the Sytem Menu >> Preferences >> Ubuntu One and it's pretty self explanatory from there. In the mobile setup, you can set your Blackberry up. On your phone, you need to download the Funambol Blackberry Sync application which allows you to backup your contacts, Calendar, Tasks & Notes online directly into your Ubuntu One account. Ubuntu One has instructions on how to do this and is very easy to follow.

Other than this, I have not been able to figure out much more about how to really use a Blackberry with Ubuntu. It would be great to have the Desktop Manager will all it's features in a Linux version. Let's hope the Barry Project develops further and very soon can make Ubuntu and Blackberry fully compatible with each other.

---

### Post by LiquidMeson on 2010-08-24
Blackberry and Ubuntu. You sir have brightened my day. However android has most likely destroyed any hopes of further blackberry linux dev. There are some good texting android on the rise though, if you have the money I'd recommend a switch. Android has cookies.

---

### Post by adduds on 2011-01-07
great post!

---

### Post by Chris11 on 2011-01-07
thank you for the post.. but it does not work for me...

typing barrybackup and after flashing up the Barry Windows for a second, I got the following message...

> chris@chris-desktop:~$ barrybackup
barrybackup: symbol lookup error: barrybackup: undefined symbol: _ZN5Barry10ControllerC1ERKNS_11ProbeResultE


any help is appreciated, thanks, Chris

---

### Post by lzy2k1 on 2011-01-10
Thank you very much!

---

### Post by [Snc] on 2011-01-10
Great post! :D

Another way to run BlackBerry desktop software is to have a virtual machine with windows present or a dual boot with windows.

---

