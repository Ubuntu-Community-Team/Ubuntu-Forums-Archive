---
title: "A University Setup"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Wilson29thID on 2007-09-30
Greetings.

I have just installed Ubuntu on my formerly windows-xp laptop. My only experience with Linux was running Mandrake for a short time at home several years ago.

I am now trying to get Ubuntu working with my university's wireless network. I would like to point out that I have searched these forums and google extensively for pre-existing examples of this, but it seems every network is a bit different.

My network is a WPA Enterprise, PEAP, TKIP. In windows XP, you get a pop up dialogue when you are connecting that allows you to enter your username, password, and domain -- it then checks that to the school's microsoft xp logins database and lets you in.

In Ubuntu, there is no pop-up dialogue. I believe the windows-xp pop up is generating a certificate (that's just me thinking logically) and I need to generate that certificate myself on Linux.

------------------------------------

At my university's IT FAQ, it says that they do not support Linux computers at this time. I was told in IRC that something like "xsupplicant" or "wpa_supplicant" could be a work-around. Since I am new to Linux, I truly do not know how to use those tools. I have installed xsupplicant successfully, but I don't know where to go from there.

If any of you have heard of a situation like this, where the domain has to be entered to log in...or if there is anything you can think of that will help, I really appreciate this.

Unfortunately, if I can't get the internet working, I have no choice but to revert back to god-forsaken Windows :(

Thanks in advance for the help.

---

### Post by spd106 on 2007-09-30
Have you read through the HOWTO: Wireless Security sticky?

There is a PEAP example about half way through the guide, it uses CCMP rather than TKIP, but unless I am mistaken it should be a straight swap.

Incidentally I believe Ubuntu 7.10 will have much better support for this as via Network Manager 0.6.5.

---

### Post by Wilson29thID on 2007-09-30
Yes, I did check that guide out.

The main problem I'm having is that no one else in these forums has had a problem that includes the domain.

I've seen other posts that talk about the Windows XP pop-up, but they leave the "Logon domain" field blank. In my network, I have to specify the domain.

I've tried wcid too - not even that gives you a section to supply the logon domain. Where can I specify this info??

---

### Post by spd106 on 2007-09-30
I'm probably not going to be of much help as I've never used PEAP authentication.

This website goes into more detail about wpa_supplicant, so you might want to have a look, though you probably have already.
[http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=wpa_supplicant/wpa_supplicant.conf](http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=wpa_supplicant/wpa_supplicant.conf)

Can you use wpa-identity username@domain in the interfaces file?

---

### Post by Geneset on 2007-10-01
I have a similarissue but emynetwork is certificate based accessed from (on xp) funk softwares odyssey client. Any ideas how to drag the certificates out of xp into ubuntu?

---

