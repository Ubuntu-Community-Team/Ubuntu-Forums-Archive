---
title: "Fingerprint reader for Lucid"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by gupta_sumesh63 on 2010-09-21
Is there any good fingerprint reader package for Lucid?
I used thinkfinger but the command [HTML]tf-tools --acquire my-name[/HTML] gives error that usb not found.
Any ideas what could be the problem?:(
I use Compaq Presario Laptop.

---

### Post by Kixtosh on 2010-09-22
> **gupta_sumesh63 said:**
> Is there any good fingerprint reader package for Lucid?
I used thinkfinger ...Try the information in this thread:

[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

But first, you should check if your device is supported.

1) Open a Terminal window and enter:```
lsusb
```

This should yield a result similar to this:```
you@yourcomputer:~$ lsusb
Bus 005 Device 002: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[B]Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
[/B]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Note the line I have highlighted in bold. Then get yourself over to this list:

[http://reactivated.net/fprint/wiki/Supported_devices](http://reactivated.net/fprint/wiki/Supported_devices)

Notice how, in that list, the numbers from my output match the numbers from the **USB Vendor ID** and **USB Product ID** columns? That is what matters, regardless of what brand of laptop is being used.

There is more reading for you here:

[https://launchpad.net/~fingerprint/+archive/fprint](https://launchpad.net/~fingerprint/+archive/fprint)

---

### Post by gupta_sumesh63 on 2010-09-23
Thanks for the reply and links
My finger reader device is not yet supported.:(
I'll wait for it to be supported.
Thanks again

---

### Post by Kixtosh on 2010-09-23
> **gupta_sumesh63 said:**
> ... My finger reader device is not yet supported.:( ...That's too bad, but to be honest, I have some reservations about using this now.

I mostly used the fingerprint reader in Win XP as a _convenience_:

- No need to type the Windows user login when starting up,
- Fingerprint reader automatically pops up when I visit websites with a username and password (fast and convenient login),
- Ability to encrypt files and protect access, _even if_ the hard drive is removed from the computer,
- And so on, and so forth ...

But from reading about it, it seems that fingerprint readers are not very secure to begin with. The convenience factor is very real for me, but the _security_ may not be what I once thought it was.

With Ubuntu, since the system is apparently so secure to begin with, I'm thinking I'll let Firefox remember my passwords securely so that I have an equal convenience factor, and maybe encrypt the "Home" folder too. This may afford me better security with almost identical convenience. I might even go as far as using the fingerprint reader for initial login only. 

The BIOS enabled password is also something I like to use when traveling, but I'm not sure if it's easy to defeat that or not. It doesn't stop your hard drive from being removed and files accessed (if they are not encrypted) but it does stop your laptop from being started or even re-installed (since it won't read any drive, or even the BIOS settings, until the password is entered).

My only issue at the moment is that I prefer to use Chromium than Firefox, and apparently Chromium does not encrypt remembered passwords, which would instinctively seem like a concern.

---

