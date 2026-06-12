---
title: "No Sound. Speak notification set to &quot;Mute All&quot;, but it is greyed out?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-05-20
I booted Ubuntu and for some unknown reason, I don't have sound. Nothing is set to mute, yet the notification has the speaker icon with --- next to it to signify everything has been muted, but it's not. Any help with this?

---

### Post by UnknownFear on 2010-05-20
Anyone have any idea? I really don't want to re-install Ubuntu if I don't have to.

---

### Post by lidex on 2010-05-20
Try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo pulseaudio --kill
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

Now this:
Post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by UnknownFear on 2010-05-20
> **lidex said:**
> Try this:

Thanks for replying with information on how to fix this, however, upon booting into Windows, and than booting into Ubuntu, it seems it has corrected it self and I now have sound. Thanks for the help, regardless.

---

