---
title: "security level is 0 ( 1 = none, 2 = standard"
date: 2016-05-28
forum: Networking &amp; Wireless
---

### Post by claudio19 on 2016-05-28
Hello

I have an error when i try to open from Windows 10 with Connection Desktop remote my ubuntu

security level is 0 ( 1 = none, 2 = standard)
error - problem connecting

I see already topic [http://ubuntuforums.org/showthread.php?t=2230453](http://ubuntuforums.org/showthread.php?t=2230453) but is not working

When i try to put the code inside Putty

[B]gsettings set org.gnome.Vino require-encryption false

[/B]i receive 


```
** (process:2602): WARNING **: Command line `dbus-launch --autolaunch=f52d6b5751470f46fa8fc7b200000009 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n


** (process:2602): WARNING **: Command line `dbus-launch --autolaunch=f52d6b5751470f46fa8fc7b200000009 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n

```

At the beginning the server was working just fine

I have 54 serves of Ubuntu and starting from  5 days i have that issue with 5 from all 54 and i don't know why

My steps to install xrdp are :

1[FONT=Arial][COLOR=#000000]** - **[/COLOR][/FONT]sudo apt-get update
2 - sudo apt-get upgrade
3 - sudo apt-get install xrdp
4 - sudo /etc/init.d/xrdp restart
5 - sudo reboot

When i launch remote desktop is working fine, after i close, i i want to open again i receive this error
If i reboot server i cal login again but after 5 min of logoff same issue

Little help ? Why others server are working just fine and this 5 no ? 

How i can solve this issue

Tnx

---

