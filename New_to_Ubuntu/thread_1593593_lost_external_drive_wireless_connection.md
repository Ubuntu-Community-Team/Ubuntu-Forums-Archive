---
title: "lost external drive wireless connection"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by joelgeez on 2010-10-11
Okay. Just started using Lucid Lynx recently. Was happy, but I decided to jump on Maverick yesterday.
With Lucid, everything worked as it was supposed to. Since upgrading, not so much.
My biggest puzzlement is that until upgrading, my exteral hdd talked to Belkin router which talked to computer.
Computer recognizes wireless router and internet connection. It recognizes Maxtor external drive when plugged in directly, and when I use Vista (I'm a dual booter).
Second, I've followed several posts to make the keyring login box stop annoying me, but everytime I reboot, there it is again.
Thanks in advance,
Joel

---

### Post by Hippytaff on 2010-10-11
Not sure about this one - so your wireless works? just annoyed by something that will not completely go away?

---

### Post by joelgeez on 2010-10-11
> **Hippytaff said:**
> Not sure about this one - so your wireless works? just annoyed by something that will not completely go away?
Two issues:
1. Since upgrade, external hard drive not recognized when the drive is plugged into my Belkin router.

2. Can't stop keyring login box from appearing when I do a reboot.
J

---

### Post by JustinR on 2010-10-11
> **joelgeez said:**
> 
2. Can't stop keyring login box from appearing when I do a reboot.
J

Go to System > Preferences > Passwords and Encryption Keys. Right click 'Passwords: default' and click 'Change Password'. Change the password to your current login password.

After that the Keyring box shouldn't pop up anymore.

---

### Post by joelgeez on 2010-10-11
> **JustinR said:**
> Go to System > Preferences > Passwords and Encryption Keys. Right click 'Passwords: default' and click 'Change Password'. Change the password to your current login password.

After that the Keyring box shouldn't pop up anymore.
My keyring login password was the same as my regular password. 

However, I think I solved the problem by following instructions and clicking 'Delete' instead.

Rebooted and no keyring login, so thanks for leading me to the context menu box.
J

---

### Post by JustinR on 2010-10-11
> **joelgeez said:**
> My keyring login password was the same as my regular password. 

However, I think I solved the problem by following instructions and clicking 'Delete' instead.

Rebooted and no keyring login, so thanks for leading me to the context menu box.
J

That means you have to re-enter all of your lost passwords, eg. like wireless network passwords, Gwibber/Empathy, etc.

---

### Post by Hippytaff on 2010-10-11
excellent...remember to mark the thread as solved in the thread tools at the top of the page :-)

---

### Post by JustinR on 2010-10-11
> **Hippytaff said:**
> excellent...remember to mark the thread as solved in the thread tools at the top of the page :-)

He still has his first problem. :-D

---

### Post by joelgeez on 2010-10-11
> **Hippytaff said:**
> excellent...remember to mark the thread as solved in the thread tools at the top of the page :-).

No. Issue 2 addressed, but not issue 1.

When I updated from 10.04 to 10.10, I lost the wireless connection to my external hard drive.

That issue has not been addressed yet.
J

---

### Post by JustinR on 2010-10-11
> **joelgeez said:**
> .

No. Issue 2 addressed, but not issue 1.

When I updated from 10.04 to 10.10, I lost the wireless connection to my external hard drive.

That issue has not been addressed yet.
J

How did the connection work for you in Ubuntu 10.04? Did you see the drive in the Network places folder?

---

### Post by Hippytaff on 2010-10-11
> **joelgeez said:**
> .

No. Issue 2 addressed, but not issue 1.

When I updated from 10.04 to 10.10, I lost the wireless connection to my external hard drive.

That issue has not been addressed yet.
J

over eager to see resolution...:-s

```

iwconfig

```and
```

lsusb or lspci

```

:-s

---

### Post by joelgeez on 2010-10-11
> **JustinR said:**
> How did the connection work for you in Ubuntu 10.04? Did you see the drive in the Network places folder?
It appeared on the desktop, as a "place." I would guess that it showed up in network.

I don't remember all the places I saw it because it showed up in two or three places.
J

---

### Post by joelgeez on 2010-10-11
> **Hippytaff said:**
> over eager to see resolution...:-s

```

iwconfig

```and
```

lsusb or lspci

```

:-s
Entered code as written. Lots of stuff showed up in terminal window but I have no idea what I was supposed to be doing or what was supposed to happen.
J

---

### Post by JustinR on 2010-10-11
> **joelgeez said:**
> It appeared on the desktop, as a "place." I would guess that it showed up in network.

I don't remember all the places I saw it because it showed up in two or three places.
J

Yep, that means it should show up in Network. If you go to Places > Network. Do the drive or router show up? If the drive shows up then just open it up and it will appear on the desktop. If the router shows up, double click that and the drive should appear.

---

### Post by joelgeez on 2010-10-12
> **JustinR said:**
> Yep, that means it should show up in Network. If you go to Places > Network. Do the drive or router show up? If the drive shows up then just open it up and it will appear on the desktop. If the router shows up, double click that and the drive should appear.
 
Thanks. At work now. Will try when I get home. Fingers crossed. Confidence high.
J

---

### Post by joelgeez on 2010-10-12
> **JustinR said:**
> Yep, that means it should show up in Network. If you go to Places > Network. Do the drive or router show up? If the drive shows up then just open it up and it will appear on the desktop. If the router shows up, double click that and the drive should appear.
 
Thanks. At work now. Will try when I get home. Fingers crossed. Confidence high.
J
[FONT=Comic Sans MS]“Never give up! Never surrender!” – Peter Quincy Taggart, Captain of the NSA Protector[/FONT]

---

### Post by anewguy on 2010-10-12
For others following this thread who may not understand - the user has a network-attached storage, a drive connected on the network not on a PC, and that is what they are trying to "see".

Dave ;)

---

### Post by joelgeez on 2010-10-12
> **JustinR said:**
> Yep, that means it should show up in Network. If you go to Places > Network. Do the drive or router show up? If the drive shows up then just open it up and it will appear on the desktop. If the router shows up, double click that and the drive should appear.
Well that was so simple. Double click. Who knew?
Just like you said. There it was.
If you have a moment what exactly did I do and where is this kind of stuff documented?
Thanks again,
Joel

---

