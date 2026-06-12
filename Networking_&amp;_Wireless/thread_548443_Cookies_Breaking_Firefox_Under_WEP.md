---
title: "Cookies Breaking Firefox Under WEP"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by RuDeE on 2007-09-11
I have searched around and read many threads on this forum, but none seem to match my exact circumstance. 

I'm running a g3 ibook wireless over a WEP secured network. The problem is: when i try to go to sites that use cookies Firefox cannot load the page. Pages just sit in endless purgatory waiting to load. I can access sites like, wikipedia, google's main search page, etc. I cannot access pages like gmail, myspace, or even this very forum. 

Now, if i uncheck allow cookies in firefox's preferences I am able to access the main page of all the sites listed above with the exception of gmail. I'm even able to log in under my user name here at this forum, but when i go to search the forums or access any of the categories where threads are posted, firefox is once again trapped in limbo. 

I have tried running firefox as root using sudo su - and also just sudo firefox. I still encounter the same problem. 

The interesting thing is that at my folks house on an unsecured wireless network I do not encounter these problems, but under this WEP encryption I am S.O.L. 

Any help would be much appreciated.

---

### Post by noob12 on 2007-09-11
I would look for something else on your network like your DNS or proxy settings.  WEP is completely oblivious to cookies or whatever traffic is flowing.

Some other things to check / try:

Have you installed any plugins?  Try removing those or disabling them.

Try moving aside the .mozilla directory under your home directory and starting from scratch there and seeing if that helps.  If it does, check all the permissions on your original copy.

---

### Post by RuDeE on 2007-09-11
> **noob12 said:**
> I would look for something else on your network like your DNS or proxy settings.  WEP is completely oblivious to cookies or whatever traffic is flowing.

Some other things to check / try:

Have you installed any plugins?  Try removing those or disabling them.

Try moving aside the .mozilla directory under your home directory and starting from scratch there and seeing if that helps.  If it does, check all the permissions on your original copy.

It's not plugins, and it's not the .mozilla directory as I tried running firefox under root and achieved the same effect. I also tried moving the folder just to be on the safe side. 

As far as checking proxy and DNS settings, what exactly would I check? Also, could it be some sort of configuration setting for the wireless router that I could check?

---

### Post by noob12 on 2007-09-11
I would try moving the .mozilla folder especially if you have run as root with HOME or USER environment variables still pointing to yourself/your home dir.

Firefox proxy settings are under Edit | Preferences | Advanced | Network Tab | Connection Settings ...   .   Usually you want Direct Connection in your situation.

Your router could play a part if it supports some sort of site / parental controls and tries to inspect traffic.  Disable that if you have that.  What brand and model of router do you have?

It could also just be flaky DNS service from your ISP.  Try the OpenDNS ones and see if that helps.  This HOWTO has some pointers: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by RuDeE on 2007-09-12
> **noob12 said:**
> I would try moving the .mozilla folder especially if you have run as root with HOME or USER environment variables still pointing to yourself/your home dir.

Firefox proxy settings are under Edit | Preferences | Advanced | Network Tab | Connection Settings ...   .   Usually you want Direct Connection in your situation.

Your router could play a part if it supports some sort of site / parental controls and tries to inspect traffic.  Disable that if you have that.  What brand and model of router do you have?

It could also just be flaky DNS service from your ISP.  Try the OpenDNS ones and see if that helps.  This HOWTO has some pointers: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

I've tried moving the .mozilla folder. No sucess. I have played with the firefox proxy settings. Nada. Checked the routers settings, we have a 2wire gateway series router. There was nothing suspicious there that i noticed. As far as DNS goes... i'm skeptical. I'm on my wifes g4 right now, and she used mac osx. There are no problems with her wireless. I'm going to have a friend of mine come over and play around a bit with my laptop, and if we come up with a solution i will post it. Thanks much noob.

---

### Post by noob12 on 2007-09-12
OK.  I'll be curious to see what you find.  Thanks.

---

### Post by RuDeE on 2007-09-18
The adventure continues!

I had my friend come over today and scour my computer for the source of my wep disabilities. It turns out he was as dumbfounded as my by the whole situation. We have another box upstairs where i am located running ubuntu and a wireless connection with the same dns and proxy settings as my little g3 laptop. the other computer upstairs works, my little ibook does not. so just for kicks, my friend doubled up the dns name server and search options in network manager, and wham! it's working. he checked his gmail right on the spot. satisfied that the problem is solved i take him home. when i return no gmail, etc... again. 

on a side note, we were convinced early on in our examination of the problem that is was the dns servers because of a handy program called wireshark. we had it capture all of the packets when trying to go to the gmail website, and then took a look. dns queries were failing. however, since i've returned home, i cannot reproduce the result. dns seems to be working. my resolve.comp looks exactly the same as the other computer upstairs. i'm pretty bummed. is there anywhere else i can look for dns settings, or are there any other suggestions. 

also, i burned a ubuntu 7.04 ppc live cd just to test whether the problem was with some file or setting on my hard drive.  it is not. the live cd also could connect to site which don't send out cookies, but for sites like gmail, myspace, etc... no luck. i wonder if there is a problem with a script somewhere in the ppc version of ubuntu when it comes to wep? 

anyway, a long story and a lot of information. i hope someone has an idea or two. they are much appreciated.

Rudy

---

### Post by RuDeE on 2007-09-25
Soley for Noob12.

By forsaking the GUI and using ifconfig, I've got it running. The problem was not proxy or DNS, just the classic Network Manager ruining things. 

Solution: Set the device to roaming mode in Network Manager. This removes eth1 from /etc/network/interfaces. Add it back in. Use iwconfig to set the essid and hex key. Run /etc/init.d/networking restart. Bam! It works. 

P.S. Though I have nothing listed in the DNS and Server section under network manager. /etc/resolv.conf still displays my search and nameserver information correctly. I'm not sure what file would be setting that up. 

Nevertheless, everything is up and running, and I am satisfied. 

Rudy

---

