---
title: "EMERGENCY! using ubuntu to free windows of virus?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-09-02
ok. i have windows xp and ubuntu 9.04 on my little acer aspire one AOA150 8.9". while in windows i got a virus. which puts an icon in the tray and says the following 

"windows has detected spyware infection! it is recomended to use special antispyware tools to pervent ( yes pervent) data loss.Windows will now download and install the most up-to-date antispyware for you. click here to protect your computer from spyware!" 

 yes it really says pervent. now my question is. can i use ubuntu to go into my windows partition to delete the infection?? the infection is in C:/WINDOWS/system32/drivers/agp440.sys and i got a few trojans which have been removed except this one. 

i use avg and it says this file is whitelisted.. i went in to manually take care of it and nothing. andthe little Red icon with white X in my tray is annoying and pops up with that saying every like 5 minutes. what do i do? the virus is: Trojan Horse Generic14.ADMQ . thanks for any help.

---

### Post by NoaHall on 2009-09-02
Ehm, what you have there is scareware.

[http://en.wikipedia.org/wiki/Scareware](http://en.wikipedia.org/wiki/Scareware)

Boot into ubuntu, download and install avg free or clamav. Then scan your windows hard drive.

---

### Post by cirabisi2009 on 2009-09-02
is clamav more ubuntu friendly? or will i have to download something special for avg on ubuntu?

---

### Post by NoaHall on 2009-09-02
clamav is more command line based (although there is a gui), and it scans all, avg is the same, but i think it's more gui based.

---

### Post by sigurnjak on 2009-09-02
[http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html)

Try this! Install , register , mount your windows partition and scan away , worked for me like a charm .

---

### Post by running_rabbit07 on 2009-09-02
Bit defender can scan the Windows drive and remove the viruses. A quick google will help you get it installed.

---

### Post by kevinatkins on 2009-09-02
In this situation, you might want to check out Dr. Web ([http://www.freedrweb.com/](http://www.freedrweb.com/)) - grab their Live CD and boot from that, then run a full scan on the Windows partition. This has got me out of trouble where AVG and others have failed. Oh, and one other thing - before attempting to repair a virus infection, make sure you *turn off* Windows System Restore first - you can always enable it again afterwards...

---

### Post by cirabisi2009 on 2009-09-02
wait i have an issue... i used wubi to install ubuntu.... i cant find my windows partition :( im in ubuntu now too.

---

### Post by NoaHall on 2009-09-02
Then do as kevin said, and download the Dr.Web live disk.

---

### Post by bear24rw on 2009-09-02
or burn a live cd and boot from it..

---

### Post by cirabisi2009 on 2009-09-02
i used Dr. Web but it didnt seem to get rid of it. i am back in windows and its still here after a complete scan with it. bit defender didnt do it either. nothing will get infected if i transfer everything to ubuntu and then back to a fresh re-installation of XP right?

---

### Post by mike555 on 2009-09-02
When you transfer files make sure you don't transfer the virus with them ......... check hidden files too ....

---

### Post by Petrosclark on 2009-09-02
I think you should try Malwarebytes.  Always worked for me.  Just go to [http://www.malwarebytes.org]("http://www.malwarebytes.org/") and install it, update and run it.

---

### Post by cirabisi2009 on 2009-09-02
> **Petrosclark said:**
> I think you should try Malwarebytes.  Always worked for me.  Just go to [http://www.malwarebytes.org]("http://www.malwarebytes.org/") and install it, update and run it.


k i will give it a shot.

---

### Post by RetchingRabbit on 2009-09-02
> **cirabisi2009 said:**
> i used Dr. Web but it didnt seem to get rid of it. i am back in windows and its still here after a complete scan with it. bit defender didnt do it either. nothing will get infected if i transfer everything to ubuntu and then back to a fresh re-installation of XP right?

AFAIK, there is no way to save a Wubi install through a reinstall of Windows. just another reason not to use Wubi except for evealuation. It just isn't the same as a "real" install.

---

### Post by cirabisi2009 on 2009-09-03
well nothing has worked so i am sending it to a good friend who can do it for sure. but thanks for all the suggestion guys. and i am doing an install from cd when i get it back so ubuntu will ACTUALLY be aprt of the system?

---

### Post by zeroseven0183 on 2009-09-04
You can also try to use [Kaspersky Online Scanner]("http://www.kaspersky.com/kos/eng/partner/default/pages/default/check.html") or [ESET Online Scanner]("http://www.eset.com/onlinescan") in Windows.

By the way, I believe you can still access the Windows file even you installed it through Wubi. Check out the /host folder.

---

### Post by R_W322 on 2009-09-04
I'd download Winpatrol for Windows XP boot up XP Isolate the program and stop it from running (Winpatrol will do this) Then reboot in to safe mode to safely delete the file and delete the registry edit it most definitily left. Shouldn't be to hard to find where it is in the Regedit, just do a google search on it. I wouldn't try using another O.S. to eliminate a simple virus. 

RYAN.WDZIECZNY

---

### Post by Bucky Ball on 2009-09-04
Have you tried in windows:

Start->Run

Type 'msconfig'. In there you will find the start up items (last tab on right from memory) and your 'virus' icon. Untick it and reboot into windows. Still there? 

It is probably that simple. Will still be on your system but not doing much (unless you decide to download the 'anti-spyware'!).

---

