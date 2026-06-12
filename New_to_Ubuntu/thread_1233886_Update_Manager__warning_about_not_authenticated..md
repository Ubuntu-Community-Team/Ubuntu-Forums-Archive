---
title: "Update Manager  warning about not authenticated."
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Jonas thomas on 2009-08-07
A friend of mine a couple of days ago, told me about major hole being plugged and that I should update. He said it was across multiple distros'  so I guess it was something Debian'ish?  I've been offline for a little while so I'm sort of out of touch here.

Anyway, when I fire up my update manager and I get this warning about two packages that can't be authenticated:
libavutil50
libswscale0

They seem to be legit... How big of a deal is it that they can't be authenticated?

---

### Post by tarps87 on 2009-08-07
Out of interest try:
```
sudo apt-get update && sudo apt-get upgrade
```
Can't remember the GUI way but I think there is a refresh button.
I tend to se this message when list of packages to update is out of sync with the latest packages on the server.

My knowledge of package authentication is Ubuntu is to good so I'll let someone else answer that

---

### Post by Paddy Landau on 2009-08-07
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys *key*
```where *key* is the key that the update manager complains about (it's a long string of digits and letters A-F that looks something like AB7080EBE247D1CFF).

Then do the update and upgrade again; do you still get the error?

---

### Post by Jonas thomas on 2009-08-09
> **tarps87 said:**
> Out of interest try:
```
sudo apt-get update && sudo apt-get upgrade
```
Can't remember the GUI way but I think there is a refresh button.
I tend to se this message when list of packages to update is out of sync with the latest packages on the server.

My knowledge of package authentication is Ubuntu is to good so I'll let someone else answer that

Thanks, going the cl way it exposed the key I needed to be fixed up by the next command.

---

### Post by Jonas thomas on 2009-08-09
> **Paddy Landau said:**
> ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys *key*
```where *key* is the key that the update manager complains about (it's a long string of digits and letters A-F that looks something like AB7080EBE247D1CFF).

Then do the update and upgrade again; do you still get the error?

Thanks... That did the trick for that issue anyway... Btw... I was amused by your matrix youtube link... ;)

---

