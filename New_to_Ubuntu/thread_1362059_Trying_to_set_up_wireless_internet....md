---
title: "Trying to set up wireless internet..."
date: 2009-12-22
forum: New to Ubuntu
---

### Post by speedygonzalas on 2009-12-22
Hey, I've been trying to set up a wireless internet connection using this link:
[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)
and so far everything has gone well except I'm now stuck on step four part 5) which requires me to open up /etc/modules using text editor and add 'ndiswrapper' to the bottom of the file, but every time I try to save it the computer tells me I do not have the privileges. I tried going to the terminal and using sudo -i to become root which seems to put me as root in the terminal but doesn't make any difference outside of it. I need to know what I need to do to make this change.
Thanks a lot in advance.

---

### Post by zuber786 on 2009-12-22
I am not sure how to help you
I tell you what happened with me, I am currently using Kubuntu
before I was using ubuntu itself, and I never had to set up internet manually 
it was automatically setup for me.

---

### Post by USB_NL on 2009-12-22
hi

```
sudo su
```

dos that help?

---

### Post by USB_NL on 2009-12-22
[quote=speedygonzalas;8544530]I tried going to the terminal and using sudo -i to become root[/quote=speedygonzalas;8544530]

what dos ```
sudo -i
``` do?

---

### Post by speedygonzalas on 2009-12-22
It's supposed to enable you as a a root user in the terminal as far as I know according to this
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
and it didn't really help, but thanks alot anyways.

---

### Post by speedygonzalas on 2009-12-22
Yeah for me that's normally the case, in fact I'm using my computer with the internet right now as we speak, except I have it connected through the ethernet cable but I need to make it a wireless connection instead to the router so I can use my computer from my room. o well... I guess I'll just have to keep digging.

---

### Post by USB_NL on 2009-12-22
sudo ifconfig wlan0 down

stops wlan0 in step 5

is that the problem?

---

### Post by 3rdalbum on 2009-12-22
Ndiswrapper does not work with wireless internet (mobile broadband), only with wireless networking. If you are talking about the type of internet connection which works from mobile phone towers, then right-click on the Network Manager and add a Mobile Broadband connection.

---

