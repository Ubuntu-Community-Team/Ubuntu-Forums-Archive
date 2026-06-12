---
title: "nm-applet wifi not working? or user error?"
date: 2015-09-11
forum: Networking &amp; Wireless
---

### Post by bowie101 on 2015-09-11
hi. I have nm-applet to connect to wifi. Sometimes it detects the wifi, sometimes not. about 50/50 every time I click on it, I roll the dice. When it does see networks, I click on one , it asks for an "encryption key" which I take to mean the password. Type in password, and it doesn't work. No wifi connection successful. Is it me?

---

### Post by howefield on 2015-09-11
Thread moved to the "*Networking & Wireless*" forum for better support.

---

### Post by bowie101 on 2015-09-11
are there other wifi applications to use instead?

---

### Post by bowie101 on 2015-09-12
I will tell you what I did, so that this may be of some help to others. Yes, it seems that "encryption key" when it comes to wifi is the same thing as your wireless password. Words. They sometimes get in the way. I did a search for "the best" or other wifi network/manager tools for linux/lubuntu/ubuntu. Came across a good list, and then installed anything from the list I could using synaptic (usually use command line) or looked to for the tarball on the internet to install from source. 

Among the things I installed was WICD. For my setup at least, (netbook now running lubuntu 14.04) WICD works for wi-fi, vs. the default, which doesn't. Interestingly, it doesn't seem to work for all my wireless networks. But it at least works for one of them. I will try the other things I installed, as well.

---

### Post by nknwn on 2015-09-12
I also had this problem with nm-applet but was able to connect with a line in the Terminal as below:

sudo nmcli dev wifi connect **yournetworkssid** password [B]yourwifipassword
[/B]

---

### Post by bowie101 on 2015-09-14
very strange. Someone went into my post and completely changed it to something nonsensical. and it also says last edited by howefield, but i can't imagine an administrator doing that.

---

### Post by nknwn on 2015-09-14
nm-applet is reliable on this laptop since I upgraded to: Lubuntu 14.04.3 LTS
The icon is on the tray by default.
I entered the WIFI password once and have not needed to enter it since.

---

### Post by bowie101 on 2015-09-15
I have to assume that if I install lubuntu 14.04 from a pen drive, and then do my aptitude update and aptitude upgrade and accept everything, that would get me to where you are, Lubuntu 14.04.3, or even more current when that time comes. yes?  question answered -

"  aptitude -y -s safe-upgrade  "

---

### Post by nknwn on 2015-09-15
That should work but I'm running 14.04.3 from a pen drive. So it's up to you to blaze the trail :)

---

### Post by bowie101 on 2015-09-15
yes. indeed, i seem to be up to date. As the days pass, your terminal command is working more and more. I sure as hell don't know what is different, from one day to the next, but yet, it works more and more.

---

