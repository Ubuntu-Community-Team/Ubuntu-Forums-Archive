---
title: "Some web pages will not work in Ubuntu"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by fallingleaf on 2007-10-09
This is very strange.  There are several web sites that simply won't function on Ubuntu but work on Windows machines on the same network.  I also have a VMware virtual machine running XP on the Ubuntu computer and they don't work there either.  Here are two examples.  

If I go to [https://www.yourpay.com/](https://www.yourpay.com/) and click login, it times out.  Works fine on Windows.  Same with [http://www.yousendit.com/](http://www.yousendit.com/)  I click login and it times out.

Running Feisty on a Thinkpad T60.

---

### Post by dickohead on 2007-10-09
Sounds like a local network issue...

Just for kicks, can you ping the addresses your trying to get to?

Open up a terminal and type in:
```

ping yourpay.com
ping yousendit.com

```

---

### Post by fallingleaf on 2007-10-09
Thanks for the reply.

Actually I can't ping the addresses.  DNS lookup works, but I get no response from the sites.

---

### Post by callan79 on 2007-10-09
> **fallingleaf said:**
> If I go to [https://www.yourpay.com/](https://www.yourpay.com/) and click login, it times out.  Works fine on Windows.  Same with [http://www.yousendit.com/](http://www.yousendit.com/)  I click login and it times out.
Running Feisty on a Thinkpad T60.

Looks like the sites change from HTTP to HTTPS (secure) when you click the login button, so you might be having issues with secure sites in general?

Are you using wireless? If so, are you using ndiswrapper? And what happens if you plug in via regular ethernet cable?

If you're using ethernet cable already, this might get interesting ....

Can you also verify that your broadband is just ADSL modem/router to your computer, and you're not going Internet => Router => Second Router => Computer ?

Cheers
Callan

---

### Post by fallingleaf on 2007-10-10
I am using wireless with ndiswrapper.  I have tried this on two different networks.  My network at home is an ISDN modem connected to a Windows XP box with internet connection sharing.  This has a Linksys router connected to it set to work as a wireless access point.  At work it is a DSL modem/router with a Belkin wireless router connected to it set to work as an access point.

I don't have a spare cable to connect the ethernet but I tried connecting directly with the ISDN modem  to the laptop and still having the same issue.

I haven't noticed any problems in general with https.

---

### Post by vincenzoo on 2007-10-10
Hello, i tryed to do so:
```
$ ping yourpay.com
PING yourpay.com (205.167.140.62) 56(84) bytes of data.

--- yourpay.com ping statistics ---
139 packets transmitted, 0 received, 100% packet loss, time 138052ms
```
but... what does it mean?

---

### Post by fallingleaf on 2007-10-10
I think it just means they have their server set to not answer ping requests.

---

### Post by callan79 on 2007-10-10
> **fallingleaf said:**
> I am using wireless with ndiswrapper.  I have tried this on two different networks.  My network at home is an ISDN modem connected to a Windows XP box with internet connection sharing.  This has a Linksys router connected to it set to work as a wireless access point.  At work it is a DSL modem/router with a Belkin wireless router connected to it set to work as an access point.

Curious issue, and don't worry about the ping failure, that's just the website's firewall.

Have you seen [http://ubuntuforums.org/showthread.php?t=482478](http://ubuntuforums.org/showthread.php?t=482478) ?

Cheers
Callan

---

### Post by fallingleaf on 2007-10-11
I think I found the problem.  I'm using Wicd instead of network manger.  I connected directly with the ISDN modem again, stopped the Wicd daemon, and now it works fine.  I guess I'll have to try to work out my issues with network manager.  Actually, I was planning on doing a fresh install when Gutsy final is released so maybe everything will work perfectly then.  :)

Thanks for the help.   I'll post my solution on that other thread as well.

Update: This seems to be fixed in the testing version of Wicd available here: [https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=233390&release_id=542935](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=233390&release_id=542935)

---

### Post by IwarV on 2008-03-22
apologies for dragging up an old thread, but I need some help translating the technical stuff  here.

I am using a *wired* router (Netgear RP614v3) and every so often my Ubuntu 7.10 refuses to make a secure connection, be it online banking or even simply e-mail.
What I have been doing so far is to unplug the input (from the modem) to the router, wait a minute or so and then reconnect.

Strangely enough however, this has not been an issue until in recent weeks. As if an update broke this on ubuntu.

Now I am 99.99% sure that the router is not to blame, because the other computer on the same router is running Windows XP (the 'gaming' machine) and that one has no problem with secure connections when this happens.

I.e.my finger is firmly pointing at Ubuntu.

I googled around and found this old thread. But it seems that even when the problems are pretty much the same, this thread seems to concentrate on wireless networking which is not the case on this particular occasion.

Any Ubuntu/networking buff here got any ideas or things for me to try?

Thanks in advance,

Iwar

---

### Post by update_manager on 2008-03-22
> 
I am using a *wired* router (Netgear RP614v3) and every so often my Ubuntu 7.10 refuses to make a secure connection, be it online banking or even simply e-mail.
What I have been doing so far is to unplug the input (from the modem) to the router, wait a minute or so and then reconnect.


Do you have any other issues when https doesn't work?

When you have this problem, run a packet sniffer like wireshark and post the output. You'll want to be careful that your post doesn't include any private info like your mails.

---

### Post by IwarV on 2008-03-22
Well, I installed WireShark and I am COMPLETELY lost.
That is some tool. Unfortunately, you'd need to be an expert in these things to make sense of it first.

Thanks for the help so far anyway.

---

