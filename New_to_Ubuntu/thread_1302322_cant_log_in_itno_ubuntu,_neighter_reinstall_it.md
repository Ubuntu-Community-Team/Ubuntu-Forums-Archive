---
title: "cant log in itno ubuntu, neighter reinstall it"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by patchido on 2009-10-26
well, i believe that my other post wont be visible, it even changed topic, so i think it is better to do this one.

[http://ubuntuforums.org/showthread.php?t=1296679](http://ubuntuforums.org/showthread.php?t=1296679)

i cant log into ubuntu, becuase i changed the home folder, and for some reason i cant log into ubuntu live neihgter reinstall ubuntu, or format via windows

---

### Post by nothingspecial on 2009-10-27
Boot into recovery mode. Press escape at the grub loading dialogue and choose "recovery mode > drop to root shell prompt".



```
chown -R [COLOR="Red"]username[/COLOR]:[COLOR="Red"]username[/COLOR] /home/[COLOR="Red"]username[/COLOR]
```
```
chmod -R 775 /home/[COLOR="Red"]username[/COLOR]
```
```
chmod 644 /home/[COLOR="Red"]username[/COLOR]/.dmrc
```
```
chmod 644 /home/[COLOR="Red"]username[/COLOR]/.ICEauthority
```

*change each occurence of username to your actual username*

reboot.

---

### Post by nothingspecial on 2009-10-27
Another fix occurs to me, if that doesn't work.

Boot into recovery mode as before and create a new user

```
useradd bob admin
```

Change bob to whatever username you like.

Log in as bob (or whoever) and copy all your stuff to bob`s home directory.

Don`t know if this is necessary but make sure nothing that you`ve copied is still owned by your old username
```

sudo chown -R bob:bob /home/bob
```

Once you are sure bob has got everything you need/want from your original home folder you can delete your old user account if you want to, you don`t have to.

[COLOR="Red"][SIZE="3"]This will remove your old home directory do not do it unless you are sure[/SIZE][/COLOR]

```
sudo userdel -r username
```

Then from bobs account you can recreate your old account or you can stick with bob.

---

### Post by patchido on 2009-10-28
didnt work for eighter of the 2 methods, but do u know why cant i reinstall

---

### Post by nothingspecial on 2009-10-29
What happened when you tried them?

Are you able to boot into recovery mode?

---

### Post by patchido on 2009-10-29
recovery yes, i get same error, need 644 permission, something like that|

---

### Post by nothingspecial on 2009-10-29
I need to go to bed now but I need to know exactly what you have done. Do you still have a home directory? Why would the recovery shell not let you make another account? What errors are you getting --- exactly?

---

