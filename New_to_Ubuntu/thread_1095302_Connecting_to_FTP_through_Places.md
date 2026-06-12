---
title: "Connecting to FTP through Places"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by exar.jun on 2009-03-13
I am trying to connect with my domain host ftp.  It is ftp.fatcow.com.  I keep getting "invalid reply" with I go thru places>connect to server...I am able to connect to the server via console and thru firefox.

Help appreciated.

---

### Post by viljun on 2009-03-13
Have you tried this:

Places > 
Connect to server > 
Ftp-with login > 
Write down your info (ftp port is 21 - try also 20 if this won't work) >
Connect

---

### Post by exar.jun on 2009-03-13
Yes I tried your suggestions.

Using intrepid 64bit

FTP with login

server:ftp.fatcow.com
port:21
folder:/
user:myname

No go....still saying invalid reply

---

### Post by exar.jun on 2009-03-14
bump...i tried it from the live intrepid 386 cd and it gave same error.

Should I install hardy instead?

---

### Post by blueridgedog on 2009-03-14
> **exar.jun said:**
> Yes I tried your suggestions.

Using intrepid 64bit

FTP with login

server:ftp.fatcow.com
port:21
folder:/
user:myname

No go....still saying invalid reply

I assume this works from the terminal...just to verify your credentials.

Just enter

```
ftp ftp.fatcow.com
```

---

### Post by exar.jun on 2009-03-15
Yes...I am able to connect thru the console and thru gftp.  Just not when I try to mount a connection thru places.

---

### Post by exar.jun on 2009-03-17
Any thoughts on what forums section here would be best suited in answering this question.  I have tried setting up a few ftp connections besided ftp.fatcow.com.  If anyone has luck connecting to that server I would appreciate advisement.

Thanks.

---

### Post by PukingPenguin on 2009-03-17
> **exar.jun said:**
> Any thoughts on what forums section here would be best suited in answering this question.  I have tried setting up a few ftp connections besided ftp.fatcow.com.  If anyone has luck connecting to that server I would appreciate advisement.

Thanks.

I'd suggest networking and/or servers. wish I could help, but I don't primarily use Gnome...

---

### Post by pointyblufish on 2009-03-17
Not sure if this would help or not, but it's quick to try. Leave the folder field blank instead of putting / there. It might be that the server wants to redirect you and your settings conflict with that?

---

### Post by Botbob89 on 2009-03-17
Just to get more information...how are you connecting to the internet? Directly? Network? Through a proxy? All of those can make a difference....

---

### Post by exar.jun on 2009-03-18
Connecting to the internet directly.  I am beginning to think that it is on fatcow.com and not ubuntu.  I was able to mount a server through places on a public server.

And pointy...thanks for the idea however, I have tried leaving all fields blank in multiple different variations. 

I believe the issue is that fatcow uses active FTP and not passive mode or vice versa.   Nautilus only uses one of the modes unfortunately.  Hopefully Jaunty will allow for selection of passive or active mode when setting up a connection to ftp.

---

