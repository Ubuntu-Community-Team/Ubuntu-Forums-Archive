---
title: "Password? What password?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Daniel5759 on 2011-03-07
I freely admit to being new to Ubuntu.I have it installed on a 4gb thumb drive. It seems to work reasonably well. But, when i try to access certain things like computer janitor, or the open as administrator command. I get a screen asking for a password. Since I never set one. I have no idea what it's asking for. How can I resolve this? Any help would be greatly appreciated. Thank you.

---

### Post by wojox on 2011-03-07
Use the password you login with. Unless you mean your running live and don't log in?

---

### Post by col48 on 2011-03-07
Not sure how you could get away without setting a password - it's just about the first thing the install would ask for (and ask you to retype for confirmation).  Have you tried just hitting Enter?

I think there are ways of forcing password (re)set using a Live CD which does not require a password itself.  Search this forum, if no-one else replies with something more specific.

---

### Post by Daniel5759 on 2011-03-07
I never set a log in password. That's why I'm so confused about this. It's asking for a password that doesn't exist.

---

### Post by Daniel5759 on 2011-03-07
I installed it to a thumb drive using the iso image and the install utility. So, it never asked me to create a password.

---

### Post by uRock on 2011-03-07
> **Daniel5759 said:**
> I never set a log in password. That's why I'm so confused about this. It's asking for a password that doesn't exist.

You didn't create a username and password when installing? If not, then hit enter when the screen pops up and it should work.

---

### Post by wojox on 2011-03-07
Open a terminal and try this:

```
sudo passwd ubuntu
```

---

### Post by Daniel5759 on 2011-03-07
Tried pressing enter. No go. :(

---

### Post by uRock on 2011-03-07
Is it the default keyring popping up?

---

### Post by Daniel5759 on 2011-03-07
I followed your instructions. I keep getting an incorrect password message even though I type it in correctly. What now?

---

### Post by Daniel5759 on 2011-03-07
It's a box that pops up asking for the administrative password

---

### Post by uRock on 2011-03-07
If you created a LiveUSB from the ISO and didn't actually install it, then it shouldn't ask for a password at all. With my LiveUSB, I run sudo commands and do other admin stuff without it asking for a password. However, some apps ask for a default keyring password that it required me to set up for certain applications.

---

### Post by Daniel5759 on 2011-03-07
BTW. I am running live.

---

### Post by wojox on 2011-03-07
Are you sure you didn't install it on the flash drive instead of just burning it. Like uRock said the root account is inactive on a Live enviorment.

---

### Post by wojox on 2011-03-07
Maybe you got a bad burn. How did you burn the image?

---

### Post by Daniel5759 on 2011-03-07
I installed it using the installation utility that's available from the site i also downloaded the ISO image. Pendrivelinux.com.

---

### Post by Daniel5759 on 2011-03-07
It's asking for a password for computer janitor, gparted and for open as administrator. I don't know why it's doing that. The installation using the is ISO is and the utility never asked me to create a password. So, I never did.

---

### Post by migs73 on 2011-03-07
> **Daniel5759 said:**
> BTW. I am running live.

I have had a look at Pendrivelinux and there are options there to have a LiveUSB and a full USB install. When booting from the USB do have the option screen asking if you wish to install, or try ubuntu without making any changes to your system?

If you don't get these options, you have a full install on your USB drive, hence why it is asking for your password. We have to know how Ubuntu is installed as the outcomes are very different.

Mike

---

### Post by Daniel5759 on 2011-03-07
As  *have already stated. It is a live install. Those options are there. I am being asked for a non existent password in certain *programs in Ubuntu. I don't know how to explain it any better that that. Now. Can somebody give me an idea for fixing this problem? Or am I just spinning my wheels? I will say this again. I downloaded the ISO and the installation utility. I ran the utility which placed a live copy of Linux on my 4gb thumb drive. I try running things like Gparted and computer janitor and I get a box on my screen asking for an administrative password which has never been set. How do I get past that so I can use those utilities? Anybody who can answer that has my undying gratitude.

---

### Post by uRock on 2011-03-07
Reinstall it using a different image file.

---

### Post by Dorsenstein on 2011-03-07
I'm pretty sure the default pass is either 1234 or 12345. One of those should work if you never set a password.

---

### Post by migs73 on 2011-03-07
> **Daniel5759 said:**
> As  *have already stated. It is a live install. Those options are there. *

Sorry if I have offended you, I was just trying to ascertain in other ways what the type of install was. The terminology sometimes is confusing  and doesn't translate well.

The fault you were reporting **should** not happen in a live install (as you know) and the outcome would be to reinstall (as Urock suggests above). If it was a full install you can reset your password from the recovery mode.

Mike :)

---

### Post by aolone on 2011-06-04
at the login screen you will see "ubuntu" above the entry field, enter ubuntu for ID and press enter. At the password screen you will see at the bottom a toolbar and click on the arrow near ubuntu and select recovery console. The recovery console will open, move the mouse to the recovery console to enable it, the cursor will become black. Enter: sudo passwd ubuntu and press enter it will ask you to enter a new unix password, max 8 characters, then again it will ask you to confirm. Now for for the password to work you cannot reboot, just type: exit and enter, you will have the login screen again, now enter ubuntu for id and enter the password you have used and you will be able to login. You may have to repeat this every time you boot, or not if you're lucky.

---

