---
title: "Quiet down chatty Samba + CUPS"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by eric a on 2007-08-15
Hello everyone, thank you for providing this community for discussion.  I am using 7.04 release, and tightning security on a laptop installation. The difficulty I am having is with the chatty nature of Samba and CUPS.

On Samba, I have sucessfully implemented hashed passwords for all available shares. The remaining issue is that Samba appears to advertise the laptop every few seconds on the laptop's network connection.  Can anyone advise how to prevent this and still have Samba serving out shares ?

On CUPS, I only need to print to remote printers served via CUPS on another machine running OSX. However, if I stop cupsd running on the laptop, the remote printers can not used until cupsd is restarted on the laptop.  Once cupsd is back up and running, remote printing works and CUPS starts to broadcast it's presence.  Can anyone either advise a way to either print to remote cups printers without cupsd running on the laptop, or stop cupsd from throwing out these messages ?

Thanks

---

### Post by ihristov on 2007-08-17
cups by default is binding only to localhost, so there is no need to be stopping it. Unless your setup is different.

Basically what you want is normally done by a firewall. Linux has a built-in firewall by default, You can disable certain traffic with iptables rules. You can set them up by hand or use firestarter or some other GUI to generate the rules you want.

Also keep in mind that if you cut off certain Samba traffic, it's possible you will no longer be able to open shares.

I personally have samba not starting by default and I start it by hand only when I need it.
```
sudo /etc/init.d/samba start
```

---

### Post by eric a on 2007-08-20
Thank you for the reply. I got Samba silent by entering this into smb.conf. Don't really know if anything else interacts with this:

local master=no
browse list=no
lm announce=no

I am still able to map drives from remote systems by entering the server name.

Then in cups, putting this in at the top of cupds.conf did it for me:

Browsing Off

Since I am doing this laptop with my young daughter as a school project and keeping setup easy as possible, we are trying to avoid all the command line that we can in daily use.

---

