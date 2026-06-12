---
title: "[SOLVED] Security doubts"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-01-06
Hi Friends,

          As I am a new user to Ubuntu and Linux, pls clarify my doubts ons security.

1. I have read in the forums that default root account is locked. So, I can believe that my system cannot be hacked?

2. Any login user who uses sudo command can take root previliages?

3. If #2 is not possible then which users can use sudo command and take root previlages?

Thanks.

---

### Post by shifty_powers on 2009-01-06
1). yes that is true about root account being locked by default. it does not make it impossible to hack you account, but it does make it very, very hard.

2). only if they have been given admin privileges. if it is a limited account, they will not be able to use sudo. (unless i am wrong...)

3). only those which you have setup for this, i.e. accounts that have been given admin privileges. (what this means is that they are part of the sudo group).

---

### Post by Titan8990 on 2009-01-06
1. Everything can be hacked but it does make it much more difficult.

2. Yes, but they must be a member of the admin group or any other group you manually add to /etc/sudoers

3. Whichever you want :).

---

### Post by donkyhotay on 2009-01-06
Theoretically any system that is powered on can be hacked, however realistically your pretty safe with linux (unless they are physically at your computer) because there are no unneeded network services. Even if someone does gain physical access (which realistically is a whole other problem), Ubuntu is nice because without the root account enabled a hacker needs both username & password to access the system (rather then just password). Any account that is configured to administer the account can have root access (the first account you create will have this by default) however you can choose whether you want a user to have admin access or not.

---

### Post by Tim Sharitt on 2009-01-06
Only users created with admistrator priviledges can take full root priviledges. Desktop users can do things like mount drives, use a modem, etc. Or you can create completly unpriveledged users.

---

### Post by kwacka on 2009-01-06
To gain access and hack your system they would need to identify a sudo user's password, in the same way thatthey would need root's pass to ceack your setup.

Any user can be placed into the sudo group, and thus gain administrative access, by someone who is already a member of the sudo group. i.e. the more users that have sudo access, the less secure your setup.

The advantage of sudo over su is that you are only accessing specific administraive activities (e.g. adding a specific application) rather than opening up the complete system - which is what happens when you are running as root.

---

### Post by B34ST1Y on 2009-01-06
> **Jeyaganeshdj said:**
> Hi Friends,

          As I am a new user to Ubuntu and Linux, pls clarify my doubts ons security.

1. I have read in the forums that default root account is locked. So, I can believe that my system cannot be hacked?

2. Any login user who uses sudo command can take root previliages?

3. If #2 is not possible then which users can use sudo command and take root previlages?

Thanks.

anything is "hackable" per-se. thinking you're unhackable is just ignorant

---

### Post by shifty_powers on 2009-01-06
a bit harsh, not everyone is a computer expert after all...

---

### Post by Titan8990 on 2009-01-06
> To gain access and hack your system they would need to identify a sudo user's password, in the same way thatthey would need root's pass to ceack your setup.


This not true. For example, if you ran Apache as a root daemon and that Apache service is exploited then your whole machine is compromised. However, by default when you install daemons via aptitude it will never run a daemon as root.

---

### Post by The Cog on 2009-01-06
Unless you edit the sudoers file, it is only users who are members of the **admin** group who can use sudo to raise their priviledge. And only the very first user (created during installation) who is made a member of the **admin** group by default.

---

