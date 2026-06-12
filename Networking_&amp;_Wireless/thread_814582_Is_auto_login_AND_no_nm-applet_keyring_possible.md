---
title: "Is auto login AND no nm-applet keyring possible?"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by brett123 on 2008-05-31
I have Ubuntu auto login with my account, as I'm the only user here. However nm-applet keeps asking for my password to connect wirelessly.

I've searched around and it appears (to a dumb newbie at least) that you can't get rid of both - it's one or the other. Is there anyway I can not enter passwords everytime I boot up?

Thanks.

---

### Post by abhiroopb on 2008-05-31
Yes I've been meaning to post this. Its a bit annoying to say the least. What I find most annoying is if I change the boot password I need to edit some files before I only put in the login password.

---

### Post by brett123 on 2008-06-02
Any ideas?

---

### Post by oofnik on 2008-10-08
I'm having difficulty trying to fix this as well. Instead of autologin I'm using the fingerprint reader to log in via thinkfinger_pam.

If I type in the password at login, nm-applet does not ask for a password. If I use fingerprint, it does. Is there a way to make nm-applet not ask for a password since it's already logged in?

---

### Post by oofnik on 2008-10-09
Not really a fix, but a suitable workaround for me.
As nm-applet was the only thing using the Gnome keyring, I decided to try Wicd, a replacement for Gnome network manager: [http://wicd.net/](http://wicd.net/)

It works great for me. Just follow the instructions on the download page and it should install properly. I had to run
```
sudo wicd & 
``` then
```
wicd-client & 
```

to get the daemon and userspace client running immediately after install, but they both came up OK after a reboot.

---

### Post by jynxF on 2008-10-16
Having repeatedly failed to get nm-applet and auto-login to work together on hardy, I tried wicd - thanks for that! It works perfectly - just follow the installation instructions (I didn't need to run anything from the command line to get reconnected).

---

### Post by RobTi on 2008-10-18
Thanks
A complete novice at this and tried this to fix the nm-applet from asking for a wrong password at boot and all is now working as it should.
Robert

---

