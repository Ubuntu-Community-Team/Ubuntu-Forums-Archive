---
title: "Password required to connect to network on startup"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Judgegeo on 2009-04-28
How do I disable this annoying feature? 

Thanks.

---

### Post by MockY on 2009-04-28
Assume that you are talking about wireless.
If so, get rid of NetworkManager all together and install Wicd instead.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by y_garti on 2009-04-28
do you have auto login and the keyring ask you for your password every-time you do the auto-login ?

---

### Post by Judgegeo on 2009-04-28
> **y_garti said:**
> do you have auto login and the keyring ask you for your password every-time you do the auto-login ?

Yea, why is there no "remember password" or some kind of options to disable it. It's messing with my conky, media server, the lot.

---

### Post by lovinglinux on 2009-04-28
You need to setup the keyring password. This is a problem usually associated with automatic login. Read explanation below:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by Judgegeo on 2009-04-28
> **lovinglinux said:**
> You need to setup the keyring password. This is a problem usually associated with automatic login. Read explanation below:

Thanks, but I went with the earlier suggestions and installed wicd.

---

### Post by lovinglinux on 2009-04-28
> **Judgegeo said:**
> Thanks, but I went with the earlier suggestions and installed wicd.

No problem. Whatever works best for you  ;)

---

### Post by stchman on 2009-04-28
> **Judgegeo said:**
> How do I disable this annoying feature? 

Thanks.

If your wireless is encrypted then your computer will have to supply the password every time it uses the router.  Fortunately Ubuntu stores the passphrase in the keyring so once you enter it once no need to enter it again.

---

### Post by The Pinny Parlour on 2009-05-01
> **lovinglinux said:**
> You need to setup the keyring password. This is a problem usually associated with automatic login. Read explanation below:

Hello

Firstly, thanks for the assistance you have provided.

This feature of asking for a password to access networking functions is a flat out pain in the butt.  I followed your instructions but I don't have a "password keyrings" tab in step 3. 

HOW THE HECK DO I TURN THIS CRAPPY FEATURE OFF?

---

### Post by wersdaluv on 2009-05-01
It requires you to enter password to the keyring because the keyring provides access to saved wlan passwords. Thus, this feature is for your security. This is not very useful for everyone, though. The only solution I know of is using wicd instead.

---

### Post by The Pinny Parlour on 2009-05-01
> **wersdaluv said:**
> It requires you to enter password to the keyring because the keyring provides access to saved wlan passwords. Thus, this feature is for your security. This is not very useful for everyone, though. The only solution I know of is using wicd instead.

Thank you.  I can understand that it's for security, but it is god darn annoying.  Thankfully I have fixed it by nuking every instance of password in applications>accessories>passwords and encryption keys.  I then logged out and back in again, and entered my wireless pass-phrase and now it auto connects without the keyring bullchit.  
What I don't understand is, why does it now auto login?  What is the difference security wise and purpose of that STUPID keyring login, then manual wlan login?  

Anyway, I'm glad it's fixed but I'm rolling back to Intrepid as jaunty is a right pain.  vlc and totem pauses and frame skips on playback.

---

### Post by Judgegeo on 2009-05-01
> **wersdaluv said:**
> It requires you to enter password to the keyring because the keyring provides access to saved wlan passwords. Thus, this feature is for your security. This is not very useful for everyone, though. The only solution I know of is using wicd instead.

When I installed wicd, everything was fine.. but then after reboot it said "CONNECTED" when it wasnt.. I then had to manually connect to the internet which was a pain and re-install gnome-network-manager.

I've found a way round the keyring frustration though,

Open gnm, goto the connection and click edit, at the bottom there should be an option to "save for all users" or "allow all users" something along those lines, once set I havent had a single request for a password :KS

---

### Post by MC707 on 2009-09-07
> **Judgegeo said:**
> 
Open gnm, goto the connection and click edit, at the bottom there should be an option to "save for all users" or "allow all users" something along those lines, once set I havent had a single request for a password :KS

Nice, that worked for me. Your explanation is vague, though... so I will explain step by step for ppl with the same annoying *feature*.

Right click the wireless icon, then click edit connections. Select the wireless tab, then select the wireless network you wish to connect to. Press the edit button on the right. Finally, tick on the "available to all users" box to the left of the cancel button. Finally, click apply and enter your password for the last time. Done, no more asking after rebooting or logging off.

---

