---
title: "PC Defender has added itself to Ubuntu Firefox"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by smacfarl on 2009-09-21
Hi,

I have an instance where the "PC Defender Mozilla extension" has attached itself to the an Ubuntu instance of Firefox. How do I get rid of it? Looks like there is now a cross platform path to exploit Firefox.

I don't know enough about how extensions to firefox work on linux. All help is appreciated.

---

### Post by philinux on 2009-09-21
Tools>addons>extensions> Disable or uninstall

---

### Post by smacfarl on 2009-09-21
It's a remote machine from me. Will determine if it's attachment is visible from the extension manager. It certainly fires the pop-ups quite visibly. Anyway I can learn what firefox exploit was used to install this extension?

Dumb question. What's the best way to get to that remote Ubuntu Desktop from my desktop if I wanted to look for myself, rather than waiting for user feedback?

---

### Post by Sidewinder1 on 2009-09-21
Since it's remote, can you be sure that it wasn't installed by a user on that machine? Just curious.

---

### Post by smacfarl on 2009-09-21
No I can't be sure it wasn't a user mistake at this point. I am actually hoping this is the case.

---

### Post by TyTiger on 2009-09-21
> **smacfarl said:**
> It's a remote machine from me. Will determine if it's attachment is visible from the extension manager. It certainly fires the pop-ups quite visibly. Anyway I can learn what firefox exploit was used to install this extension?

Dumb question. What's the best way to get to that remote Ubuntu Desktop from my desktop if I wanted to look for myself, rather than waiting for user feedback?

If its Gnome, then theres a VNC Based remote desktop application pre-installed, configurable under System -> Preferences -> Remote Desktop

If you need to use port forwarding the port is standard VNC by default (5900) even though it shows up as vnc:/my-pc:0 it actually runs on port 5900 :0 is just the attached display. 
**[COLOR="Red"]HIGHLY RECOMMEND SETTING UP A PASSWORD[/COLOR]**

---

### Post by Sidewinder1 on 2009-09-21
:-)

---

### Post by lovinglinux on 2009-09-21
> **TyTiger said:**
> If its Gnome, then theres a VNC Based remote desktop application pre-installed, configurable under System -> Preferences -> Remote Desktop

If you need to use port forwarding the port is standard VNC by default (5900) even though it shows up as vnc:/my-pc:0 it actually runs on port 5900 :0 is just the attached display. 
**[COLOR="Red"]HIGHLY RECOMMEND SETTING UP A PASSWORD[/COLOR]**

ssh is more secure

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

**[COLOR="Red"]HIGHLY RECOMMEND USING KEYS INSTEAD OF PASSWORDS[/COLOR]**

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by lovinglinux on 2009-09-21
> **smacfarl said:**
> Hi,

I have an instance where the "PC Defender Mozilla extension" has attached itself to the an Ubuntu instance of Firefox. How do I get rid of it? Looks like there is now a cross platform path to exploit Firefox.

I don't know enough about how extensions to firefox work on linux. All help is appreciated.

I never heard about "PC Defender Mozilla extension". I did a search with Google and the Mozilla Add-ons site, the only extension close to that title that I could find was [Browser Defender Toolbar](https://addons.mozilla.org/en-US/firefox/addon/8909).

Are you talking about that virus scanner, that has an interface that look like Windows? If yes, then it's just a web site script that pops up when the user visit it. It's a mockup to trick the user into installing their crappy anti-virus, which probably is a malware.

---

### Post by LewRockwell on 2009-09-21
> **lovinglinux said:**
> I never heard about "PC Defender Mozilla extension". I did a search with Google and the Mozilla Add-ons site, the only extension close to that title that I could find was [Browser Defender Toolbar](https://addons.mozilla.org/en-US/firefox/addon/8909).

Are you talking about that virus scanner, that has an interface that look like Windows? If yes, then it's just a web site script that pops up when the user visit it. It's a mockup to trick the user into installing their crappy anti-virus, which probably is a malware.

this(what lovinglinux said)

.

---

### Post by lovinglinux on 2009-09-21
> **LewRockwell said:**
> this

.

?????

---

### Post by LewRockwell on 2009-09-21
> **lovinglinux said:**
> ?????

change

.

---

