---
title: "Knetworkmanager problem"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Alberto2 on 2008-06-12
Hello,
I'm using Kubuntu 8.04 in dual boot with Win 98 SE with satisfaction, but I have got a problem about connecting to the Internet (ADSL connection via cable). In fact, sometimes (a little frequently), **Knetworkmanager** fails in connecting to it (and no messages are displayed).
So, every time that happens, I close the Kubuntu session, start a Windows one and immediately I can connect to the Internet.
I'll be grateful to you if you give me some advice to solve this problem.
Best Regards

---

### Post by Ayuthia on 2008-06-12
> **Alberto2 said:**
> Hello,
I'm using Kubuntu 8.04 in dual boot with Win 98 SE with satisfaction, but I have got a problem about connecting to the Internet (ADSL connection via cable). In fact, sometimes (a little frequently), **Knetworkmanager** fails in connecting to it (and no messages are displayed).
So, every time that happens, I close the Kubuntu session, start a Windows one and immediately I can connect to the Internet.
I'll be grateful to you if you give me some advice to solve this problem.
Best Regards
Have you tried connecting to your router manually?  Here is an example of how to do it in the Terminal if you don't have encryption set on your router:
```
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
Just replace name with the essid of your router.  For more information about how to connect manually, try this [link]("http://ubuntuforums.org/showthread.php?t=684495").
This is not the ideal solution, but it will help determine if Knetworkmnager is having problems.  If it is, you might try another network manager link wifi-radar or wicd.

---

### Post by Alberto2 on 2008-06-12
Hello,
Maybe I haven't explained well my problem, as, even if my router can do both, I'm connecting to the Internet by means of a cable and the ethernet card. So, no need of essid.
Is there a way to check if, in my case, Knetworkmanager works all right? And, is there another application like knetworkmanager I could try? (by command line, too?)
Best Regards

---

### Post by Ayuthia on 2008-06-12
> **Alberto2 said:**
> Hello,
Maybe I haven't explained well my problem, as, even if my router can do both, I'm connecting to the Internet by means of a cable and the ethernet card. So, no need of essid.
Is there a way to check if, in my case, Knetworkmanager works all right? And, is there another application like knetworkmanager I could try? (by command line, too?)
Best Regards
No, you explained your problem just fine.  I just can't read.

You should be able to check it manually:
```
ifconfig
```
This should show if you are connected or not because an ip address should be associated with it.  If it does not connect, you might also check dmesg from the Terminal.  If you check it when you lose the connection, you should be able to see a message on what happened.

---

### Post by Alberto2 on 2008-06-12
Thank you,
I'm a beginner with Linux (but I like it and its philosophy).
In the meantime I had a look at wicd installation procedure, so I added this line to the sources.list file: deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
then I typed apt-cache search wicd but my return ended with no informations.
At last I typed apt-get install wicd but the response was that wicd is not found.
Isn't that repository the right one for my Kubuntu 8.04?
Any help?
Best Regards
P.S.
In case I succeed in installing wicd, I must uninstall Knetworkmanager that is not compatible with it (but I have to do that after, otherwise I don't have any connection to the repository where wicd is).

---

### Post by Ayuthia on 2008-06-12
> **Alberto2 said:**
> Thank you,
I'm a beginner with Linux (but I like it and its philosophy).
In the meantime I had a look at wicd installation procedure, so I added this line to the sources.list file: deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
then I typed apt-cache search wicd but my return ended with no informations.
At last I typed apt-get install wicd but the response was that wicd is not found.
Isn't that repository the right one for my Kubuntu 8.04?
Any help?
Best Regards
P.S.
In case I succeed in installing wicd, I must uninstall Knetworkmanager that is not compatible with it (but I have to do that after, otherwise I don't have any connection to the repository where wicd is).

Have you run sudo apt-get update?

---

### Post by devnulljp on 2008-06-12
> **Alberto2 said:**
> Hello,
I'm using Kubuntu 8.04 in dual boot with Win 98 SE with satisfaction, but I have got a problem about connecting to the Internet (ADSL connection via cable). In fact, sometimes (a little frequently), **Knetworkmanager** fails in connecting to it (and no messages are displayed).
So, every time that happens, I close the Kubuntu session, start a Windows one and immediately I can connect to the Internet.
I'll be grateful to you if you give me some advice to solve this problem.
Best Regards
I'll lay you odds that knetworkmanager is putting the wrong interface as the default route.
In knetworkmanager, click Routes, you'll see Default gateway (that should be your router) and device -- that should be your interface. I've seen it seemingly at random try to push through the wrong interface and the connection won't work.  
I'm really not liking knetworkmanager...

---

### Post by Alberto2 on 2008-06-13
Ayuthia and devnulljp,
Thank you for your advice.
First: sudo apt-get update permitted, at last, the installation of wicd
Second: I cannot operate on Knetworkmanager settings any longer as now I've installed wicd (the two of them are not compatible).
Best Regards

---

