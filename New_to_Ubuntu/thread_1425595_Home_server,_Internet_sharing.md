---
title: "Home server, Internet sharing"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by jirayam on 2010-03-09
Hello to all.

A week ago I scrapped my Windows server that did Internet connection sharing and internal file sharing duties in  my home.

I am not new to computers at all, but it has been impossible to get Ubuntu to share it's wired Internet connection with the other wired LAN connection. I believe I've tried everything.

First thing is that whenever I start the internal LAN connection I lose the Internet connection. I have to disconnect it to recover the Internet connection.

Trying to start both and set them up, via the 'simple' way of setting the Internet connection to shared or using Firestarter to set sharing and a firewall, it doesn't work.

It's very frustrating, not Ubuntu fun at all.

Many, many thanks in advance for your kind support.

---

### Post by [Shadow] on 2010-03-09
Hello!

I can at least help you with a little of that.

I know for sure that if you want to use your PC as a home server that shares files with other computers you will first of all want to install Samba, which will allow you to share folders and files with other computers on your network (windows, linux, etc.)

To install Samba

```
sudo apt-get install samba
```

Here are some interesting tutorials on connection sharing

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

Hope at least one of those helps you!

---

### Post by jirayam on 2010-03-09
Thanks Shadow. Willl read and reread that info to see if I get a clue.

Thanks again.

> **'[Shadow] said:**
> Hello!

I can at least help you with a little of that.

I know for sure that if you want to use your PC as a home server that shares files with other computers you will first of all want to install Samba, which will allow you to share folders and files with other computers on your network (windows, linux, etc.)

To install Samba

```
sudo apt-get install samba
```Here are some interesting tutorials on connection sharing

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

Hope at least one of those helps you!

---

### Post by jirayam on 2010-03-10
Well, I give up.

A manufacturer will be happy now I'm forced to get a hardware router.

No ubuntu for me.

---

### Post by marshmallow1304 on 2010-03-10
Hope I'm not too late.  If you're using 9.10, you can use the network config tool to share internet.  System->Preferences->Network Connections.  Select the connection you want to share, click Edit.  On the IPv4 Settings tab, change Method to "Shared to other computers".

---

### Post by QIII on 2010-03-10
You can share your internet connection as above.

But be aware that you will suffer some of the same performance degradation on your client machines as you would with ICS in Windows (but you may never have noticed it).

Any time you route through software (rather than hardware) you incur a great deal of overhead that will slow the shared connection down.

Even with the availability of ICS in Windows, good connections are best achieved through a hardware router and I would recommend against using ICS.

---

### Post by jirayam on 2010-03-11
> **marshmallow1304 said:**
> Hope I'm not too late.  If you're using 9.10, you can use the network config tool to share internet.  System->Preferences->Network Connections.  Select the connection you want to share, click Edit.  On the IPv4 Settings tab, change Method to "Shared to other computers".Thanks, mm.

I tried that first, and it doesn't work in my machine.

I tried via Firestarter and I get an error message indicating the firewall can't start.

I'm trying again, with more peace of mind than I had in the past days.

Will let you all know.

---

### Post by jirayam on 2010-03-11
Thanks QIII.

It is a dedicated server, so no issues re local user performance of the server machine.

It is a dual PIII 1GHz machine.

BTW, I've noticed that Ubuntu uses the processors more evenly, and it pushes them more than XP. I may be wrong.

> **QIII said:**
> You can share your internet connection as above.

But be aware that you will suffer some of the same performance degradation on your client machines as you would with ICS in Windows (but you may never have noticed it).

Any time you route through software (rather than hardware) you incur a great deal of overhead that will slow the shared connection down.

Even with the availability of ICS in Windows, good connections are best achieved through a hardware router and I would recommend against using ICS.

---

### Post by jirayam on 2010-03-16
Guys, thanks for your efforts in supporting me but it is not worth it.

I managed to share a connection but lost it when I restarted the machine.

I'm sure there is a way, but I'm no masochist.

I'm on a middle ground, where I want to do advanced things but I'm no Linux expert, and I don't want to be one. I needed a tool, just that, and this one is not ready for prime time, perhaps not even for reruns.

Thanks again. Back to Windows, with a hardware firewall/router.

Thanks again.

---

### Post by GO%)$@*1 on 2010-03-16
If you just want a local server, just on your network, for FTP, Apache, MySql, you should try LAMPP (XAMPP for Linux, as it's now called). It's at [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

Sorry if I'm wrong, or if this message is totally irrelevant. I'm almost asleep and I skimmed the whole thing....

---

### Post by GO%)$@*1 on 2010-03-16
Instead of using firestarter, you could use ufw. I don't know if it'll suit your needs, but it works (as far as I know).

```
sudo apt-get install ufw
sudo ufw enable
sudo ufw status
man ufw
```

---

### Post by jirayam on 2010-03-18
> **kuyanatan said:**
> Instead of using firestarter, you could use ufw. I don't know if it'll suit your needs, but it works (as far as I know).

```
sudo apt-get install ufw
sudo ufw enable
sudo ufw status
man ufw
```Many thanks, K.

If that's all there is to do, it didn't work either.

Maybe we can go step by step.

My first issue is that most of the time, I lose the Internet connection when I start the internal connection. More clearly, I think that once I start the internal connection, ubuntu drops the real one and tries to use the internal for internet access.

Second, the names of the network connections are not consistent. I have two NICs but I have three "ethx" connections, 0, 1 and 2.

How can I reset either the names or the whole networking thing, and start anew.

Thanks in advance.

---

### Post by jirayam on 2010-03-19
Wel, I reached a point where the ubuntu machine even refuses a manual IP address for the internal NIC.

Bye, guys.

---

