---
title: "Question on encrypted folders, vsfptd, samba"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by judderwocky on 2011-01-20
This is a dumb question. I have been playing around with VSFTPD and the basic network sharing system. I have an encrypted home folder.

My question is this: network sharing doesn't occur over the windows/Samba server because of the encryption... which is what i wanted. however it seems that I am still able to login as myself through ftp and access my encrypted files. this seems strange to me, because I thought that VSFTPD was actually running as a different user or as root, so i'm confused as to how it can read my files... is the system decrypting the files and then passing them off to vsftpd as though its me? i just want to clarify...

i added the home folder encryption in for the added privacy... and am a little confused that i could still get into the files through vsftpd ... thanks  for advice in advance

---

