---
title: "&quot;modprobe ndiswrapper&quot; freezes edgy"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by neobonzi on 2006-11-08
Hey all!

  I upgraded to edgy awhile ago and everything is going GREAT except for my wireless card. When i upgraded it wasnt working at all and after some help I learned it was because ndiswrapper was apparently causing trouble on edgy.

  I downloaded the latest source and compiled it myself and installed it - i then installed the drivers for my Intel 3915ABG Wireless card. I ran sudo modprobe ndiswrapper and the wireless card started up and *seemed* to be detecting networks and working fine.

  After that I noticed that my computer simply began locking up (no mouse movement, nothing). I have to use the command "sudo modprobe ndiswrapper" every time I restart my computer, and sometimes it freezes immediately upon executing the command and sometimes it takes a little while, but it freezes. If i dont use this command the computer will run for hours completely fine.

any ideas would be GRREATly appreciated, this is so frustrating!](*,)

---

### Post by wieman01 on 2006-11-08
Had the same problem with Dapper & ndiswrapper. Had to get hold of the latest source package & compile it myself. That worked & no more freezes.

---

### Post by FrodoB on 2006-11-08
Good advice.  Also checkout the ndiswrapper site and note the list of working devices:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by neobonzi on 2006-11-08
I actually manually compiled the latest ndiswrapper and that is what I am using so its confusing to me why it freezes up.

My device is supported Card: [Intel] PRO/Wireless 3945ABG according to the site - and it does in fact work - for a little while - until the computer freezes.

any other ideas?

---

### Post by neobonzi on 2006-11-09
Is there any way to run my wireless card on Edgy without the use of ndiswrapper? I heard its just plain trouble on edgy right now so maybe i can use an alternate method?

---

### Post by FrodoB on 2006-11-09
The only thing I can suggest is to change the source of your .inf that you are loading.  If you are using and .inf from XP then try 2000. Obviously remove the one that is freezing before installing the new one.

---

