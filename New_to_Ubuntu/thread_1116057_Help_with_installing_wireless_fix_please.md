---
title: "Help with installing wireless fix please"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by wiseloki on 2009-04-04
Hi,

I recently upgraded to 8.10 and now my I can't access my WPA network. I tried a thread in the Wireless forum over a week ago here [http://ubuntuforums.org/showthread.php?t=1108307]("http://ubuntuforums.org/showthread.php?t=1108307") but had no help offered.

I did some more browsing around the fora and found that it appears that others have had the same problem. I have now found this thread:-

[http://ubuntuforums.org/showthread.php?t=975684]("http://ubuntuforums.org/showthread.php?t=975684")

And that leads to this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390")

The only thing different to my issue is that these threads did not specify that the passkey was not being maintained unchanged, but other than that, their symptoms are my symptoms exactly.

So my help request to this forum is as follows: being an Ubuntu novice, I've seen the manual fix in the bug report:

> Resolution (manual):
conn@inspiron:~$ sudo rmmod ipw2100 ieee80211_crypt ieee80211_crypt_tkip ieee80211_crypt_ccmp
conn@inspiron:~$ sudo modprobe lbm_cw_ieee80211_crypt_tkip lbm_cw_ieee80211_crypt_ccmp ipw2100

and this looks pretty scary to someone unused to tinkering under the hood. So my request is now for some help with understanding and installing the fix. 

I know that the command "sudo" in a terminal window is telling Ubuntu to do something fundamental (explanation of exactly what would be welcome, but probably outside the scope of this thread - I can Google later), but I don't understand the  "conn@inspiron:~$" part in front of it. 
[LIST]
[*]Is this something specific to a Dell Inspiron? (I have an IBM T42)
[*]Do I need it, or should I just try the two commands from "sudo" onwards? Or is it Linux-speak that I need to include?
[/LIST]

I'm looking forward to a little hand-holding from you guys as I'll be tweaking Ubuntu for only the second time, so thanks in advance.

As an aside, I'm a little surprised that a bug reported in November still appears to be there on a new install. So I'm hoping it is the real problem.

---

### Post by billgoldberg on 2009-04-04
> **wiseloki said:**
> Hi,

I recently upgraded to 8.10 and now my I can't access my WPA network. I tried a thread in the Wireless forum over a week ago here [http://ubuntuforums.org/showthread.php?t=1108307]("http://ubuntuforums.org/showthread.php?t=1108307") but had no help offered.

I did some more browsing around the fora and found that it appears that others have had the same problem. I have now found this thread:-

[http://ubuntuforums.org/showthread.php?t=975684]("http://ubuntuforums.org/showthread.php?t=975684")

And that leads to this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390")

The only thing different to my issue is that these threads did not specify that the passkey was not being maintained unchanged, but other than that, their symptoms are my symptoms exactly.

So my help request to this forum is as follows: being an Ubuntu novice, I've seen the manual fix in the bug report:



and this looks pretty scary to someone unused to tinkering under the hood. So my request is now for some help with understanding and installing the fix. 

I know that the command "sudo" in a terminal window is telling Ubuntu to do something fundamental (explanation of exactly what would be welcome, but probably outside the scope of this thread - I can Google later), but I don't understand the  "conn@inspiron:~$" part in front of it. 
[LIST]
[*]Is this something specific to a Dell Inspiron? (I have an IBM T42)
[*]Do I need it, or should I just try the two commands from "sudo" onwards? Or is it Linux-speak that I need to include?
[/LIST]

I'm looking forward to a little hand-holding from you guys as I'll be tweaking Ubuntu for only the second time, so thanks in advance.

As an aside, I'm a little surprised that a bug reported in November still appears to be there on a new install. So I'm hoping it is the real problem.

Doing stuff that affects the whole OS, not just the user, needs sudo. 

Sudo is doing su, su meaning super user (root). Think admin in Windows.

"conn@inspiron:~$" is the terminal prompt. It contains your username (conn) and the name of the machine you are on (inspiron). 

If you were to ssh into another machine for instance that prompt would change, and the prompt would tell you what machine you are manipulating.

--

About the commands, I don't really know the stuff used in it. It's most likely safe to use.

Use the man command in the terminal to be sure what something does.

In a terminal issue "man rmmod" for instance.

---

### Post by wiseloki on 2009-12-06
Just for info, I upgraded to 9.10 and this seemed to fix the issue......for a while.

It now looks like I had an unknown and intermittent hardware problem. Issue solved by ditching the T42 and installing Ubuntu on an X60s

Thanks for the advice, though

---

