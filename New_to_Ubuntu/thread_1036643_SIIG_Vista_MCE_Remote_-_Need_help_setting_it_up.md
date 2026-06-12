---
title: "SIIG Vista MCE Remote - Need help setting it up"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by MockY on 2009-01-11
I just bought a SIIG Vista MCE Remote, thinking it would work fine with Lirc. But I seem to have issues with it. All guides lists many different MCE remotes, but none looks quite like mine.

This is the output lsusb gives me:
```
Bus 001 Device 002: ID 147a:e017 Formosa Industrial Computing, Inc.
```
I successfully installed Lirc, but I am not really sure what to choose from when the config prompt comes up.
I run sudo dpkg-reconfigure lirc and choose **Windows Media Center Remotes (new version Philips et al.)** since it is after all a new remote. I choose **None** on the IR transmitter prompt. When that is done Lirc refuses to successfully start and gives me:
```
 Starting remote control daemon(s) : LIRC   [[COLOR="Red"]fail[/COLOR]]
```
However, if I run through the setup again and choose **Windows Media Center Remotes (old version MicroSoft USB ID)**and none on the IR reveiver prompt, Lirc starts successfully. The light on the receiver is not contant red as if I am constantly pressing a button. I tried the remote in Boxee and MythTV and it does not work.

Could someone please help me with this?
Thanks.

---

### Post by MockY on 2009-01-11
Upon reboot, the remote now works in Boxee and GeexBox, but it does not work in MythTV. Any ideas to why and how I go about and fix it?

---

### Post by lostPenguin20 on 2009-06-22
Would you mind sharing your configuration?  I am not able to get the SIIG Vista MCE remote working with Boxee.  Yes I have installed LIRC, but not sure if my setting/config are correct.
 
Thanks

---

### Post by the_pod on 2009-07-03
Bump. Just bought one of these myself (the only non-$100 one that Fry's carried).

Any progress getting it installed or am I in for an afternoon of disappointment?

---

### Post by MockY on 2009-07-07
I can't answer that but it does work wonderfully in XBMC (using the Mediastream skin), and after trying all media center software out there, none comes close to the stability of XBMC.

---

