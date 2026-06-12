---
title: "How do I change the default booting OS on a Wubi install?"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by diablo75 on 2009-09-18
I have a Wubi install on my mom's PC and I'd like to change it so the boot loader menu that appears, offering the choice between Windows XP and Ubuntu, defaults to Ubuntu instead of Windows so she doesn't have to arrow down to select Ubuntu.

---

### Post by jzacsh on 2009-09-18
> **diablo75 said:**
> I have a Wubi install on my mom's PC and I'd like to change it so the boot loader menu that appears, offering the choice between Windows XP and Ubuntu, defaults to Ubuntu instead of Windows so she doesn't have to arrow down to select Ubuntu.

**[COLOR="Red"]...WARNING: BACKUP YOUR C:\BOOT.INI FILE BEFORE DOING THIS...[/COLOR]**

*I'm not sure that this is the right way, so double check it (with the link below)*

I believe XP isn't very nice about letting you configure the boot order in the "c:\boot.ini" file.
_You can view it by doing:_
[I]run... msconfig
click the 'boot.ini' tab (i think).[/I]

_anywho, to edit this file, you can:_
* open it with notepad
* copy its contents
* paste contents into a new notepad
* close the original
* edit the new "untitled" one to what you like...
*  - (in your case that means I believe reordering them)
* click 'file' > 'save'
* save the file directly to your c:\ as boot.ini (*you're attempting to overwrite the existing one at this step*)
* it should ask you "overwrite?", click yes


**this also, will be a good reference** "[How do edit the Boot.ini file in XP]("http://support.microsoft.com/kb/289022")":
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by philinux on 2009-09-18
Since wubi uses windows bootloader this has to be done from windows.

Pretty easy though.

[http://www.psychocats.net/ubuntu/wubi#bootorder](http://www.psychocats.net/ubuntu/wubi#bootorder)

---

### Post by jzacsh on 2009-09-18
> **philinux said:**
> Since wubi uses windows bootloader this has to be done from windows.

Pretty easy though.

[http://www.psychocats.net/ubuntu/wubi#bootorder](http://www.psychocats.net/ubuntu/wubi#bootorder)

oh, that looks ten times better ^ do it philinux's way :)

---

