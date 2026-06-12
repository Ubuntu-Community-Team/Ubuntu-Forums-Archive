---
title: "Having to restart network during startup every time?"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by nbitting on 2008-01-26
So I finally got my wireless working great, but I'm having an issue where my wireless doesn't automatically connect when I restart my computer.  I have to go into the terminal and type in:

sudo /etc/init.d/networking restart

Then, the wireless connects and all is fine.  Can anyone tell me how I can automatically make this happen during startup?  Do I put this line of code in my profile?  I'm sort of new and can't remember where all of the directories are at.  Any help would be greatly appreciated.

Thanks!

---

### Post by kevdog on 2008-01-26
Here is an idea -- see if it works

echo "/etc/init.d/networking restart" | sudo tee -a /etc/rc.local
sudo chmod +x /etc/rc.local

Reboot and see if this works.  Commands inside the rc.local file should be completed during the boot procedure.

---

### Post by nbitting on 2008-01-28
That didn't work...nothing happened at all.  Anyone else have any ideas?

---

### Post by YoungJim on 2008-01-28
I've got the same problem; I'll make another post here if I find anything that works.

---

### Post by YoungJim on 2008-01-28
What worked for me, on 64-bit gutsy on my ghetto acer aspire 5100 notebook:

Make sure network manager is closed
Get WICD ([http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php"))
Configure it per the instructions
Set it up once
Forget about it
Drink coffee, enjoy snow day :)

---

