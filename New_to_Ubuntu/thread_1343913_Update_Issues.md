---
title: "Update Issues"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by DaveAB6 on 2009-12-02
Hi, 

      Yes I'm a noob, however I'd like to get some help with an issue I'm having.  I'm not entirely sure if others are having this issue, however here goes:
I was using 9.04 without too many issues, but when I upgraded to 9.10 I could no longer achieve updates, or add software. I reverted back to 9.04 and was fine until the latest updates for 9.04 had me reboot and then the updates no longer worked... again.  At this point, I decided to do a fresh install using the 9.10 Live CD and yet again I was receiving an error for updates.  Command line entries give the same results.  

The error is as follows:

                        Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  Cannot initiate the connection to [us.archive.ubuntu.com:80]("http://us.archive.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)  
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  Cannot initiate the connection to [security.ubuntu.com:80]("http://security.ubuntu.com/") (0.0.0.10). - connect (22: Invalid argument)
 
 

Now, before you say "Just connect to the internet" It is, at least partially. I can get to Google, and a few various other sites, but not all.  Even Ubuntu's site is questionable for connectivity.  I thought maybe an IPv4 vs. IPv6 issue but I'm still just not sure.  Any help would be greatly appreciated.

---

### Post by QIII on 2009-12-02
Using the nav bar in your browser, are you able to navigate to 

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

---

### Post by DaveAB6 on 2009-12-02
I'm not entirely sure, I know I wasn't able to get to the forum this morning before I left for work. But I will check this evening when I get home.  I'll update you as soon as I'm able.  thanks for the interest and help in advance.

---

### Post by QIII on 2009-12-02
If you get a chance, could you tell me a little bit about how you connect?

Do you have high-speed?  What kind of modem?  Do you have a router inside the modem?

If you use Firefox, could you type 

```
about:config
```

in the nav bar, search for "ipv6" and make sure it is disabled?

If you are using FF, please try to get to lovinglinux' great tutorial for troubleshooting and optimization at 

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

I'm at work and can only check in once and a while, so I might not get right back to you.

---

### Post by slakkie on 2009-12-02
Looks like you are using a proxy or some sort. Please check this.

---

### Post by NoaHall on 2009-12-02
Hm. Could you also post the output of ```
 cat /etc/apt/sources.list
```?

---

### Post by DaveAB6 on 2009-12-02
Absolutely, I'll gladly check and try all suggested when I get home this evening.  Thanks again in advance for the help/suggestions

---

### Post by stoogiebuncho on 2009-12-02
I'll just jump in here and add that my Mom is also effected by this bug or whatever it is.  She has been getting these connection errors for about a week now and has been unable to update her system.  She also can't connect to ubuntu's home page, or to these forums.

She has two machines.  One is a desktop, and it IS connected to the internet through a proxy (dansguardian).  Her laptop, however, has a direct connection to the internet via their wireless router.  Both are having problems connecting, though the rest of the internet seems to work normally.

We've tried changing the server in "Software Sources" (Server for the United States, Server for Canada, Main Server), but none of them work.

Any suggestions?

---

### Post by sandyd on 2009-12-02
> **stoogiebuncho said:**
> I'll just jump in here and add that my Mom is also effected by this bug or whatever it is.  She has been getting these connection errors for about a week now and has been unable to update her system.  She also can't connect to ubuntu's home page, or to these forums.

She has two machines.  One is a desktop, and it IS connected to the internet through a proxy (dansguardian).  Her laptop, however, has a direct connection to the internet via their wireless router.  Both are having problems connecting, though the rest of the internet seems to work normally.

We've tried changing the server in "Software Sources" (Server for the United States, Server for Canada, Main Server), but none of them work.

Any suggestions?
both of your ISP's DNS servers having problems resolving domain names (or secretly blocking all of ubuntu's servers O_o). The last time i checked, 0.0.0.10 is not a valid ip address.
in this case, you will want to look at opendns.com

p.s. just curious, what ISP are you guys using.

p.p.s. can you do```

cat /etc/dhcp3/dhclient.conf 
```p.p.s. its easy to get opendns for ubuntu.
on the affected computer, run this.
```

gksudo gedit /etc/dhcp3/dhclient.conf

```replace the entire line that has "prepend domain-name-servers" in it with "prepend domain-name-servers 208.67.222.222, 208.67.220.220;"

---

### Post by stoogiebuncho on 2009-12-02
Thanks.  I'll be out at my parent's place tomorrow and I'll try this and let you know how it goes.  I can't remember which ISP they use but I'll find out.

---

### Post by DaveAB6 on 2009-12-02
Thanks for the info, currently like [stoogiebuncho]("http://ubuntuforums.org/member.php?u=490159")
I'm unable to access the forum from the 9.10 box. I've tried what was suggested, however I've received the same results. I realize I'm new at this and I know I'm missing something so obvious that I'll just kick myself later for it but anyway...
  As for how I'm configured, I've got  a cox cable modem connection through a Blitzz BWA711 router.  The Windows computers on the same connection are able to access all sites just fine, so I fear it's not a matter of being denied access by the ISP.  It's got to be a configuration issue. as for that, why am I able to access Google and do a search with it? 
Again, any further help would be greatly appreciated.
Thanks

[ ]("http://ubuntuforums.org/member.php?u=490159")

---

### Post by DaveAB6 on 2009-12-03
Okay,
I find it amazing that I have achieved the internet again and all seems to be well with my ubuntu box.  Admittedly I have reverted back to 9.04 once again. but that seems the only way the updates and software installations seem to stay operational.  Maybe it has something to do with one of the new dhcp3 updates or maybe restricted drivers available for the network card. I don't know. But I do know that I have a stable 9.04 box now. I guess I just can't run 9.10. Oh well.  
Thanks again for everyones help on this, although I never got the resolution I had hoped for, I appreciate it none the less.

Thank you.

P.S.  I'll leave this thread open, just in case someone has anything further to offer on this subject.  Besides, I really don't feel this was solved.

---

### Post by stoogiebuncho on 2009-12-03
The interesting thing is that my parent's problem magically fixed itself today also.  I went over there ready to switch them to opendns, and as soon as we started the computer, the update manager popped up and started downloading updates.   Weird.

So I haven't a clue as to what happened.  It's not like the problem could have been fixed by an update, since the problem was that we couldn't download updates.

Their ISP is Speednet, by the way, although it sounds like this may not have been an ISP issue after all.

Oh well, it's working.  Thanks for the advice.

---

### Post by DaveAB6 on 2009-12-06
Okay,

     New turn of events... I went ahead and upgraded to 9.10 to re-attack this problem from yet another angle.  I've taken my Blitzz router out of the equation and plugged directly into the Cable modem.  Viola! everything works exactly like it is supposed to.  Now why is the 9.10 treating my router as if it is a Proxy?  Not entirely sure... but I guess the real question is how to configure the 9.10 correctly so I can keep using my router, because I can't usurp the the cable modem directly all the time and leave all others without means to access the internet via the wireless access point.
    Oh, incidentally, I also installed a wifi card into the 9.10 box and ran into the same issue, and I mean exact. So I guess that means that 9.10 just can't talk through the  Blitzz BWA711.  
     As for now I guess I'll just keep plugging away until I can find a firm solution to this... I'll still take any suggestions on this that I can though.

Thanks again for everything gang, and keep the suggestions coming  I'm willing to try darn near anything, obviously since I've rebuilt the box several times already.

Thanks,

-Dave

---

### Post by DaveAB6 on 2009-12-08
Closing this thread due to no further updates...  Thanks again everyone.  I know it's not officially solved, but I think that it's best to go ahead and close it.

-Dave

---

