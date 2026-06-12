---
title: "User on multiple computer"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by MWilliams13 on 2007-09-04
On Edubuntu could there be anyway to put users on a network and allow them to connect to their profiles with the same password without doing it manually on each one. We are considering converting our school district from Windows XP to Edubuntu,Ubuntu,or Kubuntu. We already have servers for files so being able to acess files is no problem we can just let them (the students) acess a central network. Any help for this? If you need more details ask and I can fill that out.

---

### Post by simonn on 2007-09-04
I have not done this.

At a high level, what you want to do is use NIS to "share" the login/password stuff and NFS to share /home from the server. However, I know very little about NIS so cannot be of any help other than point you towards it. Google is your friend.

EDIT: Have a look at [http://ubuntuforums.org/showthread.php?t=508862&highlight=NIS](http://ubuntuforums.org/showthread.php?t=508862&highlight=NIS)

---

### Post by MWilliams13 on 2007-09-05
Thank You. I have started to get this to work.

---

