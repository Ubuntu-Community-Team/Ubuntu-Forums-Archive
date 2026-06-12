---
title: "no internet access"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by mgdwcb on 2009-01-08
Hello,
I do a lot of my work online but since I had a Trojan on Windows have decided to switch to Linux. I have just installed ubuntu but cannont access the internet.  But I can access it with live DVDs of Knoppix and gentoo - they seem to automomatically detect my internet setting.  Is there any way to see what the other live DVDs detect and use those settings in ubuntu? 

I am not very PC literate so any help will be appreciated.

thanks

---

### Post by RobsterUK on 2009-01-08
Welcome to the forums and the land of Ubuntu.

First of all, what kind of setup do you have? Are you trying to connect using wireless or a network cable?

Also, which version of Ubuntu have you installed?

---

### Post by mgdwcb on 2009-01-08
Thanks for your reply.

i have a broadband wire connection in the UK with Btitish Telecom.

---

### Post by superprash2003 on 2009-01-08
go to the terminal(applications->accessories->terminal) and type ifconfig and post output here

---

### Post by Law506 on 2009-01-08
This was a suggestion I made in another post located here [http://ubuntuforums.org/showthread.php?t=1012937]("http://ubuntuforums.org/showthread.php?t=1012937") and it helped a few people.  Dunno if this is your problem quite yet.


2 things you might want to check.

1. Quick simple thing to check as well, did this my first time.

Up in the corner where it shows the network icon, left click on it and it should drop down a menu and if I am correct, you should see something like Auto eth0. If there isn't a dot next to it then that means it isn't selected and it won't connect.

Try clicking it and see what happens.

2. Another thing to check, this also happened to me.

On your windows side go to Device Manager and find your network card and right click and go to properties. Go over to the Advanced Tab and you should see a selection for Wake On Settings in the Properties box. To the side of it you should see a drop down menu and if this is disabled you need to change it to one of the other selections. I am at work right now and my XP computer is set to "Wake On Magic & Directed". I dual boot at my house which is turned off.

Hopefully some of this helps.

---

### Post by albinootje on 2009-01-08
> **mgdwcb said:**
> But I can access it with live DVDs of Knoppix and gentoo - they seem to automomatically detect my internet setting.  Is there any way to see what the other live DVDs detect and use those settings in ubuntu? 

Which Knoppix version did you use ? A recent one ?
Can you post the output of the following in a terminal :
```

lshw -c network
lspci
ifconfig -a
route -n
cat /etc/resolv.conf

```
Thanks.

---

### Post by mgdwcb on 2009-01-08
ok thanks, I'll check these replies and get back asap. I have to reboot to live dvd every time I post online.:(

---

### Post by kestrel1 on 2009-01-08
The top command will not work correctly, it should read```
sudo lshw -C network
```

---

### Post by albinootje on 2009-01-08
> **kestrel1 said:**
> The top command will not work correctly, it should read```
sudo lshw -C network
```

Did you try it yourself before posting this comment ?
It does work fine.

However, you need sudo for :
```

lshw -c disk

```
Compare the result with :
```

sudo lshw -c disk

```

---

### Post by mgdwcb on 2009-01-08
sorry, Im out of my depth with this. I was impressed by how all the Linux live CDs just accesses the internet. I just need a reliable internet access on an OS on my hard drive. I don't understand any of the terminal scripts and can't make head nor tail of the network connections. Maybe I shoud try another distributor / Linux verson.

---

### Post by ibizatunes on 2009-01-08
Copy and paste (each command separately) in application > accessories > terminal and see what results it return

Are you using ubuntu 8.04 or 8.10 > 8.10 has better wireless support

---

### Post by ugm6hr on 2009-01-08
> **mgdwcb said:**
> sorry, Im out of my depth with this. I was impressed by how all the Linux live CDs just accesses the internet. I just need a reliable internet access on an OS on my hard drive. I don't understand any of the terminal scripts and can't make head nor tail of the network connections. Maybe I shoud try another distributor / Linux verson.

Did you try the Ubuntu LiveCD?  How did you install Ubuntu?  Which version did you use?

What specifications does your computer have?  What kind of modem do you use for BT (router or USB modem)?

Just stay on a LiveCD while we get you to give us necessary information from these commands.  Once we have enough, we can try and work out why it isn't behaving in Ubuntu.

We need you to copy and paste the responses from these commands here to help.

```
lspci
lshw -class network
ifconfig
```

PS: This is useful to read about getting help here: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

---

### Post by kestrel1 on 2009-01-08
> **albinootje said:**
> Did you try it yourself before posting this comment ?
It does work fine.

However, you need sudo for :
```

lshw -c disk

```
Compare the result with :
```

sudo lshw -c disk

```
Yes I have tried it & I got an error. No there where no typo's as I copied & pasted.
However, just tried it again & it works fine, go figure.
Didn't mean to step on anyone's toes guys.

---

### Post by handydan918 on 2009-01-08
Is this a wireless or wired connection? If you have tried other distros, and found some that just work on your box, sure, why not use one of them?

I use Mepis, and have for years. Can't praise it enough. One of the easiest, noob friendliest distros around.

---

### Post by mgdwcb on 2009-01-11
ok I've calmed down now and getting to like ubuntu. I successfully pinged my IP address in Network Tools, with no errors and the network manager seemed to think that I was "online". But..no browser worked and I could not download updates to ubuntu. I have been working in GUI and made screenshots of all the settings.  I noticed that the Multicast is disabled. Could that be the problem?

---

### Post by mgdwcb on 2009-01-11
ok I've calmed down now and getting to like ubuntu. I successfuly pinged my IP address with no errors, and the network manager showed I was "online" but no browser worked and I could not download updates (error message as if I was not connected). I noticed that "Multicast" was disabled. Should this be enabled?

---

