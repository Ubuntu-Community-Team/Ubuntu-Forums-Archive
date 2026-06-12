---
title: "Network problems after upgrade"
date: 2005-03-26
forum: Networking &amp; Wireless
---

### Post by uggeli on 2005-03-26
I upgrade my system today (26.3.) and all seemed to go well, but after I restart my machine the networking isn't working anymore. How am I supposed to get the fixing new update now when I simple can't connect to net? I'm writing this from xp, can i download some packages from here and burn to cd and install from there to ubuntu?

I know hoary is still beta, but I do hope that after final release there won't come no more upgrades which crash your system someway. In hoary's history there has been quite a lot problems after upgrading, but well as mentioned this is still 'beta'

btw. sorry for little bit frushtration here, it's not just that my system doesn't work anymore, but I'm allso in fever.. :|  

Anyway happy easter to all!

---

### Post by wellery on 2005-03-26
I also have the same problem. I just created a new post. I've also got no idea what to do. I thought it was something I did to stuff it up. I then re-installed and had the same problem. It seems that one of the updates release today has stuffed internet access in hoary.

---

### Post by arctic on 2005-03-26
[QUOTE=uggeli]I upgrade my system today (26.3.) and all seemed to go well, but after I restart my machine the networking isn't working anymore. How am I supposed to get the fixing new update now when I simple can't connect to net? I'm writing this from xp, can i download some packages from here and burn to cd and install from there to ubuntu?

I know hoary is still beta, but I do hope that after final release there won't come no more upgrades which crash your system someway. In hoary's history there has been quite a lot problems after upgrading, but well as mentioned this is still 'beta'

btw. sorry for little bit frushtration here, it's not just that my system doesn't work anymore, but I'm allso in fever.. :|  

Anyway happy easter to all![/QUOTE]
first of all it would be nice if you give any indication of what kind of network you are running. don't expect to get any useful help without giving us proper information. ;)

and: if you are not able to fix things like these, i highly recommend NOT to use test-versions of distros. this saves you a lot of frustration.

there is a reason why horay is still listed as "preview". it should only be used by those who are able to fix stuff themselves and do extensive bug-testing for the final release = experienced linux users. if you are not able to hack your way through bugs and know how to modify scripts, then you are definitely not a veteran user and should stick ONLY to what is known and well tested (=4.10 warty).

better luck next time :D

---

### Post by joepotter on 2005-03-26
[QUOTE=uggeli]I upgrade my system today (26.3.) and all seemed to go well, but after I restart my machine the networking isn't working anymore. How am I supposed to get the fixing new update now when I simple can't connect to net? I'm writing this from xp, can i download some packages from here and burn to cd and install from there to ubuntu?

I know hoary is still beta, but I do hope that after final release there won't come no more upgrades which crash your system someway. In hoary's history there has been quite a lot problems after upgrading, but well as mentioned this is still 'beta'

btw. sorry for little bit frushtration here, it's not just that my system doesn't work anymore, but I'm allso in fever.. :|  

Anyway happy easter to all![/QUOTE]

Hi,

I always run at least one little "spare" distro on my hard drive to deal with days when I bork up the bootloader or the network. I also keep a live CD around for really bad days.

I read on the mail list that the dhcp3-client in the last update was bad. It has been fixed now, but you need to get on-line to get the latest dhcp3-client; a problem, eh?

You could download the .deb in windows and then boot into Ubuntu and mount the proper partition and grab said .deb for install by dpkg.

You could just up and configure your network "static" rather than dynamic till you do the update. If you are behind a router like me that would be dead easy. If you are connected directly to a cable modem, you might need to find out the IP in windows first and then use that till you can grab the .deb.

You do have choices.

I hope that helps.

---

### Post by joepotter on 2005-03-26
[QUOTE=joepotter]Hi,

I always run at least one little "spare" distro on my hard drive to deal with days when I bork up the bootloader or the network. I also keep a live CD around for really bad days.

I read on the mail list that the dhcp3-client in the last update was bad. It has been fixed now, but you need to get on-line to get the latest dhcp3-client; a problem, eh?

You could download the .deb in windows and then boot into Ubuntu and mount the proper partition and grab said .deb for install by dpkg.

You could just up and configure your network "static" rather than dynamic till you do the update. If you are behind a router like me that would be dead easy. If you are connected directly to a cable modem, you might need to find out the IP in windows first and then use that till you can grab the .deb.

You do have choices.

I hope that helps.[/QUOTE]


Adding more here. I saw this on the e-mail list. It looks promising.

"After the upgrade, I could not connect anymore; I have a nonstandard
network config (using ifplugd) but I would guess all dhcp users could be
effected.

When I ran "sudo ifdown eth0; sudo ifup eth0", I got a very helpful
error message telling me the problem:

sit0: unknown hardware address type 776
/etc/dhcp3/dhclient.conf line 21: expecting semicolon.
        netbios-name-servers, netbios-scope interface-mtu;
                                            ^

Adding a comma between netbios-scope and interface-mtu fixed it. (I used
a comma, contrary to the error message that says "semicolon", since all
the other entries on this line are already separated with commas -
probably an error in the error message  :) "

---

### Post by joepotter on 2005-03-26
[QUOTE=joepotter]Adding more here. I saw this on the e-mail list. It looks promising.

"After the upgrade, I could not connect anymore; I have a nonstandard
network config (using ifplugd) but I would guess all dhcp users could be
effected.

When I ran "sudo ifdown eth0; sudo ifup eth0", I got a very helpful
error message telling me the problem:

sit0: unknown hardware address type 776
/etc/dhcp3/dhclient.conf line 21: expecting semicolon.
        netbios-name-servers, netbios-scope interface-mtu;
                                            ^

Adding a comma between netbios-scope and interface-mtu fixed it. (I used
a comma, contrary to the error message that says "semicolon", since all
the other entries on this line are already separated with commas -
probably an error in the error message  :) "[/QUOTE]


I just did a "dist-upgrade" and it broke networking just as this thread indicated. The fix of adding a comma worked perfectly.

To the original poster ---> thanks, I found an easy way before it happened to me!

:-)

---

### Post by uggeli on 2005-03-26
@artic

Maybe I wrote something wrong, I'm not so good at english.. I mean nothing special network like lan in home or something, just my internet connection, which is dsl using dhcp. Oh and yeas you're right that newbies maybe shouldn't use 'beta' versions, but in other hand this is good way to learn, when you have to fix something. And don't get me wrong when I said I'm little frustration, cause in XP I'm much more fruchtrationed.. :D

@joepotter

I was trying to find deb of that dhcp3-client and I found this page:
[http://higgs.djpig.de/ubuntu/www/hoary/net/dhcp3-client](http://higgs.djpig.de/ubuntu/www/hoary/net/dhcp3-client)
It's just that when trying to install that it gives warning about downgrading and some errors, don't remember what those were, will check that again later. Anyway after booting system things were not working and apt-get istall -f puts back the newer version (guess it wont remove it in any point cause it can't install that new package from net. Do you know where to get newest deb?



Edit: joepotter was faster.. :) Will try that fix now


Edit2: That comma really solved problem, thanks a lot joepotter! The reason why I was trying that deb before that 'comma' was that my english is so rust that I didn't know for sure which mark is comma! (,) :D

---

### Post by joepotter on 2005-03-27
[QUOTE=uggeli]
Edit2: That comma really solved problem, thanks a lot joepotter! The reason why I was trying that deb before that 'comma' was that my english is so rust that I didn't know for sure which mark is comma! (,) :D[/QUOTE]

Glad to hear you have the problem fixed. I saw the fix on the mail list; this has saved me several times. Perhaps you should subscribe to the list and check it before big upgrades.

I use the filters of Mozilla-Thunderbird to handle the high volume of posts to the lists (plus a few others) and it works well.

By the way, our little school had a team of interns from Finland a couple of years ago. Great bunch they were, and they spoke English better than we natives.

---

