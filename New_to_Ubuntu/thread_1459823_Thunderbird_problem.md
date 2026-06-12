---
title: "Thunderbird problem"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-21
I've was playing around with debs trying to find the right version of thunderbird, and i seem to have messed things up so much that now i cant get any version of thunderbird to start at all. I've tried removing all thunderbird versions, and deleting the .thunderbird file in my home folder, i've even tried to go back stock thunderbird version in the ubuntu repos and nothing starts. 
Here is what the terminal says:
```
jamie@jamie-kubuntu:~$ thunderbird

(thunderbird-bin:15976): GLib-WARNING **: g_set_prgname() called multiple times

```

I've tried the solution posted here, but TB dosen't dosen't start
[http://ubuntuforums.org/showthread.php?t=1362942](http://ubuntuforums.org/showthread.php?t=1362942)

---

### Post by ddecator on 2010-04-22
That error tends to always show up whenever you run Firefox or Thunderbird from the terminal, and it shouldn't cause it to not start. What version of Kubuntu are you using?

---

### Post by Falc7 on 2010-04-22
Using 9.10, KDe 4.42
This is the version i would ideally like to install (karmic, 3.0.4, 64 bit):
[https://launchpad.net/~karmic-bleed/+archive/karmic-bleed-exp/+build/1654225](https://launchpad.net/~karmic-bleed/+archive/karmic-bleed-exp/+build/1654225)

---

### Post by ddecator on 2010-04-22
Hm, I just talked to the Ubuntu Mozilla Team, and there currently isn't a PPA hosted by them for the latest Thunderbird stable release, but they plan on starting one. I would recommend waiting for that since that team provides a lot of support and has worked with Mozilla products a lot.

Alternatively, you can upgrade to Kubuntu 10.04 once it is released since it has the version you want.

Otherwise, there is always the option of downloading from the Mozilla site and running it that way.

If you want help getting the stock Thunderbird install to run, you may want to try running 'thunderbird -ProfileManager' and creating a new profile, then see if it will run. If it doesn't, then we can try something else.

I'm sure this isn't the response you were hoping for, but I hope it helps!

---

### Post by Falc7 on 2010-04-22
> **ddecator said:**
> 
Otherwise, there is always the option of downloading from the Mozilla site and running it that way.

If you want help getting the stock Thunderbird install to run, you may want to try running 'thunderbird -ProfileManager' and creating a new profile, then see if it will run. If it doesn't, then we can try something else.


Thanks for your reply :)

I have tried downloading it from the mozilla site, it used to work by me just clicking the shell script named 'thunderbird' but now nothign happens when i click that.

Nothing happens why i type 'thunderbird -ProfileManager'
either. :(

---

### Post by ddecator on 2010-04-24
When you try to run Thunderbird from a terminal, does the command end, or does it hang? In other words, after you run it, do you get the Glib-WARNING message and then just a blinking cursor, or do you get jamie@jamie-kubuntu:~$ followed by a blinking cursor?

---

### Post by lidex on 2010-04-24
Bug Report;
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893")

What happens when you do this:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
```

You're not installing the thunderbird-gnome-support package are you?

---

### Post by Falc7 on 2010-04-25
> **lidex said:**
> Bug Report;
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893")

What happens when you do this:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
```

You're not installing the thunderbird-gnome-support package are you?

Nope i didn't have that installed

> **ddecator said:**
> When you try to run Thunderbird from a terminal, does the command end, or does it hang? In other words, after you run it, do you get the Glib-WARNING message and then just a blinking cursor, or do you get jamie@jamie-kubuntu:~$ followed by a blinking cursor?

I got this:
jamie@jamie-kubuntu:~$ followed by a blinking cursor


In the end i fixed it by installing the lucid RC, i needed access to TB for work emails so i thought this was the simplest way

---

