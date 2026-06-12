---
title: "keep getting &quot;auth required&quot; message"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by charleyer on 2009-01-16
I'm *very* new to using Ubuntu, but so far it seems great. However, I'm having some frustrating problems getting connected to my wireless network at home (which is on a Windows XP machine).

I've installed 8.10, and have downloaded a couple hundred (!) updates via a wired internet connection, so I think everything's up to date. I can connect to my wireless network if I remove the security, but any time I turn the security on, I get a message that says "Wireless Network Authentication Required" over and over again.

Any ideas?

---

### Post by compiledkernel on 2009-01-16
Which auth method are you using?

---

### Post by charleyer on 2009-01-16
WEP, 128 bit.

---

### Post by compiledkernel on 2009-01-16
Are you using the passphrase or the actual WEP key when using network-manager?

---

### Post by Favux on 2009-01-17
Hi charleyer,

Is it WEP-TKIP by any chance?  You may need to remove CCMP or one of the other values from the group key.  Please see:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Good luck!

---

### Post by charleyer on 2009-01-17
compiledkernel, I'm using the 26-character key.

---

### Post by charleyer on 2009-01-17
Favux, thanks for referring me to the other thread. However, I don't have a System Tools menu in Applications. And when I start the Configuration Editor throught the Terminal, I don't see the same options you listed. Here's what I get:

auth-alg - shared
key-mgmt - none
name - 802-11-wireless-security

Any ideas? Thanks...

---

### Post by Favux on 2009-01-17
Hi charleyer,

Yes, the options (keys) are local, only available to the logged in user.  If I remember right I just went to System>Preferences>Main Menu and enabled it (checked Configuration Editor's box).

---

### Post by charleyer on 2009-01-18
Hi again Favux,

Thanks for your help on this, but it could be that I don't know enough about Ubuntu to know what I'm doing wrong. I'm still only getting the same three options (auth-alg, key-mgmt, name) even though I was able to get the Configuration Editor to show up in my Applications menu. I think I'm using the only user that's available on the system too.

Any other suggestions you can offer would be greatly appreciated!

---

### Post by Favux on 2009-01-18
Hi charleyer,

Did you turn wep back on in the router?

Did you use NM to edit the connection and add all the info?

If you go to Applications>Accesories>Passwords and Encryption Keys is your wireless connection in the Passwords tab?

---

### Post by charleyer on 2009-01-18
Right now I'm working on an ethernet connection, but yes I did turn WEP back on in the router. NM has all the correct info as far as I can tell, but I also turned off the auto-connect in the Configuration Editor for now, since that box kept coming back over and over.

I guess I've been assuming that until I can see that "group" option in the Configuration Editor that I won't be able to get it going. Is that true?

In the Passwords and Encryption Keys area (on the Passwords tab) I see these two things:

Network secret for Auto [wireless network name], and
Network secret for [wireless network name]

Both have the correct WEP key.

Again, thanks for all your time on this Favux!

---

### Post by Favux on 2009-01-18
> I guess I've been assuming that until I can see that "group" option in the Configuration Editor that I won't be able to get it going.
Yes, that's what I'm thinking.  The only time I saw auth-alg was in the third example.  It transiently appeared after I removed CCMP.  I've never seen the keys with Gconf editor without group being one of them.  I admit to being baffled.

I guess you could go at it the other way if it still won't connect.  What other values could there be?  In other words any possible values from the router that you could put in the format of the example keys?  I don't know that I would try creating the group key.  What happens if you remove shared from auth-alg?  Stuff like that.  Be sure to keep a record of everything so you can restore to the original state.

Good luck!

---

