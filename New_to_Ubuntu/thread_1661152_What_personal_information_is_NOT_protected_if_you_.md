---
title: "What personal information is NOT protected if you just encrypt the home directories?"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by sarc on 2011-01-06
I run Ubuntu 10.4 on an external USB drive.  I have some confidential/personal information an fairly high chance of technically savvy people getting to my drive when I'm not around.  I have learned from previous posts that some user information may be in the unencrypted root directory (logs of websites accessed, logs of files accessed etc.) and in the swap partition.  So could someone help me determine if I need some additional security measure (I see from other posts that entire drive necryption is difficult/convoluted in Linux...) Thanks!!!

---

### Post by JeffDavidoff on 2011-01-07
Most importantly you have to make sure that the swap space is encrypted. If Linux is swapping out data to disk if the memory is full it will reside on disk in clear text. According to [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) starting from Ubuntu 9.10 and selecting the Encrypted Home option will automatically have encrypted swap space.

Another critical place are temporary files located in directories like /tmp/, /var/tmp/ where currently open files are held. Make sure those files are securely deleted at the end of your session.

Furthermore, the system logs different user activities in /var/log/. You might want to check those logfiles for traces of your activities.

---

