---
title: "reinstate user account"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by driven1 on 2010-02-14
I have a user account in the home folder that was removed from the user list. I wanted to add the user back, but I can't because that user name is already used ie there is a home folder. I don't know how to restore that user account. Failing a restoration, I can't delete the inactive home folder either and start fresh. At this point either way is fine. Any advice.

---

### Post by night_fox on 2010-02-14
Go into the terminal,

```
sudo mv /home/user /home/user-backup # rename the folder
```
now recreate that user (Like you tried to do)
```
sudo mv /home/user-backup /home/user # move all the stuff back
sudo chown -R user /home/user # change ownership
```

---

### Post by driven1 on 2010-02-14
Worked like a charm. Thanks.

---

