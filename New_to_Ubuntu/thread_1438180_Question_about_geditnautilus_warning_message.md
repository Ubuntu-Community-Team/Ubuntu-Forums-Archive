---
title: "Question about gedit/nautilus warning message"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by oingk on 2010-03-24
Hi!

I'm making my website and I'm using the inbuilt FTP thing on my Ubuntu (Karmic koala). I guess I'm using Nautilus, not sure. Basically I connect to it via "Places" > "Connect to Server...".

This method is quite easy. However there is sometimes something that bugs me. Sometimes when I edit a website file in gedit Text Editor, and then I click on "save", it shows me this message:

> [SIZE=3]
The file sftp://mywebsitefile.html has been modified by another process since reading it.[/SIZE]

If you save it, all the external changes could be lost. Save it anyway?I always click on "Save anyway" and it seems to save it normally without any problem. However I wanted to ask you guys if you know what this is, as it comes up very ofter (about once every two times I save a file).

---

### Post by doas777 on 2010-03-24
well that is a classic "concurrency" issue. you were altering somthing, and at the same time you had it open, someone or some process altered it and committed their changes before you did. 

usually the problem isn't on your client box, but on your server. usually site pages don't change unless some one makes them, so I'm curious about your usecase. does anyone else have access to the ftp server? I don;t work regularly with linux based web servers so it is possible or even likely that it is a side effect of the server process itself.

also just fyi, sftp is a rather differant protocol than ftp. it's part of the ssh suite and uses ssh tunnels and authentication. it may be useful to keep that in mind while troubleshooting this issue. 

hth

---

### Post by r-senior on 2010-03-24
I wonder if it's a time sync issue? Synchronising your clock using a time server (in Time & Date) might help?

---

### Post by oingk on 2010-03-24
Yes, actually I'm using the SFTP thingy and not the FTP. I connect by giving it my SSH server.

Noone else has my password, as far as I know. My website seems to normally only contain the content that I made it to contain (so I guess noone is altering it, as far as I know).

Regarding my time&date, I have it normally synchronized to the time zone I live in.

When you say it might be my server, what is my "server" here exactly? My linux system, or my web hoster?

Also, is it safe to connect to my website via this method? I hope it is as I find it really convenient.

---

### Post by doas777 on 2010-03-24
by server, I mean the box that physically stores your file. so i guess that would be your webhosts. sometimes hosts add content to hosted sites, but i would not have guessed that they would do it by modifying your sources themselves.

anyway, the great thing about  a concurrency bug, is that if you don;t care what happens to another operators changes (and as the only operator, you don't) then you can just ignore it and save over.

sftp is one of the safer means for remote file access, so yes by all means, enjoy. there are security considerations when you are hosting an ssh/sftp server accessible to the internet, but since you aren't stuck hosting it, you have to hope that the isp knows how to secure it.

---

### Post by oingk on 2010-03-25
Got it, thanks very much.

---

