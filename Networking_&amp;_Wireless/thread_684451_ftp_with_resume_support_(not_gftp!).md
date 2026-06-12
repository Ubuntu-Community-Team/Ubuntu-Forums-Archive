---
title: "ftp with resume support (not gftp!)"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by protenniser on 2008-02-01
Hi all,

I need an ftp program that has the resume option working flawless (I am uploading big files in general).
Up to now I could find only 3:
gftp: crashes to often and unexpectedly, although resume works without problem, I am bored with this.
crossftp: I think there are some problems with this program, I uploaded a file with size 400 mb. and it was uploading still when the file on the server was more than 500 mb. and there is also problem with the resume part.
Filezilla: a good program but although the server supports resume, resume in the filezilla doesn't work!

So, please help/suggest me programs that have good resume support or a way to make gftp more stable or make resume work in filezilla.

Thanks, regards...

---

### Post by kpkeerthi on 2008-02-01
You can try [FireFTP]("https://addons.mozilla.org/en-US/firefox/addon/684"). Not sure if it supports resume but give it a try. 

It can also be run [standalone]("http://ayozone.org/2007/12/13/fireftp-stand-alone/").

---

### Post by protenniser on 2008-02-01
Hi, 

Thanks for the suggesiton, fireFTp does support resume, however it has too some problems, for example it read the size of the uploaded files wrong from the server when I tried to use it.
Still only one that works is gftp. :(

---

### Post by patryk77 on 2008-02-01
Works fine for me in Filezilla. Did you enable the Resume options?

Edit/ Settings / Transfers / File Exists Action... Set it to resume...

Allow resume of ASCII files is optional... It might be better to keep it of, although generally ASCII files will be short enough that you do not need it.

---

### Post by protenniser on 2008-02-01
Hi,

Thanks for trying to help but I do tried to activate resume option in filezilla, however for some reason although it does resume, the file becomes bigger than the normal size of the real file after the upload process is finished on the server. So my upload becomes meaningless (wrong.) So it doesn't work for me. 

Regards..

---

### Post by Bachstelze on 2008-02-01
Not only the client but also the server has to support resume for it to work. I personnally use Konqueror for FTP transfers but I guess it won't suit you, since you seem to be using Gnome...

---

### Post by protenniser on 2008-02-01
Hi,

Yes I do use gnome...
And I know that both sides must support resume in order it to&#305; work. However since it is working with gftp (and I am pretty sure that server I am using also supports it.) I think this is not the problem.

Regards...

---

### Post by patryk77 on 2008-02-01
could this be because you are transferring the files in ASCII mode?

Can you copy/paste the FTP session from a session in which you try to resume and end up with a larger file?

Also, do you know which FTP server is used?

---

### Post by protenniser on 2008-02-01
Hi,

I will try to answer your questions as much as I undestand.
1- No I am transferring in binary mode.
2- Yes, I sometimes (not with gftp but with other programs) end up with bigger files than the real file.
3- I am not totally sure that I understand the question but I am using the netload's upload ftp server to upload some data I have. If it works, its link is upload.netload.in

Thanks...

---

### Post by patryk77 on 2008-02-04
```
$ ftp upload.netload.in
Connected to upload.netload.in.
220 (vsFTPd 2.0.5)
```

so the server is running vsFTPd 2.0.5.

[http://gftp.seul.org/gftp-screenshot.png](http://gftp.seul.org/gftp-screenshot.png)

If you look at this picture, there is a section at the bottom of the window where everything is logged.
Starts with "227 entering passive mode" and ends with "150 Opening BINARY.....48 bytes)."

Usually, all the clients have something similar.

In FileZilla it's at the top. Now if you upload a file, and resume the upload, you should see something like APPE (for Append) in there. Copy / paste that section here inside the CODE tags, and I will take a look at it.

---

### Post by protenniser on 2008-02-04
Hi,

I could get the output from gftp (yes, unfortunately it made the similar thing too :( ). The original file I was uploading was 350.000.000 byes and after gftp told me that it is done it was 456.000.000 bytes on the server.
If this is not enogh, I'll try to get from filezilla log too.
Log is attached.
Thanks for your help, regards...

---

### Post by patryk77 on 2008-02-05
Hmmmm.... is it possible you are using more than one connection at a time?

For some reason there is confusion when it resumes the upload using the REST command.

Here you can see it resume at 76 megabytes, 316 megs and then 240 megs. Not sure what could cause that though.

If you are using multiple connections, limit them to one at a time... 

```
PASV

227 Entering Passive Mode (85,131,244,109,128,68)
REST 76451840

350 Restart position accepted (76451840).
STOR /abc.part1.rar


(...)

PASV

227 Entering Passive Mode (85,131,244,109,58,66)
REST 316846080

350 Restart position accepted (316846080).
STOR /abc.part1.rar

Connection to upload.netload.in timed out
Disconnecting from site upload.netload.in
Error: Remote site disconnected after trying to transfer file

(...)

PASV

227 Entering Passive Mode (85,131,244,109,89,91)
REST 240394240

350 Restart position accepted (240394240).
STOR /abc.part1.rar
```

---

### Post by protenniser on 2008-02-05
Hi,

I didn't even know that it was possible :) So I don't know weather I am making multiple connections of not, where can I check/change it?

---

### Post by patryk77 on 2008-02-05
I dunno about gFTP but in FileZilla it's in Edit/Settings... Transfers, then you have options for concurrent transfers.

---

### Post by protenniser on 2008-02-05
Oh okay, if that is what you mean, it was already 1 in filezilla's settings, however there was still transfer error. (extra mbs.)

---

### Post by morningboat on 2008-02-05
It seems that your server has some problem in the resume portion: In your log, second time's resume point "REST 316846080" is bigger than the third time's resume point "REST 240394240", which means the after the second time's transfer, the file becomes smaller?!

Probably the server displays a wrong file size after the resume, which causes all the other ftp clients failed to resume. gFTP works probably because it is not so good a client that it does not parse the server's command, hence avoids the server's mistake.

---

### Post by protenniser on 2008-02-06
For the first time, a worse program is working better in my life :)
Thanks for explanation, and since this is related with the server, I think there is nothing I can do, am I right?

Regards...

---

### Post by patryk77 on 2008-02-06
Yeah... you can try contacting Netload and let them know about the issue...

Sending them the file as an attachment may help too.

---

### Post by protenniser on 2008-02-06
Thanks all that helped....

Regards...

---

### Post by protenniser on 2008-02-10
Hi all,

Since I am uploading from a diferent internet and gftp doesn't work here very well. I have tried to upload with filezilla again and here is the log for resuming an upload (trying to)

Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (85,131,244,109,237,105)
Command:	APPE abc.part2.rar
Response:	550 Permission denied.
Error:	Critical error
Status:	Disconnected from server

I think it is a permission problem, anybody that can point out how to solve this, I'll be very glad, thanks...

---

