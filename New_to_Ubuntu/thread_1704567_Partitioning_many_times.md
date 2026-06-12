---
title: "Partitioning many times"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by ssdt on 2011-03-10
Is there any problem with partitioning and deleting a partition many times? For ex. is there any hard drive space that is lost because of that?

I have done a couple of partitions because my computer is facing .ICEauthority error where the Ubuntu partition does not load up. If anyone has had problem with the .ICEauthority and about updating it, please let me know a possible solution because in 10.04 the solutions provided in the forums does not help me at all.

Thank you.

---

### Post by psusi on 2011-03-10
To answer the first part of your question: no.  I can't figure out what on earth it has to do with the second part.

---

### Post by oldfred on 2011-03-10
If you have moved home around or changed the owner on a reinstall, you make get some errors. Partitioning should not make any difference. It is still just writing data to a hard drive.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---

### Post by ssdt on 2011-04-03
I have figured out the solution for this error. Just create a directory ./ICEauthority with proper permission for the current user to use and the problem should easily be fixed. 
This problem is due to Veetle TV that I installed to my computer.

---

