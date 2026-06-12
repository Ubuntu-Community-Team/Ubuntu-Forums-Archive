---
title: "Internet Security Program to Use?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by lpa53 on 2008-12-25
I just installed Ubuntu a few days ago on a castoff work laptop.  I did the install that wipes out Windows.  All is fine and I'm exploring but all of a sudden wondered about security when on the web.  

I'm an AT&T subscriber and with that I can protect my Windows laptop with McAfee for free (much better than the Norton they used before). I can download it from the web but will it work in Ubuntu?  If not, is there anything good out there that will work - and not cost me?

---

### Post by binbash on 2008-12-25
you dont need to use antivirus software, however you may want to use a firewall.there is ufw default installed with ubuntu

---

### Post by albinootje on 2008-12-25
> **lpa53 said:**
> I just installed Ubuntu a few days ago on a castoff work laptop.  I did the install that wipes out Windows.  All is fine and I'm exploring but all of a sudden wondered about security when on the web.  

I'm an AT&T subscriber and with that I can protect my Windows laptop with McAfee for free (much better than the Norton they used before). I can download it from the web but will it work in Ubuntu?  If not, is there anything good out there that will work - and not cost me?

Read this :
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Concerning computer-security more general :

Personally I prefer to use the no-script and adblock-plus addon in Firefox to keep my web-browsing more secure. But no-script is not easy to use, you can play with it, but be prepared that per webpage you visit, you might have to do some "approval" in no-script in order to properly see parts of the webpage.
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

### Post by abn91c on 2008-12-25
ubuntu's GUI firewall ifs firestarter, it is in the repositories or do in a terminal
sudo apt-get install firestarter

---

### Post by RomeReactor on 2008-12-25
Hi. Although there is no absolutely safe system, Ubuntu--and Linux in general--is rather secure. Antivirus applications in Ubuntu usually scan for windows viruses, so if you don't have windows installed, you likely don't need it; a firewall is a good idea, though. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=510812") for more information on keeping Ubuntu secure.

---

### Post by oilchangeguy on 2008-12-25
> **RomeReactor said:**
> Hi. Although there is no absolutely safe system, Ubuntu--and Linux in general--is rather secure. Antivirus applications in Ubuntu usually scan for windows viruses, so if you don't have windows installed, you likely don't need it; a firewall is a good idea, though. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=510812") for more information on keeping Ubuntu secure.

ubuntu has a built in firewall, iptables. true you can install firestarter, which is a user interface for iptables. but for 99.9% of ubuntu users iptables is best left alone.

---

### Post by albinootje on 2008-12-25
> **oilchangeguy said:**
> ubuntu has a built in firewall, iptables. true you can install firestarter, which is a user interface for iptables. but for 99.9% of ubuntu users iptables is best left alone.

Yes, true, I agree with that for the, say, 99.9% Ubuntu desktop users.

Except when you have certain services running (Think about portmap,NFS,Samba) and :

1) You're using some old-fashioned dial-up modem.
2) You're inside a LAN where you cannot trust everyone.
3) Using some open or not that well secured wifi-connection.

---

### Post by mkvnmtr on 2008-12-25
In the repositories there is a lot of very good anti intrusion software. There are programs to scan your system. there are guis to set up your firewalllllll but the normal user never uses them. The best thing for us to do is use strong passwords and a third user to do all your work in. Save your first user with the sudo password for working on the system. Then is something gets in it only affects the one user. You can delete the account and open another. I don't do all that. I have not known of a need to be that careful. Besides I have never had a virus and kind of want to see what all the fuss is. I was a Mac user for years without a antivirus system and still don't know what a virus is like.

---

