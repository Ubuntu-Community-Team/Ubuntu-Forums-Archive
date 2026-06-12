---
title: "Accessing data stored by windows"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by theskipirate on 2010-10-08
Hi,

Slowly making the transition to ubuntu but I have a small problem. I have installed ubuntu through wubi so I have only the one partition of my hard drive. How can I access data stored by windows (more importantly My Documents) and will any changes made by ubuntu be applied when booting from windows? My partner also uses this laptop but uses windows, it would be great if anything edited by myself would be changed in windows also.

Apologies if this has been addressed before, I wasn't able to find the solution!

---

### Post by Elfy on 2010-10-08
Your windows drive is accessible in /host - look in Nautilus - File System

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by theskipirate on 2010-10-08
Oh, should of said, I already came across that but "Documents and Settings" is highlighted in red and won't let me access it...

Thanks for the quick reply

---

### Post by lbrty on 2010-10-08
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

How do I access the Windows drives?

The Windows partition where you installed Wubi is available as /host within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media 

Yes, all the changes made from Ubuntu will reflect in Windows as you are working with the source file(s). If you want an performance boost, I would recommend dual booting instead of working with Ubuntu inside of Windows.

---

### Post by Elfy on 2010-10-08
> **theskipirate said:**
> Oh, should of said, I already came across that but "Documents and Settings" is highlighted in red and won't let me access it...

Thanks for the quick reply

Yes - you should have - I'd not have answered and lost the unanswered status. 

I'd not even be able to hazard a guess at why it is in red I'm afraid.

---

### Post by theskipirate on 2010-10-08
Thanks. I have found 'documents' from that but there is a big cross and padlock next to this and the GUI says the link is broken...

Any ideas?

Thanks again!

---

### Post by lbrty on 2010-10-08
@forestpiskie,

I have not seen or heard of this issue using WUBI either. Do you think it would be safe for *theskipirate *to use the following command? This would enable the user to view any folder as root/super user. I use this command in an installation of Ubuntu not WUBI. 

```
gksudo nautilus
```

---

### Post by Elfy on 2010-10-08
> **lbrty said:**
> @forestpiskie,

I have not seen or heard of this issue using WUBI either. Do you think it would be safe for *theskipirate *to use the following command? This would enable the user to view any folder as root/super user. I use this command in an installation of Ubuntu not WUBI. 

```
gksudo nautilus
```

I'm not sure I would want to be accessing windows files like that - but then to be honest I would not want to use wubi for more than a quick look to see if I wanted to install ubuntu properly.

Maybe the windows was not shut down properly.

---

### Post by bcbc on 2010-10-08
I don't have a problem writing to my files under /host using Windows XP.

What do the permissions look like if you do ```
ls -l /host
```Mine looks like this:
> drwxrwxrwx 1 root root       4096 2010-10-01 20:45 Documents and Settings

---

### Post by theskipirate on 2010-10-09
Had a look at the permissions. Mine look like:

```

lrwxrwxrwx 2 root root         60 2009-07-14 06:08 Documents and Settings -> /root/Users

```

I know wubi is only to see if you want to make the full conversion, I just want to see that I could get everything working before making the change

---

### Post by Mark Phelps on 2010-10-09
I'm guessing that you're running Win7 instead of XP, and Win7 uses much stronger security by default. There is no longer a Documents and Settings folder in Win7 for good reason -- it was a security risk.

Win7, by default, will not allow OTHER users to mess with YOUR user files, and when you're accessing those files from Linux, you're an OTHER user.

It's NOT a good idea to mess with private Win7 User Directory files using Linux.  I would advise against hacking around trying to figure out how to bypass Win7 file security.

---

### Post by theskipirate on 2010-10-09
Yes, it is widows 7. Alright thanks a lot for that, guess its not possible (or at least worth not worth the hassle) for win7.

Cheers

---

