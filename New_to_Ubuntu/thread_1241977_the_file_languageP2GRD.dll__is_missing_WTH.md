---
title: "the file language\\P2GRD.dll  is missing WTH"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-16
downloaded ubuntu twice now... keep getting the same message, the file [language\\P2GRD.dll]  is missing" i tried this with power2go iso buner and deamon tools lite what is going on here?

---

### Post by Paddy Landau on 2009-08-16
> **R3fr4cti0n said:**
> downloaded ubuntu twice now... keep getting the same message, the file [language\\P2GRD.dll]  is missing" i tried this with power2go iso buner and deamon tools lite what is going on here?
We need a little more information, because this doesn't sound right.


[LIST=1]
[*]What version have you downloaded... Is this Wubi?
[*]After downloading, did you check the MD5 sum?
[*]After you burned to disk, how specifically did you attempt to install?
[/LIST]

The answers should help us help you better.

---

### Post by R3fr4cti0n on 2009-08-16
> **Paddy Landau said:**
> We need a little more information, because this doesn't sound right.


[LIST=1]
[*]What version have you downloaded... Is this Wubi?
[*]After downloading, did you check the MD5 sum?
[*]After you burned to disk, how specifically did you attempt to install?
[/LIST]

The answers should help us help you better.
 

kk sorry im new

1 i downloaded the 9.04 the new one on the opening screen to ubuntu
2 i dont know what a md5 sum is but i never even got it open it wont allow, as soon as it finshed dl'ing i got that message and it will not let me go any further
3 no install attempted i cant even get past clicking it with out getting the error message no i could not even burn it.

i am atempting to get the 8.10 intrep now is it a prob with my computer or with the Dl?

---

### Post by Paddy Landau on 2009-08-16
> **R3fr4cti0n said:**
> i am atempting to get the 8.10 intrep now is it a prob with my computer or with the Dl?
It's a problem with your download.

The message about a dll is a Windows problem, as Linux doesn't use dll. That's why I asked the questions.

Perhaps you can download and burn 9.04 (Jaunty) from a friend's machine or from a library computer? Clearly, there's a problem with your computer. (Or try downloading using a different browser -- it may be the browser that's the problem.)

Once you've downloaded, *before* you burn a CD, check the MD5 sum.
[How to MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM")
[Find what the MD5 sum should be]("https://help.ubuntu.com/community/UbuntuHashes")
If for some reason you can't check the MD5 sum, then just skip this step.

Once you've burned the CD, *before* you install, boot from the CD. There'll be an option to check the CD for errors. Choose that option. It will check that the CD has been burned correctly.

If that passes, then reboot to "Try Ubuntu without making any changes to your computer." This will help you find out whether Ubuntu will work on your machine, for example whether the Internet works. It will be slow (it's running from a CD, after all), but it's worth doing. Play around a bit with it.

If all that passes, then reboot and install.

**N.B. If you have any data that you wish to keep, [COLOR=DarkRed]do a backup first[/COLOR].** Although the Ubuntu installation is reliable, sometimes there are problems (or you choose the wrong option) and you can lose your Windows data.

---

### Post by Old_Grey_Wolf on 2009-08-16
Looks like a problem with the Power2go software. Try to reinstall it or download the free software imgburn [http://www.imgburn.com/](http://www.imgburn.com/) and use that instead.

---

### Post by R3fr4cti0n on 2009-08-16
problem solved it was the burner, burning it as i type

---

