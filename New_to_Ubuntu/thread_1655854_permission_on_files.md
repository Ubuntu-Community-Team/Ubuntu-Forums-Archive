---
title: "permission on files"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Kashyap.K on 2010-12-30
I am not having execute permission on 'any' of my files in Ubuntu 10.10! i didn't have this problem when i was using 10.04. I upgraded it two days back. Since then I am facing this problem :( Moreover I am not able to create files/ directories in my root directory i.e my '/' directory. Please help me out.

---

### Post by Paqman on 2010-12-30
The only files and folders you should have permission to change are those in /home/username, not root.

If you're not able to make changes to your home folder either then open a terminal and run this command:
```
sudo chown -R username:username /home/username
```

---

