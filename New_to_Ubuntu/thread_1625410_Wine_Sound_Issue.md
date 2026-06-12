---
title: "Wine Sound Issue?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by unplas7icated on 2010-11-19
Hello everyone,

I'm new here and a Linux newbie. There has hardly been a problem with the OS (other than the screw ups I brought upon it through tinkering here and there) since I started using Ubuntu. About two weeks back, I had to start using Wine to run the Rosetta Stone language learning software. (My PC can't support VMs.)

Soon as I started, Wine started crashing my sound system mightily. Initially, I would get pulseaudio error messages in the terminal and would have to reboot to make it work. Going to "Sound" on preferences would give me a message, "Waiting for sound system to respond." But it never did.

Then finally I got tired of it crashing everytime the s/w used speech recognition, and, as suggested by someone somewhere, uninstalled pulseaudio and used alsa for Wine. Obv, that backfired big time and lost my entire system's sound. So I reinstalled the drivers through this command:

> sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

Now sound was back, but the software is still crashing my sound system everytime there's a little microphone use. 

//As a sidenote, people on the torrent's download link reported there to be a virus in the patch. I'm not sure if that could be relevant.

I use this command everytime it crashes, and it works fine, but it crashes without much ado soon enough:

> sudo alsa force-reload

Here is a screenie of the error message at the crash:

[IMG]http://img809.imageshack.us/img809/8466/rsunderwine.png[/IMG]


I would appreciate any input, since my language learning program will go on for some months, and I don't want my system suffering.


PS - Sorry if I was needlessly descriptive. I have no idea what is relevant here.

---

### Post by unplas7icated on 2010-11-19
It turns out this isn't a Wine/Linux issue. Just a Rosetta Stone issue.
[http://www.languagelearningblog.com/rosetta-stone-faq-microphone-setup-screen-error.html](http://www.languagelearningblog.com/rosetta-stone-faq-microphone-setup-screen-error.html)

The "fix" described doesn't work, so I guess will have to live with it.

My apologies.

---

### Post by unplas7icated on 2010-11-19
Hmm and the bug has been reported with Wine [here]("http://wine.1045685.n5.nabble.com/Bug-19310-New-Regression-in-running-Rosetta-Stone-v3-with-version-1-1-25-td1638285.html") with no success.

---

