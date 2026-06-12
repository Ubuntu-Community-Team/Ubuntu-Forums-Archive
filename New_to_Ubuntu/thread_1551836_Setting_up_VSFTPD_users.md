---
title: "Setting up VSFTPD users"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by mewsicmasta on 2010-08-12
I am having a mind boggling problem with my ubuntu server 10.4 LTS and  need some assistance. As a disclaimer i am new to the ubuntu/linux world  so please keep that in mind with responses. My end goal is to store  movies, music and files on my pc running ubuntu server and be able to  access it from wherever. I pretty much am setting up a FTP server. I  have 2 users on the pc currently, me and a user called test. 

The  files that are in my home directory are the ones i want to share. I  downloaded VSFTPD and configured that to the best of my ability. The  files i want to share are under my account which is admin. I only  created the other user so that when i have my family and friends connect  to my machine they dont have to use my login info. problem is the test  account doesnt have any of the files that i want to share. its blank. So  i have 2 questions.

1. How do i set it up to where the "test" account has access to my downloaded files?

2. Is there a more efficient way to do this?

My  end goal is to have a ftp server that my family can use and download  files from. For all i care i rather just put the files in a folder that  is accessible by both users.

---

### Post by Bachstelze on 2010-08-12
Normally, your home directory is private, meaning that other users, such as your 'test' user, aren't supposed to be able to access files in it.  The "proper" way to do what you want would probably be to put all the files you want to share into test's own home directory (which is what you see whan you connect to yor FTP with it), but if you can't do that, you can make a folder in your home directory accessible from test's home directory by doing a bind mount. For example, if you have a directory called Movies in your home directory, you can do:

```
sudo mkdir /home/test/Movies
sudo mount -o bind /home/`whoami`/Movies /home/test/Movies
```

And that will make your and test's Movies directories the same (when you put a file in yours, it will also appear in the other).

---

