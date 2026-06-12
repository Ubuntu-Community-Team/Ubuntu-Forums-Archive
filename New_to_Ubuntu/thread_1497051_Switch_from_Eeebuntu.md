---
title: "Switch from Eeebuntu?"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by jonkanon on 2010-05-30
Hello, I tried to search for existing threads with no luck (but I'm sure they're out there...) so help is very much appreciated.

I have this Asus Eee PC with Eeebuntu installed. For various reasons I'm getting a bit tired of the Eeebuntu-system and I'd rather change to a "normal" Ubuntu. So my main question is how do I do this? Since it has no CD-reader?

Also, should I be warned - it there a big problem with normal ubuntu on Eee-hardware? Like I said I'm tired of Eee, there are a couple of things that don't work, so in that case it must be strong arguments for not switching - not minor.

Sorry for bad English. And thanks.

EDIT: Model Eee PC 900, 16 GB SSD, 1 GB DDR2, Intel

---

### Post by Irihapeti on 2010-05-30
I have the same model of EeePC as you, and I've only ever run standard Ubuntu on it.

Currently I'm running 10.04. Yes, there are one or two minor things, such as some function keys (not all of them) not working and a tweak that I have to add to Grub to deal with a graphics problem. I haven't tested the microphone because I never use it, so can't comment on that. Nor have I used wireless for any length of time, either.

Ultimately, you need to test it for yourself. If you have a spare 4GB SD card, you can put it in the card slot and install to that. It will be a bit slow, but it should still give you an idea if it's going to work well enough for you. Once you are happy with that, you can install to the main drive.

To install, use unetbootin to create a bootable USB stick from the .iso image, and boot from that.

---

### Post by jonkanon on 2010-05-30
Thanks!

---

### Post by Jakiejake on 2010-05-30
> **jonkanon said:**
> Hello, I tried to search for existing threads with no luck (but I'm sure they're out there...) so help is very much appreciated.

I have this Asus Eee PC with Eeebuntu installed. For various reasons I'm getting a bit tired of the Eeebuntu-system and I'd rather change to a "normal" Ubuntu. So my main question is how do I do this? Since it has no CD-reader?

Also, should I be warned - it there a big problem with normal ubuntu on Eee-hardware? Like I said I'm tired of Eee, there are a couple of things that don't work, so in that case it must be strong arguments for not switching - not minor.

Sorry for bad English. And thanks.

EDIT: Model Eee PC 900, 16 GB SSD, 1 GB DDR2, Intel

Use A USB Flash Drive
Or An External HDD

---

### Post by Jakiejake on 2010-05-30
[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/]("http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/")

---

### Post by formaldehyde_spoon on 2010-05-30
> **Irihapeti said:**
> I have the same model of EeePC as you, and I've only ever run standard Ubuntu on it.

Currently I'm running 10.04. Yes, there are one or two minor things, such as some function keys (not all of them) not working and a tweak that I have to add to Grub to deal with a graphics problem. I haven't tested the microphone because I never use it, so can't comment on that. Nor have I used wireless for any length of time, either.

Ultimately, you need to test it for yourself. If you have a spare 4GB SD card, you can put it in the card slot and install to that. It will be a bit slow, but it should still give you an idea if it's going to work well enough for you. Once you are happy with that, you can install to the main drive.

To install, use unetbootin to create a bootable USB stick from the .iso image, and boot from that.

Microphones not working with Eee/Ubuntu is common.

To fix: there are two microphone 'channels' (or two microphones? I dk) you need to set one of them to 100%, and the other to 0%.
There are probably many ways to do this, but one way is to install padevchooser, open the pulse audio vol control in Sound&Video, then unlock the sync between mic channels, and put one down to 0.

---

