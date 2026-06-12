---
title: "wifi loses connectivity at idle at seemingly random intervals ubuntu gnome 14.04"
date: 2014-10-04
forum: Networking &amp; Wireless
---

### Post by Halpm on 2014-10-04
Hey guys - this has been really getting up my nose for some months now.
When I leave the computer not doing anything - for example the time it takes to make a coffee - or simply do something on the machine that doesn't involve the internet, the wifi will usually lose its connection to the router after a few minutes. It will then not be able to reconnect, or even find the router again until I either run the command "gksudo iwlist scan" or restart the wifi with the hardware button.
Here is a pastebin link to the output of "wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script":

[http://pastebin.ubuntu.com/8491058/](http://pastebin.ubuntu.com/8491058/)

Does this make any sense to anybody?

---

### Post by kc1di on 2014-10-04
Your Realtek wireless card doesn't like to work well with linux, but some have had success by turning off the n band channel on your router and using Channel 1.

[this page]("http://askubuntu.com/questions/456453/realtek-rtl8188ce-wireless-driver-unstable-in-ubuntu-14-04") may be of help.

---

### Post by Halpm on 2014-10-04
Thanks for the lead! The fix in [this post]("http://ubuntuforums.org/showthread.php?t=2219952&p=13003107#post13003107") seems to have fixed the problem so far. marking as solved.

---

### Post by kc1di on 2014-10-04
Glad you got it solved :)

---

