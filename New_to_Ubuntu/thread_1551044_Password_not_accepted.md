---
title: "Password not accepted"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Sodear on 2010-08-11
Cannot log-in when starting Ubuntu Lucid Lynx: password failure though I have not changed it.
This happened after typing 'sudo apt-get purge evolution' to solve a problem with Evolution e-mail, and then re-starting the computer.
So I need help in getting into a repair or recovery mode and specific help in re-setting the password so that I do not have to completely re-install Ubuntu.
Then I will probably still have a problem with Evolution which does everything except show/get/send mail.

---

### Post by Ozymandias_117 on 2010-08-11
During boot, hold shift. That will pull up the GRUB menu. Then select "recovery mode", then select Root shell (or something to that effect). Then type ```
passwd *username*
``` it will then prompt you for a new password.

---

### Post by Sodear on 2010-08-16
Followed your instructions - sorry for time lapse.  Did not work as expected: after re-entering the pwd I could continue to log-in as one of the options but was left with a command prompt.  Had no idea what to do with that.  Any advice?

---

### Post by Ozymandias_117 on 2010-08-27
> **Sodear said:**
> Followed your instructions - sorry for time lapse.  Did not work as expected: after re-entering the pwd I could continue to log-in as one of the options but was left with a command prompt.  Had no idea what to do with that.  Any advice?

Reboot :P or you can type ```
startx
``` Been out of town, just got back :D

---

### Post by engineglue on 2011-08-26
Ozymandias_117... This method is incredibly too easy. Is there a way to protect my Ubuntu box from someone doing this to gain access into my box? Yo, thanks, sup, dude... yeah..

---

### Post by SavageWolf on 2011-08-26
Anyone who has physical access the the computer generally has access to everything (Unless you encrypt stuff). They could just pop in a live CD, or just rip out the hard disk.

---

### Post by zealibib slaughter on 2011-08-26
> **engineglue said:**
> Ozymandias_117... This method is incredibly too easy. Is there a way to protect my Ubuntu box from someone doing this to gain access into my box? Yo, thanks, sup, dude... yeah..
 
Encrypt your home folder and set a grub password. But as mentioned above there is no security when someone has physical access to your system.

---

