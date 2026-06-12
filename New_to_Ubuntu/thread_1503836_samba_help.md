---
title: "samba help"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by keylokes on 2010-06-07
not sure if this is the right forum for this ..

im using linux on my computer i also have a moded xbox that i can share or play movies to and from my pc. i do that with "samba" but everytime i reboot my computer i have to recreate the user and enable it i do it with this:

"sudo smbpasswd -a MyUserName"
asks me for password twice, then
"sudo smbpasswd -e MyUserName"

is there a way to avoid doing this all the time.??
so that when i tuen it on or reboot its ready to go???
thanks in Advance.

---

### Post by cariboo on 2010-06-07
Try:

```
sudo smbpasswd -L -a <user>
```

and

```
sudo smbpasswd -L -e <user>
```

The **-L** means run in local mode, so it should save the password locally.

---

### Post by keylokes on 2010-06-08
thanks .. but it didnt do it ..

i erased my windows partition last night .. and did a clean install of lucid .. did all the upgrades and fun stuff .. and now it doesnt start automatically .. butonce i start it i can log in no problem with my account password. i would prefer a different pasword but its fine. ill eventually figure it out..

thanks though.. now off to look so it can start automatially. ThankYou

--EDIT ...

actually it is turned on .. but i cant see any folders .. i have to turn it off then on again and it works again. ("sudo /etc/init.d/smbd stop" "sudo /etc/init.d/smbd start") not fun.

---

