---
title: "Permission error on DVD playback"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2009-06-02
I have mplayer and movie player with ubuntu-restricted-extras installed and I still cannot get DVD playback. I get an error that says I may not have permission. I have never seen that type of error before. I never had DVD playback problems before. Anyone have any idea what to do about it. I followed the trouble shooting section for DVD playback in the MultiMedia how to guide here and I'm still getting no love.

---

### Post by bcrowell on 2009-06-02
How about some more info on what you were doing when you got the error, and the text of the actual error message.

---

### Post by Bigtime_Scrub on 2009-06-02
> **bcrowell said:**
> How about some more info on what you were doing when you got the error, and the text of the actual error message.

That is all the actual error message said. 

However, I ran this in terminal and I got back this. 

```
gary@gary-laptop:~$ sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 vlcReading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
gary@gary-laptop:~$ 


```

So maybe an issue with libdvdcss2?

---

### Post by jonobr on 2009-06-02
Hello


Did you check the restricted extras guide
it includes info for 9.04

It says use this

> sudo apt-get install ubuntu-restricted-extras

[Here is the link]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by eeeandrew on 2009-06-02
Is the medibuntu repository set up correctly?

Visit the community documentation at 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
for a guide on how to do this.

Hope this helps,
Andrew

---

### Post by Bigtime_Scrub on 2009-06-02
The medibuntu repository is ok and ran the install for ubuntu-restrited-extras again and nothing. It says nothing new to install because everything is already installed. Just to check I tried a different dvd and nothing either.

I also tried loading it with DVDrip to see what would happen and when I click load it says "Can't read DVD track. Faulty disk?"

It says this about all my DVDs though.

---

### Post by Bigtime_Scrub on 2009-06-02
I figured it out.

I ran this command then I restarted my computer.

```
gary@gary-laptop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh


```

I feel so stupid. O well it works now. Thank you all for your help.

---

### Post by jonobr on 2009-06-02
rock and roll baby

rock and roll

:guitar:

---

