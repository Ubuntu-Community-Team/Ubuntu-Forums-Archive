---
title: "Lots of Questions"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Brennie25 on 2009-07-17
Hi,
 I just pooped my Linux cherry dual booting ubuntu with $%#@! vista.:confused:
Questions

[LIST=1]
[*]At installation it asked to incorporate my files from documents in windows and that worked but I went back and just put everything in documents but when I returned to ubuntu it wasn't there?
[*]Ubuntu asks for a password no matter what I do how can I turn it off.
[*]Open office fails to start.
[*]Can common files be shared between Vista and ubuntu?
[/LIST]
Any Help would be appreciated

---

### Post by powel212 on 2009-07-17
> # Can common files be shared between Vista and ubuntu?

I keep my data on a separate partition. Then I can access my data no matter what OS I am using.

You can use add/remove to install ntfs config in Ubuntu. Once installed and configured your ntfs drives will be automatically loaded to the desktop on boot.

Powel

---

### Post by jerome1232 on 2009-07-17
1: Ubuntu can read/write to MS File Systems, so really it would be easier to get your vista partition mounted under Ubuntu and then you can access those files.

2: Are you talking about Auto-login? System - Administration - Login Window - Security - Check auto login, the location may have changed since I've last looked so if it's not on the security tab just snoop around.

3: What happens if you try and launch it from a terminal? Applications - Accessories - Gnome Terminal, type "ooffice -writer" then hit enter, copy and paste the output it should give us an idea of what's going on hopefully.

4: See #1

---

### Post by Brennie25 on 2009-07-17
I am going to have to figure out how to do that.

---

### Post by ugm6hr on 2009-07-17
How did you install Ubuntu?  Wubi or as a true dual boot?

Which version of Ubuntu?

If the default OO.org doesn't launch, I suspect there is a problem with the installation.  Did you check the install CD for errors before installing?

---

