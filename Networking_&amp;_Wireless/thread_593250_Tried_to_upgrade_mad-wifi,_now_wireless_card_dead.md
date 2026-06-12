---
title: "Tried to upgrade mad-wifi, now wireless card dead"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by kuriharu on 2007-10-27
Hello, 

I followed this guide ([http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)) to try to get aircrack to work. I followed the guide which involved recompiling madwifi. Now my wifi card won't work.

I'm running an Atheros chipset on 7.04. Any clues how to get it back?

---

### Post by kevdog on 2007-10-27
Guide was ok but it used dapper repositories.  Its not good to use different repository versions in most cases.  

Madwifi is contained in linux-restricted-package.  I would either reinstall this package, or you will need to compile and install madwifi from source (which isnt hard either).  Both these options should work.

---

### Post by Ansenyi on 2007-10-27
> **kuriharu said:**
> Hello, 

I followed this guide ([http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)) to try to get aircrack to work. I followed the guide which involved recompiling madwifi. Now my wifi card won't work.

I'm running an Atheros chipset on 7.04. Any clues how to get it back?
Did compilation go well? I also tried this tutorial a few days ago and I got it working after changing some things.

I followed instructions from [http://www.aircrack-ng.org/doku.php?id=madwifi-ng]("http://www.aircrack-ng.org/doku.php?id=madwifi-ng") for compilation of madwifi drivers and it worked for me.

---

### Post by kuriharu on 2007-10-27
Thanks for your advice.

I did manage to get mad-wifi working. I may try that tutorial on another day, but I'm gonna wait until I have some more time. I may upgrade to Gutsy first.

Thanks for your help!

---

