---
title: "Ubuntu 9.04 Killed Ubuntu Restricted Extras"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-04-24
After I just upgraded my sister's Ubuntu to 9.04, I found seems to have made Ubuntu Restricted Extras to none effect. You tube says that I need Flash Player. I checked Synaptic Package Manager and Add/Remove Applications and found that I still had them installed. Likewise, did I find from another site that I needed to reinstall Java when again, both Synamtic and Add/Remove says that it is still installed. Is there a way of fixing this?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by inobe on 2009-04-24
had the same issue after an upgrade, removing **swfdec-mozilla** in synaptic fixed it.

i tried for over a week removing and reinstalling, that one thing took less than a minute.

---

### Post by halovivek on 2009-04-25
you have to reinstall the ubuntu restricted extras again. I got the same problem in one of my system. I have reinstalled the extras again and it went fine.

---

### Post by RedStarYellowSun on 2009-04-25
To inobe: Interesting... Will it affect Mozilla Firefox or Ubuntuzilla in any way?

To halovivek: Really? How do I do this? I won't have to hunt down Java, Flash, Microsoft fonts, etc..., right? Will uninstalling and reinstalling "ubuntu-restricted-extras" and all packages with "linux-restricted-modules" be enough?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by evertsfnic on 2009-04-25
it happend to me too. with a fresh install

---

### Post by unicornlover442 on 2009-04-25
Dear Inobi: I just upgraded to 9.04 also and when I tried to remove swfdec it wasn't installed so that didn't work for me.I also tried to reintstall the ubuntu restricted extras thru synpatic but message told me there was a conflict and to refer back to synaptic but I don't know how to resolve the conflict. I tried seeing if adobe flash was installed but I don't think it is. Also you tube tells me I need java too. Thanks for any help.

---

### Post by mikewhatever on 2009-04-25
> **unicornlover442 said:**
> Dear Inobi: I just upgraded to 9.04 also and when I tried to remove swfdec it wasn't installed so that didn't work for me.I also tried to reintstall the ubuntu restricted extras thru synpatic but message told me there was a conflict and to refer back to synaptic but I don't know how to resolve the conflict. I tried seeing if adobe flash was installed but I don't think it is. Also you tube tells me I need java too. Thanks for any help.

Can you use the **sudo apt-get install ubuntu-restricted-extras** command and post the output. I've checked the dependencies of ubuntu-restricted-extras package, and it appears that java isn't part of it any more. This makes sense because java has been open sourced, rather unfortunate for the OP, because he'd have to hunt for it. Well, happy hunting, and hope it doesn't take you longer then 10 seconds.

---

### Post by 73ckn797 on 2009-04-25
I have upgraded to 9.04 on all my computers (4).

You will have to check off the available sources via: System/Administration/Software Sources as a first ToDo. There are 2 that are not selected after installing 9.04.

Also Google "Medibuntu" and follow the instructions there to add their repositories. 

Look for sun-java in Synaptic for the latest version 6 jre and plugin. You should also find "flash non-free plugin" there.

Once Medibuntu is added you can find many other useful apps.

Also make sure restricted sources is selected in Software Sources.

---

### Post by unicornlover442 on 2009-04-26
Hey there Mikewhatever! I did the sudu apt command in the terminal that you suggested and it looks as if that may have worked. At the very end of all the commands it says:.

Setting up ubuntu-restricted-extras (31) ...
Setting up unrar (1:3.8.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
user@user-desktop:~$ 

I also checked off the 2 available sources that were not checked in Software Sources as 73ckn797 suggested and also made sure that restricted software multiverse was checked too. 
Also added the medibuntu repository list and received this response:

--2009-04-26 00:06:31--  [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 229 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 229         --.-K/s   in 0s      

2009-04-26 00:06:31 (21.2 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [229/229]

In Synaptic, the only Java package I could locate that was installed was "Java Common"  (of course, that is, if I looked in the right place).

So there you have it. Let me know, okay. I appreciate all of your help.

---

### Post by mikewhatever on 2009-04-26
Looks like it worked, and the problem must have been the disabled repositories. To install java, search for sun-java6-jre in Synaptic.

---

### Post by kjkoec on 2009-04-26
However, I have the same problem, and uninstalling swfdec-mozilla wants to uninstall gnome as well.
??

---

### Post by unicornlover442 on 2009-04-26
Dear Mike Whatever: Just now checked for any further replies. Thank you so much for telling me exactly what to search for!
I've now found the Sun-java-6-jre and the related bin file and applied them. It shows they are now installed packages.So everything  (hopefully) now should work properly!
Many thanks to you and all the others that made suggestions.

Just one question? Will these steps need to be done each time I upgrade Ubuntu to a newer generic, or perhaps it will change depending on what new developments come along?:KS:KS:KS

---

### Post by Bender2k14 on 2009-10-29
I had the same problem and was able to solve it.  I describe how I solved it in a [blog post]("http://ubuntu-chronicles.blogspot.com/2009/05/jaunty-flash-firefox.html").

---

