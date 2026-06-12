---
title: "Slow copy speeds from samba to Vista"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Cadmus on 2008-05-21
Hello

I've recently had to move and my little media centre (previously Feisty, totally reinstalled with Hardy) now has to run on wireless, and my main machine now runs on copper. That's all working and download speeds are good from the internet.

My problem comes when I try to copy stuff from a samba share on the media centre to my local HD, speeds are very slow, always levelling out at 100kb/s.

The wireless card is an rt61 based card (an Edimax EW-7128G) which came highly recommended. Here's what I have so far in terms fo tests:
[LIST=1]
[*]Both machines get excellent speeds from the internet, close to my ADSL maximum
[*]Drivers are the very latest for the NIC on the Vista box
[*]Speeds are the same through rsync in Cygwin, using both the share (//mediacentre/blah) and direct (user@mediacentre/blah)
[/LIST]

Here's what's confusing me...
[LIST]
[*]If it was a problem with the NIC or Vista it would affect net access too
[*]If it's a compatibility problem with Vista and Samba then why is it as slow doing it through rsync proper (avoiding smb protocol)
[*]If it's a problem with my router (Thompson Speedtouch 585) why didn't it happen before when the wired/wireless was reversed?
[*]If it's a wireless on ubuntu problem why are net speeds fine?
[/LIST]

I just can't think of why this is happening, has anyone had this or knows why this is happening?

---

### Post by Cadmus on 2008-05-22
Hmm, it seems a lot of people are having problems with samba and the specific NIC in my vista machine (Realtek 8111B), but they're still getting MB/s, which is an order of magnitude better than I'm seeing. I may have to dig out an old copper PCI NIC and put that in, see if it goes.

---

