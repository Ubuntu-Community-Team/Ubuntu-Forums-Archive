---
title: "Ubuntu 13.04 &amp; Bluetooth"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by fidbeck on 2013-09-21
Hello people

I've been trying to use bluetooth to send some photos from my phone to my laptop but I'm having a bit of a problem here

I have my devide as decoverable, in my laptop I have the options Bluetooth and Visible so that mean i've successfuly connected my device to my laptop, oddly my phone says in the bluetooth devices it can find "Paired but not connected". When I try to send something over it says that the file was not sent.
Even If I try to send something from the laptop to my phone I get this error "GDBus.Error:org.openobex.Error.Failed: Unable to request session"
From the software Center I tried to install BlueWho and Bluetooth Manager (Blueman bluetooth manager) but it still doesn't work.

I also tried this but none seems to work :S

---

### Post by fidbeck on 2013-09-23
No one?

---

### Post by slickymaster on 2013-09-23
You run into a already reported bug. See [Bug #1148033]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033")

What you can do is to install bluetooth-manager:```
sudo apt-get install blueman
```and then used it to send those files.

---

### Post by fidbeck on 2013-09-23
I already did that and it doesn't seem to be working :S Don't really know why.

Odd as it may seem I can send files from the laptop to the mobile device but not the other way around :S

---

### Post by varunendra on 2013-09-23
> **fidbeck said:**
> Odd as it may seem I can send files from the laptop to the mobile device but not the other way around :S

I had the same problem with the default Bluetooth Manger. Installed blueman, still the same.

However, blueman applet > Local Services... menu showed me that two FTP services were disabled by default, I enabled them and am happy ever since. Please refer to the two FTP related checkboxes in the screenshot below -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246460&stc=1&d=1379989247[/IMG]

Tick them > Apply > Close. Let us know if it helps you too.

---

### Post by teique on 2013-10-01
> **slickymaster said:**
> You run into a already reported bug. See [Bug #1148033]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033")

What you can do is to install bluetooth-manager:```
sudo apt-get install blueman
```and then used it to send those files.

perfect! my bluetooth was useless, couldnt send or receive, and just to turn on was a pain... ubuntu 12.10
thanks!

PS.: they could implement a way to simply vote up the post, or merge this forum into askubuntu..

---

