---
title: "Make Ubuntu Laptop Temporary File Server"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by flugelhornchris on 2010-07-27
Hi all!

First off after using this forum many times to solve my computer issues, I decided to go ahead and register. Feels good. I'm not exactly a beginner, but I'd still appreciate help.

Second, I love taking photos, lots of them, and so do my family members. My camera is the only one that is really working and I don't have the USB cord for it, and my laptop is the only one that has an SD Card port. So all the photos end up on my laptop, even though my family members want them on their respective computers. So heres my question: how can I set up my laptop to be a temporary server (only for the times when photos need to be transferred) so the other computers on my network can access the photos and take them off my harddrive? I've seen it done before, my friend use to let me download anime off his server a while back ago, and the only thing I had to do was SSH in with my unique username and password (if I was in Windows I would simply use Cygwin).

Oh, just for background, my laptop runs Ubuntu 10.04 while all the others run either MS Windows XP, Vista, or 7. I'd go buy some thumb drives, external harddrives, adapters, or whatever but I can't, so no suggestions of that sort please.

Thanks!

---

### Post by stlsaint on 2010-07-27
Do just what your friend was doing by using ssh is my suggestion. Or setup samba to share out folders throught your house. With ssh you can use putty for windows and samba works with windows/linux!
See here for [openssh]("http://https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html") client.
See here for [samba]("http://https://help.ubuntu.com/community/SettingUpSamba").

---

