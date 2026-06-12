---
title: "FTP (to XBOX) problems from a network beginner"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by tabithaboof on 2008-06-23
I have a modded XBOX which I want to use as a media center and I have a few questions.

1 - I am using Filezilla which I have used for a long time to FTP to my website with no problem but I have lots of errors while trying to FTP files to the XBOX. First is when trying to transfer a file from my USB HD

```
Status:	Starting upload of /media/disk/video/Documentaries/Tesla - Master of Lightning PBS-VHS Great Quality(DivX).avi
Status:	Retrieving directory listing...
Command:	PORT 192,168,3,2,206,156
Response:	200 Port command ok. 
Command:	LIST
Response:	150 Opening ASCII data connection for ls /F/Movies/.
Response:	226 free disk space under this directory : 42.466.017.280
Command:	PORT 192,168,3,2,195,134
Response:	200 Port command ok. 
Command:	STOR Tesla - Master of Lightning PBS-VHS Great Quality(DivX).avi
Response:	426 Connection closed , file opening failed.
Status:	Starting upload of /media/disk/video/Documentaries/Tesla - Master of Lightning PBS-VHS Great Quality(DivX).avi
Status:	Retrieving directory listing...
Command:	PORT 192,168,3,2,155,210
Response:	200 Port command ok. 
Command:	LIST
Response:	150 Opening ASCII data connection for ls /F/Movies/.
Response:	226 free disk space under this directory : 42.466.017.280
Command:	PORT 192,168,3,2,173,50
Response:	200 Port command ok. 
Command:	STOR Tesla - Master of Lightning PBS-VHS Great Quality(DivX).avi
Response:	426 Connection closed , file opening failed.
Status:	Starting upload of /media/disk/video/Documentaries/Tesla - Master of Lightning PBS-VHS Great Quality(DivX).avi
Status:	Retrieving directory listing...
Command:	PORT 192,168,3,2,152,12
Response:	200 Port command ok. 
Command:	LIST
Response:	150 Opening ASCII data connection for ls /F/Movies/.
Response:	226 free disk space under this directory : 42.466.017.280
Command:	PORT 192,168,3,2,180,107
Response:	200 Port command ok. 
Command:	STOR Tesla - Master of Lightning PBS-VHS Great Quality(DivX).avi
Response:	426 Connection closed , file opening failed.
```

The same file will transfer just fine if I move it to me PC from the USB drive and THEN FTP it. I am not sure why.

Second problem is, there are a couple of files on the XBOX HD which I cant delete. I get this reponse

```
Command:	DELE Matt Foley - Halloween.mpeg
Response:	553 Requested action not taken.
```

And lastly, whenever I try to transfer a directory with a number of files in it. The transfer sometimes works for a few seconds then crashes with an error which I THINK is

```
421- too many users
```

Any help much appreciated

---

### Post by nixscripter on 2008-06-26
1. General suggestion: try using passive mode in FTP. This solves some percentage of connection problems.

2. According to the FTP procol spec (at least one of them), the error code means: **Requested action not taken: file name not allowed**. Perhaps there a special character (like dash or space?) that FTP doesn't like in the filename.

3. The second error code, 421, is rather broad. According to the spec: **421 Service not available, closing control connection. This may be a reply to any command if the service knows it must shut down.** I suspect "too many users" -- assuming you haven't been leaving other processes still connected -- is just a default error message on the software's part.

Hope this helps.

---

