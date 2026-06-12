---
title: "[SOLVED] Wireless works for WPA but not WEP"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Sydius on 2008-06-26
I can connect to WPA networks just fine using:

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

But, for some reason, no matter what I try, it doesn't work for WEP.  My coworker is running the same version of Ubuntu, and we copied the settings exactly, but I still can't connect (and he can).  Meanwhile, at home, I can connect just fine to my WPA network, as I can to other WPA networks I've found.

---

### Post by jualin on 2008-06-26
What kind of encryption are you trying to connect to WEP 64 or WEP 128?

---

### Post by Sydius on 2008-06-26
WEP 64, with a hex key

---

### Post by jualin on 2008-06-26
Someone suggested this on the web [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185470/comments/65]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185470/comments/65") Check out the link if changing from WEP 64 to WEP 128 doesn't fix your issue.

---

### Post by Sydius on 2008-06-26
Unfortunately, I cannot switch the network to 128-bit, since it is a large company network and I don't have permission, unless that's not what you meant.

As for the trick on that page, I just tried it (I don't understand what it did, so I just followed the directions exactly), and it didn't fix the problem.

When I try to select the network in the upper-right thing, it will switch to the icon of two gray circles, as if it were connecting, but they never blink green like they do when a connection is working--they stay gray forever, and it eventually (after a very long time) asks me for the password again.

---

### Post by jualin on 2008-06-26
No what I meant was to switch the way that your computer connects to the network WEP 64 to WEP 128 not the changing the Router's options. 
Just a shot in the dark , there is also something called MAC Address Filter in most routers which basically doesn't let anybody connect to the network if they don't have a MAC Address from a list. So maybe your company has not added you to their MAC Address list. 
Also something that you can do is to convert your Wireless Network in your house to WEP and try to connect to it.

---

### Post by Sydius on 2008-06-26
Alright, I'll try changing to WEP when I get home, and see if that makes any difference.  As for the 128 idea, there's only the option for 128/64, and I suppose it chooses which of the two you mean by the length of the key you provide.  I'll also verify that the company doesn't use mac address filtering (I don't think they do).

---

### Post by jualin on 2008-06-26
Ok then try that and tell me how it goes.

---

### Post by Sydius on 2008-07-01
I went home and switched my wireless router from WPA to WEP, and my work laptop could no longer connect under Ubuntu.  I also verified that my workplace does not check MAC addresses.

The same laptop works fine when booted into Windows at work--it can connect to the WEP network.

Also, after following the previous steps on the other site, my eth0 seems to have disappeared, though maybe I just don't know what I'm doing (I haven't done anything except the measures listed in this thread, though).

---

### Post by hamster_billy on 2008-07-01
I couldn't use WEP on my wireless card (never tried WPA) but installed the drivers from here and now it works fine:
[http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download")

The way mine behaved beforehand was as described, with the grey circles appearing to try to connect, but not getting any further than the password prompt. Something it also did, which was solved with these drivers, was that every network appeared as 100% reception.

If this works for you, bear in mind that every time you upgrade your kernel you'll have to reinstall the drivers, so you should keep the source code on your machine. I reckon there'll be a way round this, but I don't know what it is.

---

### Post by jualin on 2008-07-01
I have found on launchpad a bug related to your car and different solutions which solved the problem for some people. Maybe you should try some of those solutions or ask the question there since they are working on getting the card working on Ubuntu 8.04. From what I read 8.04 is the only version that is experiencing this issue. Some people claim that 7.10 doesn't have that problem. This is the [link]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185470"). Hope this helps!

---

### Post by Sydius on 2008-07-01
Before I go back to getting my WEP to work, I think I should get the wired connection to work again.  Is there any way to undo the instructions found here:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185470/comments/65](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185470/comments/65)

I followed them, and I might be able to figure out how to undo them myself, but I fear messing things up even more since I don't understand them.

---

### Post by jualin on 2008-07-01
> 1. sudo modprobe -r iwl3945
   2. create a file named iwl3945 in /etc/modprobe.d
   3. in that file enter the following entries
   alias wlan0 iwl3945
   options iwl3945 disable_hw_scan=1
   4. sudo modprobe iwl3945
   5. sudo ifconfig wlan0 up
I think that editing the file again and deleting the "options iwl3945 disable_hw_scan=1" line should do the trick. Maybe someone else can confirm this. You will have to run > modprobe iwl3945 again, after you do the changes.

---

### Post by Sydius on 2008-07-01
It looks like that made my eth0 come back, thanks.  Now, I'll see about the wireless again.

---

### Post by jualin on 2008-07-01
You are welcome, try what hamster_billy suggested it may work for you.

---

### Post by Sydius on 2008-07-01
Alright, I can confirm that installing the drivers suggested did indeed fix my problem.  Thanks guys!

---

### Post by hamster_billy on 2008-07-01
Glad to know it. :-)

---

### Post by jualin on 2008-07-01
Glad to know it too. It was hamster_billy's solution right? I will make a comment on the launchpad page with hamster's solution. Thank you dude!

---

### Post by Sydius on 2008-07-02
> **jualin said:**
> Glad to know it too. It was hamster_billy's solution right? I will make a comment on the launchpad page with hamster's solution. Thank you dude!

Yes, it was hamster_billy's solution.  The solution also worked for another person (whom I redirected here) over on the Absolute Beginner's forum.

---

### Post by jualin on 2008-07-02
> **Sydius said:**
> Yes, it was hamster_billy's solution.  The solution also worked for another person (whom I redirected here) over on the Absolute Beginner's forum.

Nice one buddy, giving back to the community already, We are proud of you!:)

---

### Post by hamster_billy on 2008-07-02
:-) Spread the word! I found out about it from this forum some while ago.

---

