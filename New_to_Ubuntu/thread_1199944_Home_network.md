---
title: "Home network"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by brawd on 2009-06-29
Hi All,

I want to network (link?) two Ubuntu computers, one 8.04 64 bit and the other is 9.04.
Addresses are 192.168.1.9 and 192.168.1.72 respectively.

I can Ping.
I can Lookup.

But that is as far as I've got with these two.

Computers with Windows show up straight away - but Ubuntus ignore each other.

Any and all help appreciated.

You might have seen this message (plea) on the forum, but I forgot to Prefix the first one and I've lost it.

regards,

Brawd

---

### Post by Celauran on 2009-06-29
If you're just planning on connecting the two Linux machines, you could set up [NFS](https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html) shares. If you'll be networking Linux and Windows machines, you'll want to use [Samba](https://help.ubuntu.com/8.04/serverguide/C/windows-networking-introduction.html) (multiple pages).

---

### Post by XCan on 2009-06-29
To be honest, NFS is nice, but if all you care about is to get it working, the built in 'script' in nautilus is really easy to use. Just right click on the folder/file you want to share and selecting 'Sharing Options'. When you enable sharing, you'll automatically be prompted to install the needed services. When all is setup (you'll need to relogin), you can easily connect to the share by typing smb://<ip>. Or you could mount it using smbmount <ip>.

---

### Post by brawd on 2009-06-29
Thanks Celauran, unfortunately that's too much jargon and tech talk for me to understand.

I still don't get why Windows just shows up in my panel, while Ubuntu is so shy.

brawd

---

### Post by brawd on 2009-06-29
Thanks Xcan,

I've done the share and setup bit on both computers. Now on the other computer I've shared a clipart folder in the home directory.

Exactly where do I type smb://192.168.1.72 which is ping address of the other computer?
Terminal didn't know the folder.

I just tried smb://192.168.1.72/home/clipart but nothing again.

brawd

---

### Post by Celauran on 2009-06-29
> **brawd said:**
> 
Exactly where do I type smb://192.168.1.72 which is ping address of the other computer?
Nautilus (file browser)

> I just tried smb://192.168.1.72/home/clipart but nothing again.

Tried 192.168.1.72/home/<your user name>/clipart?

---

### Post by brawd on 2009-06-29
Thanks to all,

Just in case some other newbie is following this discussion Nautilus doesn't appear on any lists. It's doesn't have it's own little launch icon. It seems to expand the selection that you get when you go to 'Places' and look at - say - Network. Once I did that then all the other Ubuntu machines connected on my home network appeared.
Not that any shared folders appeared of course, but I'll look into that now, lol.

Once again thank you to all.

brawd.

---

