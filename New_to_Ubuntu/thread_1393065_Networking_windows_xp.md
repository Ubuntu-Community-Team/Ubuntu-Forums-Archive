---
title: "Networking windows xp"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by mvalviar on 2010-01-28
I'm trying to access a shared xp folder from my ubuntu box. But I'm getting an access denied message. When boot to xp and try to access the same share I get "access denied you might not have permission to access this network resource." 

The other xp box is named audioslave and with an admin user william with no password. Those are what I enter when I'm prompted as I access the share but I'm still getting access denied.

From the other xp box I can see my shares from ubuntu.

How could I set up the shares on the other xp box properly?

---

### Post by mvalviar on 2010-01-29
up

---

### Post by ymra on 2010-01-29
What you want is called samba.  I cant help you beyond that because I have never used it.  good luck.

---

### Post by PPPilot on 2010-01-29
Go to your XP box and right click on the folder/folders you want to access from Ubuntu. Select "Properties" then select the shared tab. from this window you can make the folder and/or sub-folders sharable. At least that's how it works on my Ubuntu/XP network. Also you can do the same thing with an entire drive.

---

### Post by dollzii on 2010-01-29
Maybe this could help ? 

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by mvalviar on 2010-01-30
That's what I did.

On the xp box I have a folder shared already. On my own box when I boot to windows xp and try to access that xp box I get get a prompt saying I'm not permitted to access it.

Please note that I already have samba working I can see my ubuntu shares on that xp box.

The problem is that neither ubuntu nor xp on my pc can access the shares on that pc. I'm assuming it's some type of permission issue I don't know about.

---

### Post by lotharmat on 2010-01-30
IIRC,you need to have a password to share folders - Try creating a password for your admin user.

Also - On the sharing and security tab (win WP) make sure that on the 'sharing' section you have granted permission for 'everyone' to read teh folder - think of this as the gateway - everyone can see it but you can then select what access people have to enter the gateway through the 'security' permissions.

HTH

---

