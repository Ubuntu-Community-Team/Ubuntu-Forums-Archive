---
title: "n00b questions"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by nyxn00b on 2009-11-10
I just installed 9.10 and had a few questions:

When I installed Wine (Dev) & the nVidia 185? (Newer/recommended) drivers for my computer I'm getting some games that are giving me trouble. I know these should work since they worked with OpenSUSE when I tested it. To be fair I don't remember the drivers I D/Led for nVidia for OpenSUSE. (But they were the binary ones from the site a few weeks ago) There's been talk of using the 190 drivers and how to do that but when I try the suggestions I end up with a strange mix of 185/190 components in Synaptic Package Manager.

How come **su** don't work? Or at least doesn't work with my password that works with **sudo -i**?

I've got a 2 disk lvm array set up in OpenSUSE I didn't know needed to be exported. What's the best tool to use to deal with that?

When I first tried Ubuntu, I added a second user and then D/led icewm. My intention was that icewm would be used by the 'user' account while mine would stick with gdm, but it seems Ubuntu removed gdm and then installed icewm. Does Ubuntu by default only allow one manager at a time on the system?

Thanks!

---

### Post by rygar on 2009-11-10
> **nyxn00b said:**
> 
How come **su** don't work? Or at least doesn't work with my password that works with **sudo -i**?


Ubuntu does not enable root access by default, so "su" won't work.  If you want to use a shell as root, you can use "sudo -i" as you suggest, or "sudo su".  Most people suggest just typing "sudo" before every command you enter, rather than enter root mode, but i understand sometimes it's easier to be root...

If you really want to set up a root account, type "sudo passwd root" and it will prompt you for a new root password...  but as mentioned, there's really no need to do this.

---

