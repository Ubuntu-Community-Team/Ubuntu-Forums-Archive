---
title: "Thunderbird doesn't recieve mail after upgrade to Karmic"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by peakshysteria on 2009-11-05
Upgraded from Jaunty to Karmic. Update went as last time very smooth. Except the fact that Thunderbird don't seem to work as before the upgrade. I know there is new mail in the inbox (checked via webmail) but Thunderbird gives me nothing. Does anybody have a fix for this?

---

### Post by RedSingularity on 2009-11-06
Did you review your pop settings in thunderbird?  Something may have got reconfigured there.

---

### Post by peakshysteria on 2009-11-06
Eh, care to elaborate? I must say that setting up mail clients isn't part of my forte. It's been a while since I configured Thunderbird. I'm just used to it working after an upgrade. So I'm on a loss here...!

---

### Post by RedSingularity on 2009-11-06
Ok.  Who is your e-mail provider?

---

### Post by peakshysteria on 2009-11-06
let's say it's ntnu.no

---

### Post by RedSingularity on 2009-11-06
I have never herd of that before but we will see what we can do.  (It's based in norway?)

In thunderbird go to Edit>Account Settings>Click the account giving you a problem.  Then go to "server settings" under that account.  

Make sure the pop settings are correct there.  I would give you the info you need to put in but i have never personally worked with loqal.no

---

### Post by RedSingularity on 2009-11-06
You can always google something like this..........."loqal.no thunderbird setup."

I tried it here but all i get are American sites which dont know anything.

---

### Post by peakshysteria on 2009-11-06
Hm, all seems ok.

Server type: POP mail server
Server Name: is correct
User Name: is correct

Port 110 Default: 110

Can it be that after my upgrade from Jaunty to Karmic something happened to my local directory or home folder??? I can't see anything wrong with account settings in Thunderbird itself.

---

### Post by wrgb2 on 2009-11-06
Do you get an error message when trying to check your email?  Also, watch the bottom left portion of the Thunderbird window (the status line) when you click on Get Mail.

---

### Post by oldsoundguy on 2009-11-06
Did you save your Thunderbird and FireFox info, or save your ~/home folder OFF OF YOUR COMPUTER or to another drive or partition and then bring it back?  IF NOT .. your install wiped out all of your settings and everything will have to be re-installed. (and that includes your plug ins in FireFox.)

Just did that INTENTIONALLY on three machines as I wanted to gut them out and start at point "A"!! (too much saved trash to triage!)

---

### Post by peakshysteria on 2009-11-06
> **wrgb2 said:**
> Do you get an error message when trying to check your email?  Also, watch the bottom left portion of the Thunderbird window (the status line) when you click on Get Mail.

No error messages.

> **oldsoundguy said:**
> Did you save your Thunderbird and FireFox info, or save your ~/home folder OFF OF YOUR COMPUTER or to another drive or partition and then bring it back?  IF NOT .. your install wiped out all of your settings and everything will have to be re-installed. (and that includes your plug ins in FireFox.)

Just did that INTENTIONALLY on three machines as I wanted to gut them out and start at point "A"!! (too much saved trash to triage!)

All Firefox settings,addons etc are intact after the upgrade. All is smooth as ever with my beloved FF. Thunderbird doesn't receive new mail at all.

Just now Google gave me this thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1307175](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1307175)

Didn't work.

---

### Post by wrgb2 on 2009-11-06
I just upgraded from Jaunty to Karmic and all of my settings in Thunderbird were still intact, they were NOT overwritten.  Firefox, yes I had to install SOME of my plugins that were not compatible with the new 3.5.4 version.

---

### Post by RedSingularity on 2009-11-06
Not recieving email is not a local problem but usually a server problem.  In your case you say there is no error messages.  Maybe you should do a complete purge and reinstall of thunderbird.

---

### Post by frank002 on 2009-11-06
I installed Karmic in my "test" computer and I use Thunderbird also. When the computer was running Jaunty, everything worked fine. After installing Karmic I noticed that it took forever to connect to the mail server. This did not happen with Jaunty. I am holding off on Karmic.

---

### Post by peakshysteria on 2009-11-07
*bump*

---

### Post by LewRockwell on 2009-11-07
> **peakshysteria said:**
> Eh, care to elaborate? I must say that setting up mail clients isn't part of my forte. It's been a while since I configured Thunderbird. I'm just used to it working after an upgrade. So I'm on a loss here...!

[http://beginlinux.com/blog/2009/10/secure-ubuntu-9-10-mail-client/](http://beginlinux.com/blog/2009/10/secure-ubuntu-9-10-mail-client/)

.

---

