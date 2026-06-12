---
title: "How can i prevent someone to opening (Some) sites on pc?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by adeee on 2011-06-09
Well i try to make filter through
system->Preferences->Network proxy. In general tab i just wrote (testing purpose) Facebook.com and close and restart pc.
but facebook. still open.
i try another
through hosts file.
sudo nano /etc/hosts

and make this line
127.0.0.1    facebook.com
save close and restart.
And still facebook open.

can make any mistake?
how can do it in ubuntu10.10?:popcorn:

---

### Post by ubudog on 2011-06-09
Hi there!  If you are using Firefox, I recommend the BlockSite add-on.  It has password protection and everything, and it's pretty straightforward.

Here is some more info about it: [https://addons.mozilla.org/en-US/firefox/addon/blocksite/?src=api](https://addons.mozilla.org/en-US/firefox/addon/blocksite/?src=api)

Let me know if it works for you!  :-)

EDIT: Also, in some router configs, you can block certain cites.  To edit your router config, normally go to 192.168.1.1 in a web browser.  This address differs with router.

---

### Post by wolfen69 on 2011-06-09
Dansguardian is another way.

---

### Post by mike555 on 2011-06-09
After putting in the hosts file ,did you clear the browser cache ? log out and back in ?

---

### Post by collisionystm on 2011-06-09
> **adeee said:**
> Well i try to make filter through
system->Preferences->Network proxy. In general tab i just wrote (testing purpose) Facebook.com and close and restart pc.
but facebook. still open.
i try another
through hosts file.
sudo nano /etc/hosts

and make this line
127.0.0.1    facebook.com
save close and restart.
And still facebook open.

can make any mistake?
how can do it in ubuntu10.10?:popcorn:

make it like this and try

127.0.0.1   [www.facebook.com](www.facebook.com)
127.0.0.1   facebook.com

---

### Post by FormatSeize on 2011-06-09
> **ubudog said:**
> 
Here is some more info about it: [https://addons.mozilla.org/en-US/firefox/addon/blocksite/?src=api](https://addons.mozilla.org/en-US/firefox/addon/blocksite/?src=api)
 
Let me know if it works for you! :-)

Thank you for this. I will be doing this today. Now, when people come over and immediately log on to Facebook, it won't work, and they will throw up their hands and assume that the internet had died.

---

### Post by ubudog on 2011-06-09
> **FormatSeize said:**
> Thank you for this. I will be doing this today. Now, when people come over and immediately log on to Facebook, it won't work, and they will throw up their hands and assume that the internet had died.

Lol!

---

### Post by TeoBigusGeekus on 2011-06-09
If you're using Opera, there's the urlfilter.ini file in the .opera folder.

---

### Post by wep940 on 2011-06-09
> **FormatSeize said:**
> Thank you for this. I will be doing this today. Now, when people come over and immediately log on to Facebook, it won't work, and they will throw up their hands and assume that the internet had died.
 
 
I *love* it!!  ;)

---

### Post by adeee on 2011-06-10
> **collisionystm said:**
> make it like this and try

127.0.0.1   [www.facebook.com]("http://www.facebook.com")
127.0.0.1   facebook.com


ooppsss nothing happen. facebook still open.
no idea whats just wrong?

---

### Post by collisionystm on 2011-06-10
> **adeee said:**
> ooppsss nothing happen. facebook still open.
no idea whats just wrong?


Are you making sure to seperate it with a tab?

You can't put a space between 127.0.0.1 and facebook

It needs to be

127.0.0.1 TAB facebook.com

---

### Post by adeee on 2011-06-10
> **collisionystm said:**
> Are you making sure to seperate it with a tab?

You can't put a space between 127.0.0.1 and facebook

It needs to be

127.0.0.1 TAB facebook.com


work it man. tab solve problem.Thanxs
:popcorn::KS

---

