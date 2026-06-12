---
title: "how to fix apt-get check"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by seandude on 2009-09-05
Ok, so, I know how to check for broken dependencies (apt-get check) but I dont know how to fix those broken dependancies.

When I run
  
[FONT=Courier New]sudo apt-get check[/FONT] -v

I get

[FONT=Courier New]apt 0.7.20.2ubuntu6 for amd64 compiled on Apr 17 2009 04:25:25
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file[/FONT]

What does this mean?  How do I fix it?

---

### Post by powel212 on 2009-09-06
Open Synaptic 

go to the "edit" roll down menu

select "fix broken packages"

Then hit Apply and close Synaptic.

Go to "software updates" and hit check.

Should be okay now.

I hope that helps

Powel

---

### Post by powel212 on 2009-09-06
Sometimes when you do this you may get an error saying something like you have unconfigured updates and you must run "sudo bla bla bla..." to fix the problem

If you get a message like this just open a terminal and run the command that is stated in the error message. then you should be good.

I have also occasionally encountered a problem when the Miror I am using is out of date. If you have done all of the above and still have errors try changing your mirror to the main US mirror. It will be slower if you are not in the US but it will be up to date and will fix the out of date mirror issue.

I hope that helps.

Powel

---

### Post by seandude on 2009-09-06
I am in the US, I just let software sources find my closest mirror site, which just happens to be in Canada.  But that would make sense since the errors only showed up after I changed it.

Thanks.

---

### Post by seandude on 2009-09-06
Just tried doing what you said, but Synaptic isn't registering any broken packages.  Now what?

---

### Post by pastalavista on 2009-09-06
> **seandude said:**
> Just tried doing what you said, but Synaptic isn't registering any broken packages.  Now what?apt-get check is just to make sure apt is working with a valid server. What makes you think you have broken packages? To fix broken packages you can run ```
sudo dpkg --configure -a
``` or you could run ```
sudo aptitude safe-upgrade
```

---

### Post by winotree on 2009-09-06
I don't really believe that what you're seeing is an error -- I may be wrong, but I don't think I am.  Look at what you've asked:  check my version.  It seems to have done that: giving a compilation date and supported modules, which it details.  Those idx are *index* files -- even says so.  Besides I just finished a fresh installation and know there's nothing wrong with my system and look:

user@PasturePrime:~$ sudo apt-get check -v
apt 0.7.20.2ubuntu6 for i386 compiled on Apr 17 2009 04:25:29
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file

Isn't that the same as yours?  Like I said, I may be wrong but we can't both be exactly wrong, together.  Can we?  ;)

---

### Post by seandude on 2009-09-06
Ok, so what does that mean?

And Pastalavista, I just ran the "sudo dpkg --configure -a".  The terminal didn't output anything, does that mean everything is alright?

---

### Post by powel212 on 2009-09-06
After changing the mirror go to add/remove and try installing something. For example "Chromium B.S.U." Just a game. If it installs without errors you're good. If you get errors please post the error here.

Hope that helps.

Powel

---

### Post by seandude on 2009-09-06
Oh no, I've had no problem installing packages/apps.

---

### Post by winotree on 2009-09-06
> **seandude said:**
> Ok, so what does that mean?
[quote=winotree]....Look at what you've asked: check my version. It seems to have done that: giving a compilation date and supported modules, which it details. Those idx are *index* files -- even says so....[/quote]
It means there is, in all likelihood, nothing wrong with your installation of Ubuntu.  It means that you finally hit upon a combination of commands in your terminal that you'd never used and got a response you'd never seen.  Rather than taking it as information to be appreciated, you took it as an error.  :?

[quote=winotree].... Like I said, I may be wrong **but we can't both be exactly wrong, together**....[/quote]

NOTE - emphasis added 

Hoping to hear from you later today confirming your system is in stable working condition  ;)

---

### Post by seandude on 2009-09-20
Sorry I was away for a while.  My system is working fine.  I'd taken it upon myself to delete some old archives (mostly using apt-get autoclean).  I then did an "apt-get --help" just to see what else i could do and saw 'apt-get check", so I ran it, and it gave me that.  I thought that "check" meant "check for broken dependencies", so I figured I'd run to the forums and get some help. :>

---

