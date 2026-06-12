---
title: "Thunderbird - Need to move email across installations"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Todd in Berlin on 2011-07-30
Hi. I installed 11.04 alongside 10.10. I was able to manually copy e.g. Skype archive, but am not able to do similar in Thunderbird -- with the email archive. I realize that I can export the Address Book. I am pretty lost with this, can't even find where to put it, if I need to change Permissions etc. Thanks.

---

### Post by 73ckn797 on 2011-07-30
Copy the .thunderbird folder from your /home in 10.10 to /home in 11.04. You may need to delete the profile created when Thunderbird was installed. That would be titled *.default. The "*" is a wildcard, of course.

If there are permission issues do it via terminal:
```
 sudo nautilus
``` and change permissions if necessary.

---

### Post by Todd in Berlin on 2011-07-30
Thanks! That worked perfectly.

---

### Post by 73ckn797 on 2011-07-30
You're welcome. I had the same issue several years ago and know what you were dealing with. I discovered the fix out of just trying it to see what would happen. Whenever I have upgraded my system I keep the /home folder since it is on a separate partition.

Go to "Thread Tools" and mark this solved. It will help some one else.

---

