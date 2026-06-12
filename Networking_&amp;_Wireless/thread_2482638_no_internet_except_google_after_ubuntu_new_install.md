---
title: "no internet except google after ubuntu new installation"
date: 2023-01-06
forum: Networking &amp; Wireless
---

### Post by renat784 on 2023-01-06
Hello, I installed linux mint cinnamon on my dell laptop (dual boot with windows 10) but after regular installation with installing all drivers the internet became working strangely. If you use google search engine - it shows the results. If some other - no internet. You can go directly on youtube ang google translate but other sites not working at all. It says some problem with dns can't be found. I thought may be some bug with linux mint. So I installed Ubuntu and I got the same result. I installed several times in my life on the same laptop ubuntu and win 10 and never experianced such problem before. Internet always was working. So I started looking for the way to solve the problem I tried deleting dns cashe and adding some lines in files like 8.8.8.8 and 8.8.4.4 but it didn't work on on some point even google stopped working. So it seems i broke whole thing. I made usb stick with ubuntu, ran live version and internet worked through browser just the same way. I share my internet via wifi hotspot on my phone and it seems like it installing everything at start but if you later try to find updates it shows connection problems while updating. So I cant update enything and I can't solve the problem. So I deleted ubuntu :mad:    . Now I stuck with win10. So maybe it some bug with this new version of ubuntu (ubuntu and linux mint) or it just works like that on my machine? Cause I want to work on Ubuntu but these problems on start makes me won't.

---

### Post by TheFu on 2023-01-06
Exactly which files were changed and what did you change?  

Or should we randomly guess?  My first guess for a file that was change is: /etc/resolv.conf  What that it?  Did I win anything?
Would also help to specify OS versions ... you know ... the numbers.

BTW, Linux Mint isn't Ubuntu.  Posts about it should be in "Other Distro" sub-forum.

For the last 3 yrs, or so, Ubuntu has been using systemd-resolved.  This generally works, but when it fails, it is 2 levels away from the actual file used by the OS and all programs to perform DNS queries.  What's worse is that it will overwrite any changes to the real file unless it is completely disabled.  For a laptop, disabling systemd-resolved will cause problems each time the computer is moved to a new network.  For a home desktop, that really isn't too much of a concern, unless you expect DHCP to work in setting the DNS servers.

Seems a big odd that both Ubuntu and Mint have the same issue.  That makes me think there's something odd with your network, your DHCP server or your modem connection to the internet.  Since I've never used wifi connections to a commercial wifi provider and barely use a smartphone, it is doubtful I can help.

Anyway, if you can 'ping 8.8.8.8', but 'dig google.com' doesn't work, it is a DNS issue that needs fixing.  So your idea that was the problem is accurate.

---

### Post by renat784 on 2023-01-06
yes [COLOR=#000000]/etc/resolv.conf
[/COLOR]Ubuntu 22.04.1 LTS
[COLOR=#000000]ping 8.8.8.8', but 'dig google.com'  - for google it works[/COLOR]

---

### Post by renat784 on 2023-01-06
yes [COLOR=#000000]/etc/resolv.conf
[/COLOR]Ubuntu 22.04.1 LTS
[COLOR=#000000]ping 8.8.8.8', but 'dig google.com' - for google it works but not for others
I tried different things by watching youtube tutorials but nothing helped[/COLOR]

---

### Post by TheFu on 2023-01-06
> **renat784 said:**
> yes [COLOR=#000000]/etc/resolv.conf
[/COLOR]Ubuntu 22.04.1 LTS
[COLOR=#000000]ping 8.8.8.8', but 'dig google.com'  - for google it works[/COLOR]

That just points out the Google-Chrome is violating OS standards, yet again.

So, before you changed /etc/resolv.conf did you
a) stop, disable and mask systemd-resolved?  'systemctl' is the command ...  you'll need some options.
b) remove the symbolic link and create a real file with that name/location?
c) get the format of the file correct?  It isn't hard, but being correct matters.

[https://ubuntuforums.org/showthread.php?t=2362619&p=13651220#post13651220](https://ubuntuforums.org/showthread.php?t=2362619&p=13651220#post13651220) has the stop and disable spelled out. You can figure out the 'mask' option.

---

### Post by renat784 on 2023-01-06
I have mobile internet and share it with wifi hotspot to laptop - but it's first time when i have such a problem and that is strange that google services work but other sites don't. It doesn't matter after installation or just live usb. My thoughts were corrupted iso image or soft to make bootsble usb. But I tried 2 differents soft and 2 iso (mint and ubuntu). result the same

---

### Post by renat784 on 2023-01-06
when I installed ubuntu I ran firefox with default google search and everything seem ok. But I always using duckduckgo search engine and after i switched intermet stopped working. That was odd. So I switched back to google search and it worked but links when opened got error: dns cannot be found, working... and errror some like .......DNS_NX (long title). But youtube opened instantly so as google translate

---

### Post by renat784 on 2023-01-06
if I am not mistaken when I tied to do some with [COLOR=#000000]systemd-resolved. I got error in terminal command not found[/COLOR]

---

### Post by renat784 on 2023-01-06
my problem simular to [https://askubuntu.com/questions/951057/ubuntu-dns-error-chrome-dns-probe-finished-nxdomain-firefox-similar](https://askubuntu.com/questions/951057/ubuntu-dns-error-chrome-dns-probe-finished-nxdomain-firefox-similar) but didnt help in my case

---

### Post by TheFu on 2023-01-06
> **renat784 said:**
> if I am not mistaken when I tied to do some with [COLOR=#000000]systemd-resolved. I got error in terminal command not found[/COLOR]

Did you use tab completion?  I always do, so never quote me on the exact names of any service.  I honestly don't know, since tab completion will create the correct answer for me ... or you.

---

### Post by renat784 on 2023-02-05
Problem solved.
I was using wifi hotspot from my smartphone and at the same time vpn was working on the phone. It never was a problem in windows 10 but for ubuntu 20.04, 22.04 and linux mint (latest) it was a problem. Some popular websites were working but not all of them. For example quora and stackoverflow didnt work. Google Chrome sad "Hmm, some dns problems" or "dns probe bla bla bla...". 
So I turned off vpn on phone and everything now ok. I even installed vpn on linux and turned on vpn on phone and everything seems work just fine. No problem.
Just found this solution (turn off vpn) on some site accidently and it worked.

---

### Post by TheFu on 2023-02-06
A) Please mark this thread as "SOLVED" using the thread tools button, so others can find it when they look for similar issues.

B) I suspect what you've found is that your VPN isn't secure and it leaking DNS. If you care about privacy, you'll want to ensure that is corrected either by fixing some VPN settings or by changing to a different VPN provider.  For every VPN service, if you aren't paying a reasonable amount, expect that your data is what they are selling.  Every few months, there are some reputable websites that re-test VPNs seeking those with the best implementations, if you care.  If you are really paranoid, for $5/month, you can setup a VPS somewhere and run your own VPN server.  Then you'll have complete control over logging (or zero logging) and be able to run the entire system in RAM without any logs, if you like.  Then just shutting down the VPS will drop all logs.  Depending on the reason for a VPN, this might be very useful.

---

### Post by renat784 on 2023-02-10
And a little update. 
   I tested it with 2 different vpn providers and found that this problem only occurs with nordvpn installed and running on smartphone while wifi hotspot is working. So you need to turn off that vpn on the phone or you'll have problems with accessing websites on ubuntu.
  But, if you using expressvpn everething is working fine. You don't need to do anything.
So if you choosing vpn - better stick to expressvpn.
I had problems with nordvpn in windows 10 and ubuntu like can't automaticly log in after restarting OS or software update (in windows 10), it always connected slowly and had ping like 100 or more, and on ubuntu it was time to time switching between servers and one time just turned off and couldn't connect.
  I never had such troubles with expressvpn. It always just worked and that's it.

---

### Post by TheFu on 2023-02-10
> **renat784 said:**
>  
  I never had such troubles with expressvpn. It always just worked and that's it.

While "working" is good, be certain you don't mind the ownership of the company.  I'll leave it to others to perform their own research.  That goes towards trust.  When it comes to VPNs, trust is key.
[https://www.computerweekly.com/news/252466203/Top-VPNs-secretly-owned-by-Chinese-firms/](https://www.computerweekly.com/news/252466203/Top-VPNs-secretly-owned-by-Chinese-firms/)
[https://www.vpnmentor.com/blog/companies-secretly-own-dozens-vpns/](https://www.vpnmentor.com/blog/companies-secretly-own-dozens-vpns/)

---

