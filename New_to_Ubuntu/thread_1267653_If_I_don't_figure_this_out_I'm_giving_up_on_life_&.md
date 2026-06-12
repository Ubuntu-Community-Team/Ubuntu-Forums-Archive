---
title: "If I don't figure this out I'm giving up on life &gt;:O!!!"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Jmcsorley on 2009-09-16
I'm new to Ubuntu and this whole forums thing (but not to computers)... I'm having a lot of trouble on my acer one after deleting the windows partition and Installing Ubuntu netbook remix for the 2nd time >:O... My 1st problem showed up after I attempted to update. (it went slow/top bar was non existent/ect..) so i re-downloaded the netbook remix and reinstalled again.. This time I had no problems till today -_-. I tried to install the flashplugin but it seems every-time i try it sais that the update-manager,package installer,and one more thing... might be open and that i should close it (because only one can run at a time) So im look and notice that the update manager open right when i tryied to install the flashplugin... and close it and try again... same error happened.. next o turn off the computer and turn it back on and try again... something happen again... I try several things all fail and now I want to know wtf is going on?  Why does it say that i have another program running that is stopping me from installing any packages?

 BTW!!! my download speed for the package manager/ updater starts off fast but then drops ridiculously low -_- how can i fix this? (starting 10-20kb+... after about 2 seconds it goes to 2000b/s)... i can't download anything! but videos (and not even that because i can't put flash on!!!) >:O Please help before throw this thing off a building!

---

### Post by Jmcsorley on 2009-09-16
This is what showed up when i directly open the package manager...
[IMG]http://i119.photobucket.com/albums/o126/killerwing55/Screenshot.png?t=1253077215[/IMG]

---

### Post by lisati on 2009-09-16
From the command prompt/terminal, type in ```
sudo dpkg --configure -a
```
It will ask you for your password, which won't show as a security precaution.

---

### Post by mgranet on 2009-09-16
Do what it says:

Open a terminal, and type in (or copy/paste) ```
sudo dpkg --configure -a
```

---

### Post by ankspo71 on 2009-09-16
go open your terminal and type in:

```
sudo dpkg --configure -a 
```

This will try to correct the problem for you.

Also, 
go to "system">"administration">"software sources"
and change the "download from" location. You can have it automatically find the best server for you from there.

James

---

### Post by QIII on 2009-09-16
Sometimes we who are in the software industry forget ... and we write cryptic error messages expecting everyone else to know exactly what we mean.

"Manually run..." means "Open the terminal and type..."
 
 Welcome to Ubuntu.

You've found the right place for a beginner (and the old hand).

We don't bite (much) and, as you can see from the answers above, there are always friendly people willing to help.

Of course, we also have been doing this so long that WE forget we are expecting you to know what the heck we are talking about.  So if you don't understand, ask us to explain clearly...

---

### Post by Jmcsorley on 2009-09-16
Thank you all it seems to be working now... The 1st time I tried I must have typed in the command wrong because the terminal told me it did not exist. 
As for my download problem does anyone have a solution for that?

---

### Post by LewRockwell on 2009-09-16
> **Jmcsorley said:**
> Thank you all it seems to be working now... The 1st time I tried I must have typed in the command wrong because the terminal told me it did not exist. 
As for my download problem does anyone have a solution for that?

download transfer rates vary with specifics such as:

time of day

LAN load

WAN load

OS load

ISP transfer-rate throttling

Server throttling

not to mention poor and/or compromised software and firmware

stuff like that

.

---

### Post by QIII on 2009-09-16
... neighbor on your cable node watching streaming porn videos all day ...

---

