---
title: "Synaptic Package Manager error"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by boldhoof on 2011-01-30
Hi All,

I was installing WINE to use Picasa, the terminal window stuck when it tried to get and install msttcorefonts it just sat at OK, then timed out and tried again but failed. WINE and Picasa work fine, but when I tried to open the Package Manager I get this error message: ```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
``` Also if I try and install anything from the software centre it just seems to sit there not installing. Any help greatly appreciated.

---

### Post by matt_symes on 2011-01-30
Hi

Open a terminal(Applications->Accessories->Terminal) and type

```
sudo dpkg --configure -a
```

and enter your password. You will not see it echoed to the screen. This is normal.

Kind regards

---

### Post by TeoBigusGeekus on 2011-01-30
Open terminal and, guess what, run
```
sudo dpkg --configure -a
```

---

### Post by boldhoof on 2011-01-30
Thanks for the replies. This is whats happening now:

> Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

     0K .......... .......... .......... .......... .......... 25%  200  12m16s
    50K .......... .......... .......... .......... .......... 51% 19.4K 4m2s
   100K .......... .......... .......... .......... .......... 77% 32.9K 76s
   150K .......... .......... .......... .......... ...       100% 18.8K=4m22s

2011-01-30 21:33:45 (756 B/s) - `./andale32.exe' saved [198384/198384]

Now moved onto /arialb32.exe ,seems very very slow.

---

### Post by TeoBigusGeekus on 2011-01-30
Never mind that; it will finish eventually.

---

### Post by boldhoof on 2011-01-30
> **TeoBigusGeekus said:**
> Never mind that; it will finish eventually.

I am getting > Read error at byte 4218/168176 (Connection timed out). Giving up. on the ./arialb32.exe

---

### Post by TeoBigusGeekus on 2011-01-30
It seems your connection is a bit impaired. 
Do you have anything else open - browser, torrents, skype, etc.?
If so, turn them off and try again.
If not, try again at a different time or simply change your server from Software Sources.

---

### Post by boldhoof on 2011-01-30
> **TeoBigusGeekus said:**
> 
If not, try again at a different time or simply change your server from Software Sources.

How/where do I do that, I will try in the morning, see how it goes.

Thanks

---

### Post by TeoBigusGeekus on 2011-01-30
I believe it is in System>Admin>Software Sources
Find a better server and try again later.

---

### Post by boldhoof on 2011-01-31
Okay tried again, and it will still not install the fonts, it just sticks at downloading the.exe files. I can download via ftp, through the web browser no problem. Is there a way of installing the required fonts manually, I have managed to get them onto a usb stick via a winxp machine from soundforge site.

---

### Post by matt_symes on 2011-01-31
Hi

What is the full name of the file to install ?

Kind regards

---

### Post by boldhoof on 2011-01-31
> **matt_symes said:**
> Hi

What is the full name of the file to install ?

Kind regards

It was the MS fonts from soundforge site, that was the issue in downloading. So this time I left it running 2 hours later it managed to get them and all seems fine now. Think the soundforge site is just so busy, it seems like nothing is happening, but it worked in the end.

---

