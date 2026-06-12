---
title: "Using rkhunter and maybe chkrootkit"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by mikodo on 2009-04-06
Hello Everyone,

My first post. I was using MS Vista until I was hit with the Conficker Worm on April 01,2009 (long story). I downloaded and burned to disk Ubuntu Hardy 8.4.02 i386(2) and wrote it over MS and do not intend to use MS again. I am trying to secure Hardy. I have configured Firestarter and ClamTK and have set up encrypted files and emailing. I do not have the knowledge yet to configure AppAmor or to work with iptables for Netfilter.

 I have downloaded rkhunter 1.3.0-3 and installed it, as is it is shown in my Synaptic Package Manager. I cannot find it on my desktop as a GUI nor find any way to run it. My guess as a Newbie is that it needs to be run in sudo or root.

Can anyone tell me how to use rkhunter?

Thank you in advance.

First Things First!

---

### Post by rattking on 2009-04-06
Hi 
to use rkhunter open a terminal window and run
sudo rkhunter -c

and to make sure rthunter is up-to date run
sudo rkhunter --update

---

### Post by mikodo on 2009-04-06
Thank you for the reply, I used sudo with your instructions and rkhunter ran. ( my first terminal sudo effort!) It felt good. Bye MS.

---

### Post by mgranet on 2009-04-06
Unless you are concerned with an attempt by a determined attacker to compromise your rig, there is little need to attempt to secure Ubuntu beyond what is provided. Rkhunter and chkrootkit are great tools to find one of the greatest threats to your computer (the rookit, of course); trying to modify IPtables and screwing around with AppArmor are more likely to get you into problems than to improve the security of an end-user system. This ain't an attempt to start a fire with the security folks, just suggesting the Windows way of online life (install massive security, harden, and pray) is not really needed as much with Ubuntu. It gets to be a nice feeling after a while :)

---

### Post by mikodo on 2009-04-06
Say, to use and update chkrootkit would I use in terminal:

sudo chkrootkit -c and
sudo chkrootkit --update

Thanks again,

---

### Post by mgranet on 2009-04-06
The options vary with the app. You can usually use the ```
--help
``` switch after the command to get a list of the available options, and a description of what they do.

---

### Post by albinootje on 2009-04-06
> **mikodo said:**
> I am trying to secure Hardy. 

You're not running MS-Windows anymore, relax your shoulders, take a deep breath, drop the paranoia, and feel the difference of Ubuntu :)
> 
I have configured Firestarter and ClamTK and have set up encrypted files and emailing. I do not have the knowledge yet to configure AppAmor or to work with iptables for Netfilter.

For a desktop computer with Ubuntu in a trusted LAN there is no need for all this imho.
It's more important to keep your software up to date, especially the software which communication with the internet, like Firefox, Flash-plugin, IM-programs, pdf-reader etc.

I recommend using noscript addon for Firefox, and some sensible web surfing, do not just install software from unknown 3rd parties, try to stick to the Ubuntu repositories and things like [http://getdeb.net](http://getdeb.net)
> 
Can anyone tell me how to use rkhunter?

Open a terminal, and type : 
```

sudo rkhunter -c

```

Read also this carefully :
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by mikodo on 2009-04-06
Thank you, to you all, for the information, Especially to albinootje, for the kind welcoming in the private note.

mikodo

---

### Post by HermanAB on 2009-04-06
Howdy,

Relax and enjoy your new secure system.  Don't run rootkit and virus detection programs.  It is a waste of time and will only yield false alarms, since there aren't any real alarms.

---

### Post by deadlockedgamer on 2010-02-09
chkroot gave me the following Searching for anomalies in shell history files...           Warning: `//home/tag/.kino-history' is linked to another file is this an issue or false warning. There is nothing in the .kino-history folder I can find

---

### Post by deadlockedgamer on 2010-02-09
oh and rkhunter says /usr/sbin/unhide                                         [ Warning ] and
 /usr/sbin/unhide-linux26                                 [ Warning ]
and Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
 Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]
    Checking version of PHP                                  [ Warning ]
help and I infected network showed no infection and please combine this with other check

---

### Post by 3rdalbum on 2010-02-09
There's a log file, that rkhunter asks you to look at once the scan is done. This gives you more information.

Do you have your firewall set to block all incoming connections? If you have any holes poked in your firewall, are they going only to non-root programs such as your torrent client or Apache? If the answer to either of those questions is "yes", then you don't need to check for rootkits.

---

### Post by deadlockedgamer on 2010-02-10
Isn't the iptable set to block all incoming connection? plus how do you view the log file gedit could not open it. Plus I have wireshark and ettercap as root.

---

