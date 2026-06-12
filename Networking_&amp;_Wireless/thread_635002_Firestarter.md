---
title: "Firestarter"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by oxman on 2007-12-08
I've been noticing something very peculiar with the Ubuntu forums. 
Recently and all of a sudden I have been unable to access the forums!!! This was especially frustrating because I have been desperately trying to get drupal to work on my ubuntu lamp set up.
So this morning I decided to turn off the Firestarter firewall to see if I could access the forums. Low and behold, here I am.
What's the deal with that? When I turn the firewall off data begins transferring. From where and to where is anyones guess. If I turn the firewall back on in the midst of a transfer data out ceases and data in is reduced to a trickle. I do not like this behavior and would like to know why my access to the forums is limited when the firewall is up.
Any help is appreciated.

---

### Post by rune0077 on 2007-12-08
Is it only to this forum, or are you having trouble accessing other webpages as well?

---

### Post by oxman on 2007-12-08
Most other web sites I can easily access with the firewall on. There have been a couple of others that I have not been able to access but very few.

Any ideas?

I notice that [http://help.ubuntu.com](http://help.ubuntu.com) was  blocked also.

---

### Post by rune0077 on 2007-12-08
Don't know. Have you checked under the outbound policies to make sure you have not accidentally restricted outbound traffic (either as a whole or to some servers)?

---

### Post by oxman on 2007-12-08
I have not messed with firestarter since it has been installed. It just bugs me that there's traffic (even on a small scale) going on that I can not monitor to find who and what. Not even the network tools show anything. 
The only variable that is really new is that my ISP has switched from USPOPS to GlobalPOPS for bandwidth.

permissive outbound

---

### Post by rune0077 on 2007-12-08
Weird. I have no idea what could cause that then. Sorry :confused:

---

### Post by Ebuntor on 2007-12-08
In Firestarter under the *Policy* tab while selecting the *Inbound traffic policy* do you see any websites listed? 

As far as I know that's the only way Firestarter can block specific websites.

---

### Post by Vadi on 2007-12-08
I was getting iffiness with firestarter too. I didn't tinker with it at all either. I just don't launch it at all now.

It does give some warnings that it failed or start or somesuch sometimes during boot (when I manage to see it).

---

### Post by oxman on 2007-12-08
Thanks for the replies. 

No there are no sites listed to be blocked with firestarter. At least I have been able to pin point where the weirdness was coming from. I was in the process of creating a giant tin foil hat when I discovered the source of the problem. Nice to know that it does block outgoing data when it is on but what a pain to mess with.

I did do a trace route to the ubuntu forums. Watched it go through half a dozen relays then make contact to canonical. waited.... then a series of "no reply" messages and a break. So there was definitely a ping to the ubuntu server but then a rejection.

I'm in the process of setting up drupal on my lamp server and firestarter will definitely be turned off for the project. 

If anyone does come across any information. Please do post it. I'm subscribed to this thread.

---

### Post by rune0077 on 2007-12-08
Well have you tried just reinstalling the darn mess? It probably won't do much good since Firestarter isn't really a firewall but just a frontend to the one that ships with Ubuntu (think its called iptables, not sure though).

---

### Post by oxman on 2007-12-09
Funny thing about that is that it is pushing me over the edge to do an upgrade to Feisty or Gutsy. So I am hesitant to mess with it until then. It is just one in a series of issues pointing me to an upgrade. Ugh! Busy, busy, busy...

---

### Post by bw44 on 2007-12-11
> **rune0077 said:**
> Well have you tried just reinstalling the darn mess? It probably won't do much good since Firestarter isn't really a firewall but just a frontend to the one that ships with Ubuntu (think its called iptables, not sure though).

I've got a question outstanding  about firestarter on another thread ([http://ubuntuforums.org/showthread.php?t=33615](http://ubuntuforums.org/showthread.php?t=33615)). But I found your comment above which sort of confirms my understanding (that firestarter is a front-end to "the" firewall)  But how do you access the Ubuntu firewall without firestarter?

Thanks.

---

### Post by Oceola on 2007-12-11
I'm running Firestarter under Gutsy and have only experienced the package closing at times. Usually it occurs during a page change where there's a lot of "Google" ad or google-analytic traffic. At least it appears that way. It quit a couple of times while typing this.
I used Firestarter with Hoary and Breezy, it didn't quit like this and there seems to be some changes in the Policy tab. There should be an inbound deny but it seems to be only a set "allow" rule.
Outbound still has the opposite options. I know I don't like the fact it turns off without any apparent cause or warning at times.
Previously I couldn't access some of the repositories with Breezy if Firestarter was on. Once it was off, no issues. That does not seem to be the case now and all repositories seem to open properly when it's on.
Most inbounds can be stopped, if identified, in the hosts.deny files if you installed the tcpd package.
You can use a combination of iptraf and netools to identify most of the intrusive urls or the IP. In some cases they seem to be reversed as a simple form of mask. Context/syntax is in Yelp for hosts.allow and deny, just do a host.deny search.

---

### Post by rune0077 on 2007-12-11
> **Oceola said:**
> I'm running Firestarter under Gutsy and have only experienced the package closing at times. Usually it occurs during a page change where there's a lot of "Google" ad or google-analytic traffic. At least it appears that way. It quit a couple of times while typing this.
I used Firestarter with Hoary and Breezy, it didn't quit like this and there seems to be some changes in the Policy tab. There should be an inbound deny but it seems to be only a set "allow" rule.
Outbound still has the opposite options. I know I don't like the fact it turns off without any apparent cause or warning at times.
Previously I couldn't access some of the repositories with Breezy if Firestarter was on. Once it was off, no issues. That does not seem to be the case now and all repositories seem to open properly when it's on.
Most inbounds can be stopped, if identified, in the hosts.deny files if you installed the tcpd package.
You can use a combination of iptraf and netools to identify most of the intrusive urls or the IP. In some cases they seem to be reversed as a simple form of mask. Context/syntax is in Yelp for hosts.allow and deny, just do a host.deny search.

Have you tried checking under System Monitor to make sure it is actually turned off? I've experienced that Firestarter appeared to crash (the icon in the systray disappeared), but the process was still running and doing its job anyway.

---

### Post by rune0077 on 2007-12-11
> **bw44 said:**
> I've got a question outstanding  about firestarter on another thread ([http://ubuntuforums.org/showthread.php?t=33615](http://ubuntuforums.org/showthread.php?t=33615)). But I found your comment above which sort of confirms my understanding (that firestarter is a front-end to "the" firewall)  But how do you access the Ubuntu firewall without firestarter?

Thanks.

You need to use the terminal. Type "iptables --h" (minus the quotes) in the terminal to get a list of usable commands.

---

### Post by bw44 on 2007-12-11
> **rune0077 said:**
> You need to use the terminal. Type "iptables --h" (minus the quotes) in the terminal to get a list of usable commands.

Thanks very much.  If I need to manipulate the iptables, I'll probably wimp out and use firestarter -- but it's good to know about the iptables command.

---

### Post by Oceola on 2007-12-13
@Rune0077 - Thanks for the suggestion.
No this goes down completely, does not show in the System Monitor.
When it's on there's a gksu remark with the name firestarter in it.
It seems to occur with page changes.
I've experienced it at a number of different web sites, sometimes more than others. Sometimes it pops off without any indication at all, even without the page change. I almost think it's acting like a timeout of some sorts, closing when inactive?
:confused:

---

### Post by rune0077 on 2007-12-13
> **Oceola said:**
> @Rune0077 - Thanks for the suggestion.
No this goes down completely, does not show in the System Monitor.
When it's on there's a gksu remark with the name firestarter in it.
It seems to occur with page changes.
I've experienced it at a number of different web sites, sometimes more than others. Sometimes it pops off without any indication at all, even without the page change. I almost think it's acting like a timeout of some sorts, closing when inactive?
:confused:

Weird:confused: I have no idea what that could be.

---

### Post by Oceola on 2007-12-14
Maybe a possible solution.
A memory error showed up in them xsession-errors file.
 there was a never ending list of the character "S"
It looks like a stack overflow of some kind.

I tried to look at the crash report with gedit and managed to open it but it was all garbled after the first few lines. It was near 1.7 MB in size and slow to move to position.
It may be relational to the signals from the screensaver software and Firestarter, since messages about that showed up as well. It could be anything. Also noted was the presence of hits against the 1026, 1027, and 1028 ports from various IPs on the Shaw Cable network and some Mainland Chinese government sites going after ports in the 7000 to 8000 range plus some administrative port hits. Most of these were noted as blocked. 
It may also have been some form of actual access through Firestarter itself which caused the closure. Maybe something with google analytics when performing a page change where it's laid in more intensely for security or auditing.

---

### Post by oxman on 2007-12-15
Curioser and curioser. As soon as I turn firestarter on all data transfer from the forums stops. Turn the app off and we're good again. This is on Dapper BTW.

---

### Post by Oceola on 2007-12-17
@Oxman - You should try the repositories. I ran into some issues with Firestarter and a couple of the Ubuntu repositories with Breezy and with Dapper 6.06 LTS. In one case if the Community repo would open some of the main would fail. If Firestarter was on there were some other repo load failures, I don't remember which ones. Once you turned off Firestarter the repos normalized and loaded. Mostly this was with Breezy. No such issues with Gutsy except the timeout/close. I did have one event close where the gksu comment with Firestarter stayed afterwards but was not at a repository.

---

### Post by oxman on 2007-12-17
Yes, I was getting the same behavior when ever I did anything with synaptic also. The more I observe what is going on, the more I am convinced that some form of data mining is going on. It's as though firestarter is blocking traffic from the computer to external sites. That's all a just a hunch though. Network tools aren't telling me much.

---

### Post by Oceola on 2007-12-18
I was using iptraf and network tools in conjunction with firestarter. The IP identification through Network tools and iptraf is OK but in some cases I think Bidi applied (bi-directional) to some servers due to languages and only got a clean identifier from lookup, who is or trace when reversing the numerical IP of what was shown either in iptraf or nettools. Sort of a simple masking though some may think it absurd.
Also Firestarter seems to have changed a little from Breezy in that it doesn't seem to read as incoming and outgoing blocking but more just hiding the signals. It seems to me you have to use the hosts.deny for blocking but it works secondary to the hosts.allow and if the ip or url is wrong either from the actual or by syntax nothing gets blocked.
You can get a .pdf copy of the latest instructions from the Firestarter site and they've been updated as of 2007. Previous issues with the repositories may have been a masked secondary or auxiliary server from canonical through a redirect causing the issue. 

There were some previous warnings on the web about some issues with both iptraf and Firestarter.

---

### Post by Oceola on 2008-01-28
Update:
UDP signals on improperly detected Primary and Secondary DNS seem to be the culprit closing down Fire starter. This is relative to a failed Network Manager which detects the UDP signals and uses them instead of the designated Primary and Secondary DNS. Disabling "Networking" with the network Manager only partially worked as the new UDP signal would pick up and write the improper Primary and secondary to resolv.conf.

Removing the Network Manager and then using a standard dial up utility and setup will only partially resolve the issue. You have to find all "resolv.conf" files and Old ISP files and re-edit to your dial up ISP's Primary and Secondary DNS. Firestarter doesn't close after these issues have been dealt with and you can block unwanted IPs and port assaults.

This is purely theory at this point but it seems to resolve the issues with Firewall closures:)

---

### Post by K.Mandla on 2008-01-28
Moved to Networking and Wireless.

---

