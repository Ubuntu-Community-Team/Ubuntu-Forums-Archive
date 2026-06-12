---
title: "SVN error on NTFS partition from Ubuntu"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by pteri498 on 2010-03-08
I tried doing an svn checkout from a directory on an ntfs partition and get the following error:

```

cedric@cedric-eee:~/documents/school/309 $ svn co svn+ssh://path/to/project project
user@path's password: 
svn: Can't set permissions on 'project/.svn/tempfile.2.tmp': Operation not permitted

```

I realize that there's no permission setting on an ntfs partition, but how do I make subversion not care about this?

---

### Post by kumarldh on 2010-05-03
Just encountered this situation, it was working before I upgraded to Lucid Lynx.

---

### Post by kumarldh on 2010-05-03
Well, I just looked into my /etc/fstab and I found that the user who is trying to run svn up doesn't have enough permissions for the filesystem on which the user is trying to run svn up/add/* commands. I simply did sudo svn up and it worked.

---

### Post by fvaresi on 2010-06-04
Instead of using sudo, you should mount the partition using a different user/group. You can do this by editing the fstab line and adding the options **uid=<your_user_id>,gid=<your_group_id>**.

---

