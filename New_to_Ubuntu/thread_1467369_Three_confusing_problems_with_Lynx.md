---
title: "Three confusing problems with Lynx"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by sb5551 on 2010-04-30
Hows everybody doing? Hope everyones enjoying the new version.

I am having some problems that I can't seem to figure out. 

I got Compiz Fusion working, but for some reason when I go to the settings manager I can no longer get the option for 3d windows, write fire, or change the cube into a sphere. I believe others also. Every command I try to install from the terminal comes back with I already have the packages.

I am trying to disable the login screen after booting the computer. I went to Settings> Admin> Login Screen and disabled the Show screen for choosing who will login, but it still shows this when I restart the computer. 

Is there a new tutorial to get Evolution to work with hotmail and Lucid? I followed all the ones I found on google that I followed with 9.10 won't get it synced with my email.

Thanks everyone for the help.

---

### Post by kill4killin on 2010-04-30
I suppose you mean Linux not Lynx, Lynx is a command line browser :P

Anyway, check this out hope it helps you with the evolution thing:
[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

---

### Post by sb5551 on 2010-04-30
Oops sorry. I meant Lucid Lynx. Thank you for the link. Ill have to look at it when I get home.

I found another problem. Whenever I used to connect to my NAS drive, I'd just go to connect to server the secure ftp (I think, the choice above the default) enter my IP address of the server and my username and it would be mounted. Now it mounts to the desktop, but says the media stream was interrupted and won't show my folders.

Thanks again everybody.

---

### Post by lockalidiot on 2010-04-30
For your compiz issue, install an extra plugin package with terminal:

```
sudo apt-get install compiz-fuzion-plugins-unsupported
```

---

### Post by mprince on 2010-04-30
> **sb5551 said:**
> I am trying to disable the login screen after booting the computer. I went to Settings> Admin> Login Screen and disabled the Show screen for choosing who will login, but it still shows this when I restart the computer.

Do you have "Enable Automatic login" checked? It used to be on the security tab. I'm not using Lucid (yet) so it may not be called that anymore.

[http://www.ubuntugeek.com/how-to-enable-automatic-login-in-ubutnu.html](http://www.ubuntugeek.com/how-to-enable-automatic-login-in-ubutnu.html)

---

### Post by sb5551 on 2010-04-30
lockalidiot- I tried that and it said that it couldn't find the package. It also said that when I typed the same thing but for extras. Thank you though. 

mprince- I don't have any tabs when I click on the login screen. Just one.

---

### Post by sb5551 on 2010-04-30
So I know its eaery should I just give up and go to 910.

---

### Post by kill4killin on 2010-05-01
> **sb5551 said:**
> Oops sorry. I meant Lucid Lynx. Thank you for the link. Ill have to look at it when I get home.

I found another problem. Whenever I used to connect to my NAS drive, I'd just go to connect to server the secure ftp (I think, the choice above the default) enter my IP address of the server and my username and it would be mounted. Now it mounts to the desktop, but says the media stream was interrupted and won't show my folders.

Thanks again everybody.

Oh, hehe I'm still getting used to this version being called Lynx...I have a feeling this will continue to confuse me...oh well

Personally, I might wait for 10.04 to mature a bit, it did JUST come out yesterday and even the release notes say it's got some kinks that haven't been ironed out yet, I wouldn't blame you if you did, I'm still sticking with 9.10 for now on my main laptop as well.

---

