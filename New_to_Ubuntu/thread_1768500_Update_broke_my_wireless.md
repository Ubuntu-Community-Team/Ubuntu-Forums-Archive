---
title: "Update broke my wireless?"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by aa4bb on 2011-05-26
Update Manager popped up today with a small update, <1 MB. I let it update, as usual.

Since then, when I boot, my wireless light does not come on and I have no wireless networking. Everything's been fine with the wireless ever since I upgraded to 10.04 a year ago, until right now.

If I boot a live session in 10.04.2 from a USB drive, the wireless works fine. That's what I'm using to send this message.

I have a Dell Latitude D620 with about 2BGB memory.

Could the Update have done this? I haven't installed any new software or done anything out of the ordinary otherwise.

---

### Post by josephmills on 2011-05-26
hi there could we see a ```
lspci -nn
``` and a ```
lsusb
``` and a ```
rfkill list all 
``` thanks

---

### Post by ApOgEEs on 2011-05-26
Perhaps, you may check this answers which might be related to your issue:
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/155040](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/155040)

---

### Post by aa4bb on 2011-05-27
apogees and josephmills,

Thank you both for your suggestions.

I must confess: I didn't research it thoroughly enough before posting my question and I gave incomplete and misleading information on the problem by accident.

The problem was actually "Networking disabled". That included wired as well as wireless. By search, I found reports of a setting "NetworkingEnabled=false" in the file NetworkManager.state in directory /var/lib/NetworkManager being responsible. Once I edited that file and changed "false" to "true" and rebooted the system, everything is fine.

---

