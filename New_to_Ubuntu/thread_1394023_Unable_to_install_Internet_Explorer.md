---
title: "Unable to install Internet Explorer"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by MarvinBasa on 2010-01-30
Guys,

I read a lot of threads to help with my problem in IE but unable to install. I need this because our online training course was unable to run in Firefox because of dependency. 

Actions taken but failed:
1. Installed Wine and IEs 4 Linux but it says that my Wine is outdated. Tried to update but encountering problem.
2. Install PlayonLinux but encountered problem:
"Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 1B in 2s (0B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Using these commands:
**With Jaunty repository**

 Type the following commands :
 sudo wget [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

Please need help ASAP. ]

Thanks,
Marvin

---

### Post by 3rdalbum on 2010-01-30
> **MarvinBasa said:**
> Guys,

I read a lot of threads to help with my problem in IE but unable to install. I need this because our online training course was unable to run in Firefox because of dependency. 

Actions taken but failed:
1. Installed Wine and IEs 4 Linux but it says that my Wine is outdated. Tried to update but encountering problem.
2. Install PlayonLinux but encountered problem:
"Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 1B in 2s (0B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

You can only run one package manager at a time. When they have completed their work, close all other package managers and try again.

---

### Post by MarvinBasa on 2010-01-30
Thanks for your response.

I just restarted my PC and able to install PlayonLinux and IE7. However, another problem occurred. I am still not able to browse our company's site with https: because the cipher strength of IE7 is set to O. I am still unable to access our training course online because page cannot be displayed. Please need help ASAP.

Thanks

---

### Post by MarvinBasa on 2010-01-30
This has been resolved by downgrading to IE6. Thanks anyway

---

### Post by canadiandude007 on 2010-03-08
I'm having issues installing IE7 using PlayOnLinux as well using Karmic.  I'll let you know if I can figure it out.

Perhaps a combination of Wine + PlayOnLinux ... will see ...

---

### Post by executorvs on 2010-03-09
I'm trying to get the dreaded MLXchange website to run so I can change my parent's over to ubuntu. I found a couple interesting comments online about using activex in linux. I'll be looking into it more this weekend. This is to date the only thing I haven't been able to get working in linux and I would like to have it behind me soon.

---

### Post by Pascal11110 on 2010-03-09
Have you tried the IE tabs add on for firefox? I had to use this because Netflix does not work natively in firefox, but it worked great after I used this. You might want to try it to see if it can save you some trouble.

(I also use this in my windows Firefox so that I can get my windows updates with firefox, therefore my last need of internet explorer is gone)

---

### Post by executorvs on 2010-03-09
IE tabs uses the windows install of IE and simply ports it through firefox. Unfortunately that makes it little help in linux.

---

### Post by Pascal11110 on 2010-03-10
Oh, sorry, I didn't realize that was how IE tabs worked. I figured they created an IE environment in Firefox but I guess I was wrong. Thanks for pointing that out.

---

