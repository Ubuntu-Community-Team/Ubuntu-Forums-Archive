---
title: "samba password????"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by stevek123 on 2010-06-02
I'm totally miffed right now. Somehow my network / sharing got messed up and I cant access the 'shared' folders from my upstairs computer (Hardy) to my downstairs computer (Karmic). I can get shared from Karmic to Hardy wiothout issue but when I try to mount or open the shared folders from Hardy into Karmic is says "password required'. Then it wont take the passwork from either of the 2 systems. WTF? And as for password required = no its not! Very frustrated and pressed for time.

I know the folders will mount cuz they do when i open rhythmbox to use music i have up there.

---

### Post by darkdragn on 2010-06-02
Have you tried just quickly ssh-ing into your upstairs computer ( for the lazy, lol, like me) or walking up there and running smbpasswd to change the password?
And while you're at it checking your /etc/samba/smb.conf. Maybe something corrupted it. Good luck.

---

### Post by stevek123 on 2010-06-02
i looked in samba.conf and it looks like the 4 'new shares' did not get written into it. Not sure why. I'll manually edit this later and try again. FWIW i dont think I ever entered a smbpasswd - sure didnt down here on karmic and it runs fine. the smb config only shows the shared folders from when i set it up back when i was running Hardy with M$xp (now gone!).

---

### Post by darkdragn on 2010-06-02
KK, Did you get a chance to check the guest option in samba? If you never really had passwords set up, i'm betting that guest was on, and guests were allowed both read and write operations. Check to see if that is still the case, and good luck... I'm sorry that this issue occured, i know how frustrating things like this can be.

---

### Post by doas777 on 2010-06-02
just to clarify, are you using gui sharing (rclick a folder) or classic samba (with the smb.conf)?
these systems are not the same.


on the server box, have you ever registered the remote user account with samba? first you must create the user account in ubuntu, and ensure that the new user has permission to the shared content. after that, run
```
sudo passwd -a <username>
```
to tell samba what the password associated with that account is.

---

