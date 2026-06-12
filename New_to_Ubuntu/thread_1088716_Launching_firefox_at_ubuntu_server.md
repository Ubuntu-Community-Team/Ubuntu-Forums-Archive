---
title: "Launching firefox at ubuntu server"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by shahab.fm on 2009-03-06
Hi.

I just installed latest version of Ubuntu server and when I try to open firefox I get this error : 

Error: no display specified

Can any one help me with this ?

P.S. I have XTERM installed but it still doesnt help ...

---

### Post by kanikilu on 2009-03-06
Are you trying this on the server console itself, or are you doing this via SSH from another computer?

If the former, that's not going to work, you need an X server to display GUI programs like Firefox. If from another computer with X, try:

```
ssh -X username@hostname
```

And then try

```
firefox &
```

---

### Post by taurus on 2009-03-06
The server version is command line only.  If you want to run those GUI apps, you need to install X server and some kind of window manager first.  

Do you really want the server version instead of the desktop?

---

### Post by shahab.fm on 2009-03-06
> **taurus said:**
> The server version is command line only.  If you want to run those GUI apps, you need to install X server and some kind of window manager first.  

Do you really want the server version instead of the desktop?

Hi.

Yeah, I am trying to learn text based Linux for the job so I prefer the text version to MAKE myself learn and remember to work with text based unix & linux ... 

now i am installing ubuntu-desktop on the server so I have a visual desktop as well ...

---

### Post by kellemes on 2009-03-06
> **taurus said:**
> The server version is command line only.  If you want to run those GUI apps, you need to install X server and some kind of window manager first.  

Indeed.. or install a text-based browser like [links]("http://links.sourceforge.net/") (one of many).
```
sudo apt-get install links
```
should do it..

---

### Post by kanikilu on 2009-03-06
If you're already installing ubuntu-desktop, that'll work. There's plenty you can (and sometimes need to) do on the CLI even with X, but browsing the web is not one that's particularly fun doing that way - although it's certainly possible (w3m, lynx, elinks...).

---

### Post by kellemes on 2009-03-06
> **shahab.fm said:**
> Hi.

Yeah, I am trying to learn text based Linux for the job so I prefer the text version to MAKE myself learn and remember to work with text based unix & linux ... 
Great choice!

> now i am installing ubuntu-desktop on the server so I have a visual desktop as well ...
Bad choice.. ;-)

---

### Post by MockY on 2009-03-06
like some already mentioned, Elinks is a great option
```
sudo apt-get install elinks
```

---

