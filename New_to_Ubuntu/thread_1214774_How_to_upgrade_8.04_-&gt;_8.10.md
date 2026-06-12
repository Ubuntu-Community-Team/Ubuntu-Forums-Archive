---
title: "How to upgrade 8.04 -&gt; 8.10"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by ericg_ on 2009-07-16
How do I upgrade 8.04 LTS to 8.10?  I am doing this because I would like to experience the process of upgrading 8.10 to 9.04.

1) I have installed 8.04.2 LTS (downloaded from /www.ubuntu.com/getubuntu/download on 2009.07.15 and installed) 
2) Ran the Update Manager (which downloaded 155 files and installed them)
3) Checked my version (cat /etc/issue) to see I am now at 8.04.3 LTS
4) Ran the update manager again, to see if it would now move me to 8.10 (but to no avail)

I know I can install 9.04 over top of my current install.  However, I am going through these steps because I am new to Ubuntu and what to learn in a somewhat logical sequence.

-EricG

---

### Post by Waappu on 2009-07-16
Hi

I found this. Use with own risk
[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html)

I recommend to upgrade by install again lattes release.

---

### Post by 3rdalbum on 2009-07-16
> **Waappu said:**
> Hi

I found this. Use with own risk
[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html)

No no no no no!

That howto is for upgrading to an in-development release of Ubuntu, which is certainly not what you want, and is not likely to go successfully anyway as it's too large a jump from 8.04 to 9.10 alpha.

Go into System > Administration > Software Sources and under the Updates tab, choose to show "Normal releases" as updates. By default, an LTS release like Hardy will only allow you to upgrade to another LTS release; but you can change this behaviour to allow an upgrade to the next release.

Once you have "Normal releases" enabled for updates, then you can run the Update Manager from the System > Administration menu and wait a minute or two; it will give you the option of upgrading to 8.10.

---

### Post by Waappu on 2009-07-16
> **3rdalbum said:**
> No no no no no!

That howto is for upgrading to an in-development release of Ubuntu

Well, 8.10 is not anymore development release and principle should work same as you just post

---

### Post by ericg_ on 2009-07-16
The upgrade to 8.10 went very well (nice & smooth).  Thank you for the information.  It was not completely obvious that your steps were the necessary steps to upgrade.  I did not find anything on the Web close to your pointed directions either.  Was 8.04 LTS not designed for upgrading?

EricG

---

### Post by alexcckll on 2009-07-16
Hardy is a Long Term Support release - I'm running it myself.. however, I would prefer to wait for the next LTS before upgrading.

It basically means I can stay on more stable code...

If you're on the normal release, you have to upgrade through all the different versions.

Personally, I like stability.

---

### Post by ericg_ on 2009-07-17
As you can see by my profile, I am now on Intrepid (Ubuntu 8.10).  I have no regrets, but like you I prefer stability in my operating systems.  I wish I would have understood what LTS (Long Term Support) stood for prior to upgrading.  I would have stayed put.

Being new to Ubuntu and a recent "returner" to UNIX/Linux after a 15+ year walk-about, you lose touch.  But MAN!!!  I am enjoying the return!!!

EricG

---

### Post by bodhi.zazen on 2009-07-17
> **Waappu said:**
> Well, 8.10 is not anymore development release and principle should work same as you just post

```
sudo update-manager-d
``` is the proper way to update 

[http://www.ubuntu.com/testing/intrepid/beta#Upgrading%20from%20Ubuntu%208.04](http://www.ubuntu.com/testing/intrepid/beta#Upgrading%20from%20Ubuntu%208.04)

You can update LTS -> LTS 

Otherwise you need to go one at a time

8.04 -> 8.10 -> 9.04 -> 9.10 yea !!!

seriously, 9.10 is in alpha so while it !worksforme you might wish to stop at 9.04.

Update manager will make the right choice of version to upgrade to.

---

### Post by bodhi.zazen on 2009-07-17
> **ericg_ said:**
> As you can see by my profile, I am now on Intrepid (Ubuntu 8.10).  I have no regrets, but like you I prefer stability in my operating systems.  I wish I would have understood what LTS (Long Term Support) stood for prior to upgrading.  I would have stayed put.

Being new to Ubuntu and a recent "returner" to UNIX/Linux after a 15+ year walk-about, you lose touch.  But MAN!!!  I am enjoying the return!!!

EricG

Consider going to 9.04, it will be supported for longer then 8.10 and is stable.

---

### Post by ericg_ on 2009-07-18
Thanx...

I will consider upgrading to 9.04

-EricG

---

### Post by 3rdalbum on 2009-07-18
> **bodhi.zazen said:**
> sudo update-manager-d is the proper way to update 

[http://www.ubuntu.com/testing/intrepid/beta#Upgrading%20from%20Ubuntu%208.04](http://www.ubuntu.com/testing/intrepid/beta#Upgrading%20from%20Ubuntu%208.04)

Sorry for being so alarming - I thought the -d flag is for "development release", not for "next distribution". Still I think I did an upgrade from Hardy my way.

---

### Post by bodhi.zazen on 2009-07-18
Ah I see what you mean now, my mistake. I typically upgrade once I feel the beta is stable enough, beat the rush on release day.

At any rate, the point is, the preferred way to upgrade is with update manager.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

If you manually change your repositories, via synaptic or manually editing /etc/apt/sources.list, you are more likely to have problems. Has been this way for some time now.

---

