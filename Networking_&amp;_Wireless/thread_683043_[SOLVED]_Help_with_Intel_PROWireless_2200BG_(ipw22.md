---
title: "[SOLVED] Help with Intel PRO/Wireless 2200BG (ipw2200)"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by ProRathack on 2008-01-30
Hey guys,
I need help getting my driver working..
I know there is MANY  How-to's about it.. but it's always confusing me and sometimes it's intended for old Ubuntu version.( I'm Gusty version)
I'm running Ubuntu from Virtual Machine, I know the Internet is bridged , but I need help before I install it on my ''real" machine.

Please tell me which guide is the best and please know that I'm really new to Linux.
But I can Open Terminal and paste commands and run commands on it.
Please don't assume I know much.. Oh and by the way my wireless is WPA2 Encrypted.

Please help me as soon as possible, thanks.
The Security Mode is : WPA2 Personal(Choices are: WPA Personal, WPA Enterprise, WPA2 Personal, WPA2 Enterprise, RADIUS, WEP, Disable) ..Wireless Network Mode: Mixed(Choices are: B-Only, G-Only, Disabled).. Wireless Channel: 6.

 Wireless SSID Broadcast is Enabled..Status : SES Inactive .

WPA Algorithms: AES(I can change it to "TKIP+AES").. 

Please tell me how to make things work perfectly..
Thanks for your timr ^_^.
 My laptop is Dell Inspiron 630m

---

### Post by ProRathack on 2008-01-30
Someone help me please as soon as possible..
If you read this thread and willing to help me please tell me so I can know!

---

### Post by bukwirm on 2008-01-30
That wireless card should work fine in Ubuntu - at least, it worked for we without any tinkering.

For WPA2 support, you'll probably need to investigate [wpa_supplicant]("http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=wpa_supplicant"). It can be installed from the repositories. The first example in the README that may help you.

Also, [here]("http://ubuntuforums.org/showthread.php?t=263136") is a thread that might help you.

It sometimes takes a day or so you someone knowledgeable to see your question - you'll usually get an answer if you wait, though.

---

### Post by ProRathack on 2008-01-30
Thanks so much for trying to help me.
But is that guide okay?
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
Should I try it or it's junk? Or this one [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)?

Thanks again :)

---

### Post by bukwirm on 2008-01-31
I'd try the Ubuntu Forums one first - if it doesn't work, try something else.

---

### Post by p_quarles on 2008-01-31
Intel wireless cards are very well supported by Linux. Mine (a 3945) worked with the Live CD, so you should try that before installing it to the hard drive.

---

### Post by luca_linux on 2008-01-31
> **ProRathack said:**
> Hey guys,
I need help getting my driver working..
I know there is MANY  How-to's about it.. but it's always confusing me and sometimes it's intended for old Ubuntu version.( I'm Gusty version)
I'm running Ubuntu from Virtual Machine, I know the Internet is bridged , but I need help before I install it on my ''real" machine.

Please tell me which guide is the best and please know that I'm really new to Linux.
But I can Open Terminal and paste commands and run commands on it.
Please don't assume I know much.. Oh and by the way my wireless is WPA2 Encrypted.

Please help me as soon as possible, thanks.

PS: My laptop is Dell Inspiron 630m
Just replied to your private message. :)

---

### Post by ProRathack on 2008-01-31
bump.. updated with some information so may be someone will help until **luca_linux **comes online ;)
Thanks for all.

---

### Post by luca_linux on 2008-01-31
Ok, so try the following configuration:
> 
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA2
       key_mgmt=WPA-PSK
       pairwise=CCMP
       group=CCMP
       psk=your_psk


---

### Post by ProRathack on 2008-01-31
I'm speechless and don't know which way I can THANK YOU!!!
I really appreciate that because I would never do that on my own even after 1 Bilion Years :D. Thanks!!!!!
I will install Ubuntu after defragmenting my hard drive.. and if it doesn't work, I will exuse you to know your own network configuration so I can follow the guaranteed working one on your How-to.. anyway I hope this one will work as well.
Thanks again.

---

### Post by luca_linux on 2008-01-31
I assume it worked.
I'm glad that was helpful.

---

