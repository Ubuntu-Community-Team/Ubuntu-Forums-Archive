---
title: "what should i do to be super user ????"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by magedsoft on 2010-12-05
what should i do to be super user ????


what sites i should register on it ....what threads i should read....what things i should know 

...........................etc

---

### Post by Rubi1200 on 2010-12-05
What exactly do you mean and what do you want to do?

If you mean, login as root with a graphical interface; we will not tell you how to do that as it violates forum policy.

If you mean, escalate privileges in order to carry out administrative tasks, see here:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by dacanadianbomb on 2010-12-05
The first user you create during the installation is a super-user that can by default run sudo commands to run with root privileges.

I believe you can add additional users to administer the system by using the "Users and groups" utility under System->Administration->
Highlight user -> Advanced settings->User privileges-> and check mark "Administer the system" amongst the other options the user should have.
This will allow them to run sudo commands.

Is this what you are looking for ?

---

### Post by arjunlalb on 2010-12-05
type 'su' in terminal and enter the password. It will take you to the superuser mode.

---

### Post by coffeecat on 2010-12-05
> **arjunlalb said:**
> type 'su' in terminal and enter the password. It will take you to the superuser mode.

Not in a default installation of Ubuntu, it won't. :wink:

This link already posted by Rubi1200, but it sounds as though it needs posting again. :sigh:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CharlesA on 2010-12-05
arjunlalb: Please don't post how to enable the root account. I've moved your post to the jail.

OP: Read the link that coffeecat posted. :)

---

### Post by mc4man on 2010-12-05
Maybe I'm misunderstanding the OP but I take 'super' to be an adjective as in being a super user of...
Maybe they'll clear that up upon returning

---

### Post by CharlesA on 2010-12-05
> **mc4man said:**
> Maybe I'm misunderstanding the OP but I take 'super' to be an adjective as in being a super user of...
Maybe they'll clear that up upon returning
Good point. I just skimmed the thread. >.<

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

---

