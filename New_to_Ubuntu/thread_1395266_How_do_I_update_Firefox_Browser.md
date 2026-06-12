---
title: "How do I update Firefox Browser?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-31
Hi can I do simply sudo update firefox or something like that?

I am using 3.0.17 which is like 2 years old.

Thanks!

---

### Post by PPPilot on 2010-01-31
When I installed Karmic last fall, it installed Firefox 3.5.5. It has been updated twice automatically from the repositories and is now at 3.5.7. Since you are running Karmic it should auto update along with all the other software updates. You could try this from Terminal:

                                 > sudo aptitude update && sudo aptitude safe-upgradeThis also give you a birds eye view of whats going on during the update process and should update everything.

---

### Post by mattbutsko on 2010-01-31
firefox is automatically updated with ubuntu's update manager.

---

### Post by listerdl on 2010-01-31
OK! Sorry the computer i am on is an older version of ubuntu - my sig is for another machine...

so if it is automatically updated, my settings must be incorrect...

thanks for replues.

---

### Post by deer dance on 2010-01-31
You could use Ubuntuzilla to update to 3.6 which isn't available in the repositories yet.

---

### Post by lovinglinux on 2010-02-01
See the Installing Other Versions section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It explains the methods available. I recommend Ubuntuzilla, if you are on 32bit.

Direct link to the information you want: [http://tinyurl.com/yb98jwy](http://tinyurl.com/yb98jwy)

---

### Post by lud on 2010-02-01
What about

System->Administration->Update Manager

?

---

### Post by nanotube on 2010-02-01
> **lud said:**
> What about

System->Administration->Update Manager

?

that pulls stuff from the same repositories as synaptic. if you don't have a repository with ff3.6 in it, update manager is not going to find it.

---

