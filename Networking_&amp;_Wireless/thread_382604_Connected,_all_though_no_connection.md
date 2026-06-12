---
title: "Connected, all though no connection"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by transfixion on 2007-03-12
I installed Ubuntu again after a long long time.

I did it on a Packard Bell laptop. Ubuntu found both network cards, the wireless and the eth0 ethernet card. I was able to get it connected to the wireless using the SSID and WPA passphrase. 

Still, there is no rection from the net. It takes 2 minutes after I try to open a URL and it hits me back with "can not open page" (or whatever the message is). 

I am not sure if I tried this with the ethernet card and a cable, but I think I did and I got the same error message.

Installing any necessary apps or programs is hard because there is no connection to gain.

Any thoughts and help is appreciated.

---

### Post by chili555 on 2007-03-12
Please try this: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by transfixion on 2007-03-13
Thanks, I tried your help.

It worked half way - the other command; gksudo gedit /etc/modprobe.d/blacklist did not return anything.

The first command; gksudo gedit /etc/modprobe.d/aliases worked.

Could it work still, if I just follow the next step, or is the command that did not work very necessary?

Thanks.

---

### Post by conjur3r on 2007-03-13
Which one of these works?

# ping google.com
or
# ping 64.233.167.99

If neither, then see if you can ping your router or another machine on your LAN.  If you can't, you haven't successfully set up your wireless connection yet.

---

### Post by conjur3r on 2007-03-13
If it's not a networking issue, the article you are following above will disable IPv6 support system wide.  This is good if you are certain it is an IPv6 issue.  You can try disabling it in firefox first by going to 'about:config' and setting network.dns.disableIPv6 to true.  Restart firefox for changes to take effect.

---

### Post by transfixion on 2007-03-13
I will try as soon as I am back on the Ubuntu laptop. 

It does not have to be the wireless connection that should work. The wired with cable could work too - same procedure?

---

### Post by Rui Pais on 2007-03-13
> **transfixion said:**
> Thanks, I tried your help.

It worked half way - the other command; gksudo gedit /etc/modprobe.d/blacklist did not return anything.

The first command; gksudo gedit /etc/modprobe.d/aliases worked.

Could it work still, if I just follow the next step, or is the command that did not work very necessary?

Thanks.

Hi,
what do you mean by "gksudo gedit /etc/modprobe.d/blacklist did not return anything"? 
It should have opened a text file. Did the file was empty or gedit didn't start?

whats the output of
```
sudo cat /etc/modprobe.d/blacklist
```?

Btw, changing aliases it's not necessary. It may even not work, at least on edgy. You need to add a line to
> blacklist ipv6 to blacklist file and reboot.

You can check if it worked by typing:
```
lsmod | grep ipv6
```
it should give no output.

To ensure that your problem is in fact an ipv6 issue, you can disable ipv6 locally on firefox and see if it works. 
Open FF and type: 
> about:config
on 'Filter' type ipv6. It should give a 'network.dns.disableIPv6' on list bellow. Double click on that entry list until it says 'True' on value.
Restart FF and check if you can surf web.

Another thing. What happens when you do a: sudo apt-get update?

---

### Post by transfixion on 2007-03-13
Great, tty job error now. I can not even boot in to Ubuntu nor Debian anymore cause of the tty job problem. I got no idea how to fix that, I read through the forums, I found many threads, but failed to find the right solution.

Anger!!

---

### Post by Rui Pais on 2007-03-13
> **transfixion said:**
> Great, tty job error now. I can not even boot in to Ubuntu nor Debian anymore cause of the tty job problem. I got no idea how to fix that, I read through the forums, I found many threads, but failed to find the right solution.

Anger!!

Well that has nothing to do with your network problem. Seems that something important to the boot proccess was deleted or corrupted. Can this be related with the fack that you could happen to open your blacklist file?... something like /etc/ stuff deleted or corrupted?... 

Are you saying that both an Ubuntu and a Debian install fails? 
Do you have a common boot partition or something shared among the two?

Can you boot in a recovery mode?

---

### Post by transfixion on 2007-03-13
I can not boot at all. And it is not the first time I get this problem. I have Debian and Ubuntu on one hard disk. 

I can't boot in to recovery on neither one of my distros.

I have not been playing around in the /etc catalouge or any other file systems. So I can hardly imagine that I've been fat fingering around in places I shouldn't have been to.

How is this tty problem solved?

---

### Post by Rui Pais on 2007-03-13
OSs should be independent.
If you cannot boot ***any*** of them, you have either some common stuff that became broken,  (like a boot partition for all OSs) which seems not much a possibility anyway...
or you hardisk have some problem. Maybe even an hardware failure.

Boot from a live cd and do a e2fsck  -f on partitions of your drive.
Try to mount them to see if they available and you can read it.

Sorry, but sounds bad. 
You need to track the problem first before even start to think about solution... but it sounds bad :(

---

### Post by transfixion on 2007-03-22
Well, back on track. I fixed the tty;job problem.

I followed the IPV6 how-to in order to fix it. Well, now, the wireless connection stops at "idle" - it is not getting anything else than that.

I am running out of ideas on this.

Someone else here who has any clue?

Edit: I could need a pppoe or VPN setup option, can it be found? Or even a terminal-how-to on how to set up the wireless from the terminal.

---

