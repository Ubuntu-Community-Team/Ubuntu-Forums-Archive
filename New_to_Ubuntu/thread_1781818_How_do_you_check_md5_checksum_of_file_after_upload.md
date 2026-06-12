---
title: "How do you check md5 checksum of file after upload to ftp?"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by seventhsamurai on 2011-06-14
Hi Guys

I've been uploading a lot of fairly large files to a remote ftp server using Filezilla or Fireftp. Quite a few times now, mostly due to a not-so-good internet connection, the files get corrupted during upload as get stopped often and then resume.

I was wondering if there is any way for me to check the md5 checksum of a file off the ftp after I have finished uploading it, to compare it with the md5 of my local file to verify that there was no corruption in upload.

Is there any software that can do that?

I'd appreciate your help.

Thanks.

---

### Post by doctorbighands on 2011-06-14
Can you SSH into the remote server? If so, you could just md5 in the usual way.

If not, then I'm not sure. Also, there may be issues comparing your remote file (assuming it's intact) to the local version because of transferring via ASCII mode. See the comments in this thread for some insight into that, and into what you're trying to do in general:

[http://www.perlmonks.org/?node_id=548567](http://www.perlmonks.org/?node_id=548567)

---

