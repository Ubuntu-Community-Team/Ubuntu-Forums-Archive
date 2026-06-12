---
title: "Unable to access certain websites from Ubuntu"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by DemianDemerzel on 2011-05-14
Hi,

I downloaded and installed Ubuntu 11.04 (Natty Narwhal) only a few hours ago and in the process I deleted my old operating system Windows 7.

Now what's happening is that I am unable to access some websites including [http://www.hotmail.com/](http://www.hotmail.com/), [http://www.theatlantic.com/](http://www.theatlantic.com/) and [http://www.tvfanatic.com/](http://www.tvfanatic.com/) .

When I type in a  URL in the browser and press ENTER, all I get is the Firefox waiting sign or a rotating ring. The wait is endless. 

In contrast, I have no problem visiting other websites like [http://www.project-syndicate.org/](http://www.project-syndicate.org/) or [http://www.wikipedia.org/](http://www.wikipedia.org/) and [http://www.bbc.co.uk](http://www.bbc.co.uk) .

I am a non-technical guy. I was moved by the Ubuntu philosophy and decided to get rid of Windows so there is no going back. So I would be grateful to you if you could suggest what to do.

Thank you for reading and caring to reply.

---

### Post by 00arthuryu on 2011-05-14
This sounds more like a problem with the website / your internet provider, not Ubuntu. I use hotmail everyday and have had no problems. If needed, try pinging the hotmail site or type in the IP address directly. Your host might be re-routing all [www.hotmail.com](www.hotmail.com) to a different IP.

Hope this helps

---

### Post by DemianDemerzel on 2011-05-14
Hi Arthuryu,

A problem with the website. It might be. But don't you think it's unlikely to have the same problem with around half a dozen websites simultaneously. 

Add these two to the previous list:

[http://www.dw-world.de/](http://www.dw-world.de/)
[http://foreignpolicy.com/](http://foreignpolicy.com/)

Thank you for your last reply.

DE

---

### Post by jtarin on 2011-05-14
Open a terminal and type ```
gksudo gedit /etc/hosts
``` and post a copy.

---

### Post by DemianDemerzel on 2011-05-14
Hi JTarin,

I apologise but I don't know what does a '*terminal*' mean?

I forgot to mention in the previous post but I also don't know what does '*pinging a website*' mean?

Thank you for taking out your precious time to reply.

---

### Post by jtarin on 2011-05-14
> **DemianDemerzel said:**
> Hi JTarin,

I apologise but I don't know what does a '*terminal*' mean?

I forgot to mention in the previous post but I also don't know what does '*pinging a website*' mean?

Thank you for taking out your precious time to reply.OK...your using Natty so I don't kbnowif this will work...try the ALT + F2 keys. There should be a dialogue pop-up on your desktop. In that dialogue type gnome-terminal. The terminal will open and then you can proceed as directed in my last post.

---

### Post by DemianDemerzel on 2011-05-14
Hi JTarin,

This is what I get after doing as directed

==========================================================

127.0.0.1    localhost
127.0.1.1    demian-N61PC-M2S

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

==========================================================

What should I do now?

---

### Post by Thewhistlingwind on 2011-05-14
I don't mean to interrupt others in the middle of helping you, but you may in fact just need to switch your user agent. 

([https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)) Not sure if that's the one everyone uses, but something along those lines may be what you need.

---

### Post by jtarin on 2011-05-14
> **DemianDemerzel said:**
> Hi JTarin,

This is what I get after doing as directed

==========================================================

127.0.0.1    localhost
127.0.1.1    demian-N61PC-M2S

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

==========================================================

What should I do now?

Use the same procedure and open /etc/resolv.conf and edit to look like this:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```save...then try to connect.

---

### Post by alphacrucis2 on 2011-05-14
> **Thewhistlingwind said:**
> I don't mean to interrupt others in the middle of helping you, but you may in fact just need to switch your user agent. 

([https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)) Not sure if that's the one everyone uses, but something along those lines may be what you need.

I don't think user agent has anything to do with it as I can access all the websites he listed just fine and I don't do any user agent tweaking.

Edit. One thing I just thought of. If jtarin's suggestion does not fix the problem, then try this.

Enter the following in the firefox url bar:

```
about:config
```

Firefox will give you a warning. That's ok just click the button that says "I'll be careful I promise"

It will display a text entry field labelled "Filter", type:

```
ipv6
```

That will display one line titled network.dns.disableipv6. If the Value field says false, then double click on it to toggle it to read true. Then just click home and try your websites again.

---

### Post by DemianDemerzel on 2011-05-14
Hello AlphaCrusis,

I did exactly as you said. But the problem is still there.

Let me put it in other words "the websites I've talked about do not load. I appears they will take forever to load and I don't see any webpage. Only the Firefox waiting sign I see." :(

It doesn't seem to be a problem with the internet as I can access other websites including UbuntuForums. 

I am grateful to you for your assistance but I think I will need another solution. That one didn't work.

---

### Post by mick222 on 2011-05-14
Have you installed Ubuntu restricted extras. 
   If Not assuming you are using Natty click the shutdown button choose system settings Open synaptic package manager and search for Ubuntu restricted extras and install.

---

### Post by DemianDemerzel on 2011-05-14
Hi Mick,

Thanks for caring to reply. 

I did install *Ubuntu Restricted Extras* but to no avail. :(

---

### Post by jtarin on 2011-05-14
Have you followed my last post? I didn't see the results.

---

### Post by DemianDemerzel on 2011-05-14
Yes, JTarin.

I did follow the post. Nothing happens when I give the command **/etc/resolv.conf**. 

However, if I remove the dot from the command and write **/etc/resolvconf** I am directed to a new window and then to a new folder.

The folder reads **update-libc.d **and inside I find **avahi-daemon**.

On double clicking on **avahi-daemon**, I'm presented with an option to **RUN **it.

Thanks! :)

---

### Post by mick222 on 2011-05-14
Ok seen this problem ages ago this might help In the address bar type
about:config search for general if general user agent vendor shows up make sure it's set to firefox and check your local is correct.
 Things have changed a bit in firefox4 but worth a try.
 Also seen a thread saying flash could be a problem and to remove it then install chrome or chromium which apparently come with a different flash version ,but not sure about that.

---

### Post by DemianDemerzel on 2011-05-14
I couldn't find the **General User Agent Vendor **option.

I'm using Natty Narhwal and got it installed less than 24 hours ago. 

My previous operating system was Windows 7. It is removed now.

---

### Post by mick222 on 2011-05-14
Sorry i cant be of more help the only other things i can think of are clearing your cache and cookies and disabling ipv6 in the network manager.
 I hope someone comes along with a solution for you got to go now.
 Did you check if general.useragent.locale was set correctly.

---

### Post by DemianDemerzel on 2011-05-14
I read in Connection Information that **ipv6 **is "ignored."

What do you mean by "make sure it's set correctly?"

It reads:

**Preference Name**: general.useragent.locale
**Status**: User Set
**Type**: String
**Value**: en-US 

Is it correct or not?

And don't worry. You tried and that's what matters! :)

---

### Post by scott-ian on 2011-05-14
Does the Internet work off a LiveCD, such as the one you installed your OS off of?

---

### Post by DemianDemerzel on 2011-05-14
Hello Scott,

I believe it worked off the LiveCD. Yes it did. I'm sure. But I don't remember if I opened Hotmail or other websites, that are now giving the problem, then.

I don't have the LiveCD now. A friend has borrowed it.

---

### Post by jtarin on 2011-05-14
> **DemianDemerzel said:**
> Yes, JTarin.

I did follow the post. Nothing happens when I give the command **/etc/resolv.conf**. 

However, if I remove the dot from the command and write **/etc/resolvconf** I am directed to a new window and then to a new folder.

The folder reads **update-libc.d **and inside I find **avahi-daemon**.

On double clicking on **avahi-daemon**, I'm presented with an option to **RUN **it.

Thanks! :)The command is not "/etc/resolv.conf". The command is gksudo gedit /etc/resolv.conf". If you can't find that file then that's the problem.

---

### Post by scott-ian on 2011-05-14
Are you behind a proxy server?  I don't know much about them, but I believe it could be the source of your problem.

---

### Post by jtarin on 2011-05-14
I was going to suggest try a proxy server the destination site might be blocking.

---

### Post by DemianDemerzel on 2011-05-14
I'm sorry JTarin. I didn't understand. 

This is what I get after following the command.

=================================

# Generated by NetworkManager
nameserver 218.248.255.196
nameserver 218.248.255.194

=================================

Should I change it to what you suggest?

---

### Post by Swagman on 2011-05-14
> **DemianDemerzel said:**
> I'm sorry JTarin. I didn't understand. 

This is what I get after following the command.

=================================

# Generated by NetworkManager
nameserver 218.248.255.196
nameserver 218.248.255.194

=================================

Should I change it to what you suggest?


That command on my system  gives..

> # Generated by NetworkManager
nameserver 192.168.0.1

Which is the ip of my router

---

### Post by ClientAlive on 2011-05-14
> **jtarin said:**
> OK...your using Natty so I don't kbnowif this will work...try the ALT + F2 keys. There should be a dialogue pop-up on your desktop. In that dialogue type gnome-terminal. The terminal will open and then you can proceed as directed in my last post.


I used 11.04 Natty Nahrwall from alpha 3 through release. That I could tell, It is not any different with respect to key bindings or command line. Where the difference lies is in some of the navigation in the gui.


> **DemianDemerzel said:**
> I read in Connection Information that **ipv6 **is "ignored."

What do you mean by "make sure it's set correctly?"

It reads:

**Preference Name**: general.useragent.locale
**Status**: User Set
**Type**: String
**Value**: en-US 

Is it correct or not?

And don't worry. You tried and that's what matters! :)


Ipv6 is not something you need to mess with. I'm not entirely familiar with it but I think it is some more advanced way of configuring your connection to your router. Mine is ignored and I think most poeple's is unless they're trying to use remote access or something like that. The only concern would be if it is set up and set up wrong somehow. But don't let it worry you for now.

I read through this string and am not sure anyone has mentioned it yet. You can access your terminal by pressing ctrl+alt+t. You can exit it by typing the word "exit" onto the line in there and pressing enter. If you haven't opened on up yet to check it out go ahead and do that a couple times just to see what it's like. You can also exit the terminal by clicking the x in the corner of the window (just like any other window).

One thing you can do to trouble shoot this is install a different web browser onto the machine and then try to go to those sites with it. You will discover whether it is just firefox that is the problem or if it is something with the system beyond it. I use Opera and it is a stable web browser. You can remove it when you are done if you want but it will help you to get and answer that narrows things down. To do this follow these staps.

Open a terminal widow by pressing ctrl+alt+t

After that enter the following code into the terminal window then press enter.

```
sudo apt-get install opera
```

After you enter that and press enter you will be asked for your password. Go ahead and enter it and then press enter. It will begin to install opera. You may be asked to confirm the installation. If so, just type y on the line and press enter.

Once that is done type "opera" onto the line in the terminal and press enter. This will launch opera and you can use it in the normal way to try to go to those sites.

Please let us know what happens.

If a time comes you want to remove opera you can type the following into the terminal to accomplish it.

```
sudo apt-get remove opera
```

---

### Post by ClientAlive on 2011-05-14
> **DemianDemerzel said:**
> I'm sorry JTarin. I didn't understand. 

This is what I get after following the command.

=================================

# Generated by NetworkManager
nameserver 218.248.255.196
nameserver 218.248.255.194

=================================

Should I change it to what you suggest?


As a side note:

This is what a proxy server is:

[http://en.wikipedia.org/wiki/Proxy_server](http://en.wikipedia.org/wiki/Proxy_server)

Unless a person intentionally sets it up they probably don't have to worry about that. It is a process you have to go through to set it up in the first place.

Let's try the simple and safe solutions first. Ok?

We'll get this brother. Between us here at the forum - we got your back man.


:D

---

### Post by jtarin on 2011-05-14
> **DemianDemerzel said:**
> I'm sorry JTarin. I didn't understand. 

This is what I get after following the command.

=================================

# Generated by NetworkManager
nameserver 218.248.255.196
nameserver 218.248.255.194

=================================

Should I change it to what you suggest?Record those numbers in case you want to change back and then substitute with the ones I posted. If it works we'll make it permanent.
Are you in New Delhi with BSNLNET?

---

### Post by jtarin on 2011-05-14
> **Swagman said:**
> That command on my system  gives..



Which is the ip of my routerAnd your router contains your nameserver information.

---

### Post by ClientAlive on 2011-05-14
> **jtarin said:**
> And your router contains your nameserver information.

Is that why he has two items listed in his output jtarin? Shown in post #25.

---

### Post by DemianDemerzel on 2011-05-14
> **ClientAlive said:**
> 

One thing you can do to trouble shoot this is install a different web  browser onto the machine and then try to go to those sites with it. You  will discover whether it is just firefox that is the problem or if it is  something with the system beyond it. I use Opera and it is a stable web  browser. You can remove it when you are done if you want but it will  help you to get and answer that narrows things down. To do this follow  these staps.

Open a terminal widow by pressing ctrl+alt+t

After that enter the following code into the terminal window then press enter.

```
sudo apt-get install opera
```After you enter that and press  enter you will be asked for your password. Go ahead and enter it and  then press enter. It will begin to install opera. You may be asked to  confirm the installation. If so, just type y on the line and press  enter.

Once that is done type "opera" onto the line in the terminal and press  enter. This will launch opera and you can use it in the normal way to  try to go to those sites.

Please let us know what happens.

If a time comes you want to remove opera you can type the following into the terminal to accomplish it.

```
sudo apt-get remove opera
```

Hi ClientAlive,

This is what I get when I give the command

============================

demian@demian-N61PC-M2S:~$ sudo apt-get install opera
[sudo] password for demian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'opera' has no installation candidate
demian@demian-N61PC-M2S:~$ 

==============================

What should the next step be?

---

### Post by jtarin on 2011-05-14
> **ClientAlive said:**
> Is that why he has two items listed in his output jtarin? Shown in post #25.No

---

### Post by DemianDemerzel on 2011-05-14
> **jtarin said:**
> Record those numbers in case you want to change  back and then substitute with the ones I posted. If it works we'll make  it permanent.
Are you in New Delhi with BSNLNET?

Hey JTarin,

No, I'm not in New Dehli. A couple of hundred kilometers from it. Yes, I do have a BSNL connection. Should I swap the numbers?

---

### Post by ClientAlive on 2011-05-14
> **DemianDemerzel said:**
> Hi ClientAlive,

This is what I get when I give the command

============================

demian@demian-N61PC-M2S:~$ sudo apt-get install opera
[sudo] password for demian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'opera' has no installation candidate
demian@demian-N61PC-M2S:~$ 

==============================

What should the next step be?

Dude. I'm real sorry. I forgot. I think you have to download that from their website. Here's the link:

[http://www.opera.com/download/](http://www.opera.com/download/)

jtarin:

Sorry man. I thought you had to go and this guy wasn't gonna have anyone to help hime. Kinda dumb I know. I'm not familiar w/ proxy stuff but I did notice he has two items listed in his output rather than one and that the ip's aren't identical. Just didn't want to mislead on something I'm not absolutely certain about.

---

### Post by dniMretsaM on 2011-05-14
Why not just install Chromium from the Software Center instead of Opera? It would be less of a hassle in my opinion. Go into the Software Center and search for Chromium. If you want to install it from Terminal, run the following:
```
sudo apt-get install chromium-browser
```

---

### Post by jtarin on 2011-05-14
> **DemianDemerzel said:**
> Hey JTarin,

No, I'm not in New Dehli. A couple of hundred kilometers from it. Yes, I do have a BSNL connection. Should I swap the numbers?
It won't hurt anything. Those are Google public nameservers. Fast and reliable. You can always change back.

---

### Post by Wim Sturkenboom on 2011-05-14
If this is a nameserver issue, you should see in the statusbar of firefox the message 'Looking up .....' for a long time. If that's the case, you're on the right track. If not, I doubt that resolving hostnames is the issue.

---

### Post by DemianDemerzel on 2011-05-14
Hey ClientAlive,

The problems persists in Opera.

> **jtarin said:**
> Use the same procedure and open /etc/resolv.conf and edit to look like this:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```save...then try to connect.

Now I am going to try JTarin's solution. Let's see what happens.

---

### Post by DemianDemerzel on 2011-05-14
Dear JTarin,

I changed the numbers but the problem is still there. :(

---

### Post by ClientAlive on 2011-05-14
> **DemianDemerzel said:**
> Hey ClientAlive,

The problems persists in Opera.



Now I am going to try JTarin's solution. Let's see what happens.


Awesome. We know it isn't anything to do with firefox now; or, more specifically, any web browser. jtarin sound's like he knows what's up w/ this. I'm in the US so maybe a little different than what you guys are talking about. Don't know.

Sorry I couldn't help more. I'm interested to see how this plays out though.

:D

---

### Post by DemianDemerzel on 2011-05-14
I asked the same question to Lernu! users on their [forum]("http://eo.lernu.net/komunikado/forumo/temo.php?t=8992&p=1") and one of them has suggested there could be a problem with the DNS server. What do you think?

---

### Post by ClientAlive on 2011-05-14
> **DemianDemerzel said:**
> I asked the same question to Lernu! users on their [forum]("http://eo.lernu.net/komunikado/forumo/temo.php?t=8992&p=1") and one of them has suggested there could be a problem with the DNS server. What do you think?


It's possible. Are you able to contact your service provider in a way that's convenient enough? They may be able to give you some infomation that would be useful. The only thing I think about though is that you say you can get through to other web sites ok. Another possibility to consider is that maybe certain web sites server have a problem with the kind of intenet service or set up you are using. I would still contact your isp if you can though.

:)

---

### Post by jtarin on 2011-05-14
> **DemianDemerzel said:**
> I asked the same question to Lernu! users on their [forum]("http://eo.lernu.net/komunikado/forumo/temo.php?t=8992&p=1") and one of them has suggested there could be a problem with the DNS server. What do you think?
That's what the /etc/resolv.conf file is for....but I still haven't heard any results from this.

---

### Post by DemianDemerzel on 2011-05-15
> **jtarin said:**
> That's what the /etc/resolv.conf file is for....but I still haven't heard any results from this.

Hi JTarin,

I think I told you and other friends that I did not see any improvement even after swapping the numbers. Didn't I? :)

And, I just noticed the Login page of Hotmail downloads but I'm not able to log in.

No improvement in case of other websites.

---

### Post by wildmanne39 on 2011-05-15
> **DemianDemerzel said:**
> Hi JTarin,

I think I told you and other friends that I did not see any improvement even after swapping the numbers. Didn't I? :)

And, I just noticed the Login page of Hotmail downloads but I'm not able to log in.

No improvement in case of other websites.
That is not just one of those cases were the web site only lets internet explorer connect to it is it? I know I use to click a tab in the previous version of firefox to connect to sites that only accepted explorer.:)

---

### Post by DemianDemerzel on 2011-05-15
> **wildmanne39 said:**
> That is not just one of those cases were the web site only lets internet explorer connect to it is it? I know I use to click a tab in the previous version of firefox to connect to sites that only accepted explorer.:)

Which tab did you use to click?

---

### Post by DemianDemerzel on 2011-05-15
My boss has just advised me to use HideMyAss. It works for The Atlantic  and TV Fanatic but not for Hotmail. Moreover, it seems to me like a  makeshift solution. Any suggestion that fixes the problem once and for  all is welcome.

---

### Post by jtarin on 2011-05-15
> **DemianDemerzel said:**
> My boss has just advised me to use HideMyAss. It works for The Atlantic  and TV Fanatic but not for Hotmail. Moreover, it seems to me like a  makeshift solution. Any suggestion that fixes the problem once and for  all is welcome.Having to use a proxy with only certain sites tells me that these sights have blocked your IP number. You could always write an email to support of any sights your having problems with and give them your ISP name and address range and ask them to unblock.

---

### Post by Wim Sturkenboom on 2011-05-15
[http://38.118.71.170/](http://38.118.71.170/) should give you the same as theatlantic.com
[http://216.87.173.18](http://216.87.173.18) should give you tvfanatic.com

If those are not working, it's definitely not a nameserver issue

---

### Post by karthik.k.nair on 2011-05-15
you ma try using ipadress of the particular website tat u r not able to visit. if u r able to visite using ip address then most probably it is the dns problem

---

### Post by DemianDemerzel on 2011-05-15
> **Wim Sturkenboom said:**
> [http://38.118.71.170/](http://38.118.71.170/) should give you the same as theatlantic.com
[http://216.87.173.18](http://216.87.173.18) should give you tvfanatic.com

If those are not working, it's definitely not a nameserver issue

Which are "those"?

Call it a coincidence or what but after clicking on those two links I now face no problem loading TV Fanatic and The Atlantic. 

The problem persists with Hotmail and Foreign Policy and Deutsche Welle....

What could be behind this *so far inexplicable* problem?

---

### Post by DemianDemerzel on 2011-05-15
> **karthik.k.nair said:**
> you ma try using ipadress of the particular website tat u r not able to visit. if u r able to visite using ip address then most probably it is the dns problem


*Namaste* Karthik,

Assuming that you an expert, I want to tell you that I'm not a technical guy. I am still learning computers. Installing Ubuntu by myself to me was like climbing the Mount Everest. So I ask you - where can I find the IP addresses of the websites in question? :)

---

### Post by jtarin on 2011-05-15
> **DemianDemerzel said:**
> *Namaste* Karthik,

Assuming that you an expert, I want to tell you that I'm not a technical guy. I am still learning computers. Installing Ubuntu by myself to me was like climbing the Mount Everest. So I ask you - where can I find the IP addresses of the websites in question? :)Plenty of places to ge that info on the net....here's one.
[http://www.hcidata.info/host2ip.cgi](http://www.hcidata.info/host2ip.cgi)

---

### Post by DemianDemerzel on 2011-05-15
> **jtarin said:**
> Plenty of places to ge that info on the net....here's one.
[http://www.hcidata.info/host2ip.cgi](http://www.hcidata.info/host2ip.cgi)

Dear JTarin,

Now I have the IP address. What do I do now? Put them in the URL box. It didn't work for me.

---

### Post by scott-ian on 2011-05-15
The IP addresses should work.  If not, there may be another problem.  You didn't type your own IP by accident did you?

---

### Post by DemianDemerzel on 2011-05-15
> **scott-ian said:**
> The IP addresses should work.  If not, there may be another problem.  You didn't type your own IP by accident did you?

Hi Scott!

I just checked and found out that the IP addresses are only not working for websites which give the problem. For other websites, the IP addresses work.

---

### Post by Wim Sturkenboom on 2011-05-15
> **DemianDemerzel said:**
> Which are "those"?

Call it a coincidence or what but after clicking on those two links I now face no problem loading TV Fanatic and The Atlantic. 

The problem persists with Hotmail and Foreign Policy and Deutsche Welle....

What could be behind this *so far inexplicable* problem?
OK, should have been more clear; the links with the IP addresses should work and should give you the sites that I mentioned after them.

> **DemianDemerzel said:**
> Hi Scott!

I just checked and found out that the IP addresses are only not working for websites which give the problem. For other websites, the IP addresses work.
I think your contradicting yourself (for some of them). If you follow the links with the IP addresses that I gave and they worked, they work and your issue is a name server issue for those sites.

You can add entries in */etc/hosts* using an editor (as marked in bold below). It is a workaround and if the IP address of theatlantic.com ever changes, you must remember to check that and update the file /etc/hosts to reflect the new IP address. So I should rather try to solve it another way.
```

127.0.0.1	localhost
127.0.1.1	desktop-01

**38.118.71.170   theatlantic.com**

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by ClientAlive on 2011-05-15
> **DemianDemerzel said:**
> Which are "those"?

Call it a coincidence or what but after clicking on those two links I now face no problem loading TV Fanatic and The Atlantic. 

The problem persists with Hotmail and Foreign Policy and Deutsche Welle....

What could be behind this *so far inexplicable* problem?


I was just reading about a command called traceroute. It traces the route from your computer to the place you put in to go to and tells detailed info on each step of the way as well as general info (at the bottom) about packets sent and recieved and packet loss.

For example:

```
traceroute theatlantic.com
```

OR

```
traceroute hotmail.com
```

I had to install traceroute on my system (Ubuntu 10.04) because it wasn't already there.

```
sudo apt-get install traceroute
```

Here is an excerpt from the book I am reading that talks about it:

> **traceroute**

The traceroute program (some systems use the similar tracepath program
instead) displays a listing of all the &#8220;hops&#8221; network traffic takes to get from the local
system to a specified host. For example, to see the route taken to reach
slashdot.org . . .


Maybe it would help you in the future or with hotmail now.

You can also "ping" a web site from the command line. It will give only the basic info of packets sent packets received packets lost. If you do ping you have to hit ctrl+c to stop it after a few pings or it will just keep going. After stopping it is when the info is shown.

```
ping hotmail.com
```

HTH

---

### Post by Wim Sturkenboom on 2011-05-16
Not behind a ubuntu machine at the moment but a graphical version of traceroute is part of the networking tools in one of the menus.

---

### Post by DemianDemerzel on 2011-05-16
????????????????????

:(

---

### Post by jtarin on 2011-05-16
> **DemianDemerzel said:**
> ????????????????????

:(
Open a terminal and type "gnome-nettool".

---

### Post by DemianDemerzel on 2011-05-16
> **jtarin said:**
> Open a terminal and type "gnome-nettool".

Hi JTarin,

I get a table full of data when I give the command. What next?

---

### Post by jtarin on 2011-05-16
> **DemianDemerzel said:**
> Hi JTarin,

I get a table full of data when I give the command. What next?You need to install "The NET-3 networking toolkit".....look in Synaptic

---

### Post by DemianDemerzel on 2011-05-16
> **jtarin said:**
> You need to install "The NET-3 networking toolkit".....look in Synaptic

Good Morning JTarin,

I just checked and found out that the **NET-3 Networking Toolkit** is already installed.

---

### Post by jtarin on 2011-05-16
Then that command I gave you should bring it up. I don't have 11.04 so I don't know here you can visibly look for it, but mine  is under "Administration" in Gnome.

---

### Post by DemianDemerzel on 2011-05-17
> **jtarin said:**
> Then that command I gave you should bring it up. I don't have 11.04 so I don't know here you can visibly look for it, but mine  is under "Administration" in Gnome.

Okay, I am such a fool! But could you tell me again, which command you are talking about?

Is it ```
gesudo gedit /etc/resolv.conf
```?

---

### Post by ClientAlive on 2011-05-17
Description of -

[https://launchpad.net/ubuntu/natty/+package/net-tools](https://launchpad.net/ubuntu/natty/+package/net-tools)


*Just in case you get bored or can't sleep one night and want to learn a little more about network stuff:

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

[http://www.debian.org/doc/manuals/reference/ch05.en.html](http://www.debian.org/doc/manuals/reference/ch05.en.html)


Sorry I couldn't be of more help man. Hope you get it squared away.

:)

---

### Post by ClientAlive on 2011-05-17
> **Wim Sturkenboom said:**
> Not behind a ubuntu machine at the moment but a graphical version of traceroute is part of the networking tools in one of the menus.


I ran 11.04 for a while. I just couldn't remember where it was until right now. If you click the power button (round icon in the upper right corner of the screen) - at the bottom of that drop down list is something like 'system'. After you click that you get a list of all the stuff in system. I don't recall the exact title where those tools are but it's in there and those names at that location correspond to the names in earlier releases.
-------------------------

Edit: It's called "Network Tools" and might be in a section called "Admistration" or something like that.

That's _if_ you guys are talking about the gui for ping, traceroute, etc.

---

### Post by ClientAlive on 2011-05-17
> **DemianDemerzel said:**
> Which are "those"?

Call it a coincidence or what but after clicking on those two links I now face no problem loading TV Fanatic and The Atlantic. 

The problem persists with Hotmail and Foreign Policy and Deutsche Welle....

What could be behind this *so far inexplicable* problem?


Do you mean that after you clicked those links you could go to those sites in the normal ways after that? Like any other way of getting to them? Or do you mean you have to keep using that link to get to it after that.

---

### Post by jtarin on 2011-05-17
> **DemianDemerzel said:**
> Hi JTarin,

I get a table full of data when I give the command. What next?Open a terminal and type ```
gnome-nettool
```and please post the "data" if it doesn't come up. That data tells us what's wrong. You don't have to post all but put it in code tags.

---

### Post by ClientAlive on 2011-05-17
> **DemianDemerzel said:**
> *Namaste* Karthik,

Assuming that you an expert, I want to tell you that I'm not a technical guy. I am still learning computers. Installing Ubuntu by myself to me was like climbing the Mount Everest. So I ask you - where can I find the IP addresses of the websites in question? :)


If you can find "Network Tools" as described in my above post then click the "Ping" _tab_ - type in the name of the site you want (without the www part); click the "Ping" _button_; and, if things on the computer are working right (maybe not for you right now) it will give you the ip address. The ip address is seen when you click the little plus (+) sign near the bottom of the window. That makes the "details" opens up and the info would be in there.

Here's a picture of mine. I'm running Ubuntu 10.04 (not 11.04) but should be the same for you.
----------------------------------

Edit: What's going on is there are two ways to launch that network tools thing. What jtarin is telling you to do in the terminal is supposed to launch the same thing I'm describing how to get to using the gui.

I think what jtarin is asking you to do is if the network tools doesn't launch when you put his code into the terminal - to post what the terminal does put out. He's saying that that information can tell him something he needs to know to help you.

I hope I got that right jtarin. Please correct me if I'm wrong my friend.

---

### Post by DemianDemerzel on 2011-05-24
> **ClientAlive said:**
> If you can find "Network Tools" as described in my above post then click the "Ping" _tab_ - type in the name of the site you want (without the www part); click the "Ping" _button_; and, if things on the computer are working right (maybe not for you right now) it will give you the ip address. The ip address is seen when you click the little plus (+) sign near the bottom of the window. That makes the "details" opens up and the info would be in there.

Nothing happens when I click the Ping tab. This is even true of websites which I have no problem accessing. 

I am sorry for replying so late. I was a little disillusioned. Now I want to try it again. Thank for your support.

---

### Post by Wim Sturkenboom on 2011-05-24
open a terminal; type the command highlighted in bold

```
wim@aa0:~$ **ping -c 5 google.co.za**
PING google.co.za ([COLOR="Red"]74.125.233.20[/COLOR]) 56(84) bytes of data.
64 bytes from google.co.za (74.125.233.20): icmp_req=1 ttl=52 time=104 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=2 ttl=52 time=408 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=3 ttl=52 time=158 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=4 ttl=52 time=538 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=5 ttl=52 time=268 ms

--- google.co.za ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 104.801/296.011/538.822/159.848 ms
wim@aa0:~$

```You want the IP address which I have highlighted in red. Replace the domain by the one that you're interested in.

---

### Post by jtarin on 2011-05-24
> **ClientAlive said:**
> If you can find "Network Tools" as described in my above post then click the "Ping" _tab_ - type in the name of the site you want (without the www part); click the "Ping" _button_; and, if things on the computer are working right (maybe not for you right now) it will give you the ip address. The ip address is seen when you click the little plus (+) sign near the bottom of the window. That makes the "details" opens up and the info would be in there.

Here's a picture of mine. I'm running Ubuntu 10.04 (not 11.04) but should be the same for you.
----------------------------------

Edit: What's going on is there are two ways to launch that network tools thing. What jtarin is telling you to do in the terminal is supposed to launch the same thing I'm describing how to get to using the gui.

I think what jtarin is asking you to do is if the network tools doesn't launch when you put his code into the terminal - to post what the terminal does put out. He's saying that that information can tell him something he needs to know to help you.

I hope I got that right jtarin. Please correct me if I'm wrong my friend.Correct your are.....thanks for the explanation.Sometimes I forget the depth I need to go.:P

---

### Post by DemianDemerzel on 2011-05-25
> **Wim Sturkenboom said:**
> open a terminal; type the command highlighted in bold

```
wim@aa0:~$ **ping -c 5 google.co.za**
PING google.co.za ([COLOR=Red]74.125.233.20[/COLOR]) 56(84) bytes of data.
64 bytes from google.co.za (74.125.233.20): icmp_req=1 ttl=52 time=104 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=2 ttl=52 time=408 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=3 ttl=52 time=158 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=4 ttl=52 time=538 ms
64 bytes from google.co.za (74.125.233.20): icmp_req=5 ttl=52 time=268 ms

--- google.co.za ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 104.801/296.011/538.822/159.848 ms
wim@aa0:~$

```You want the IP address which I have highlighted in red. Replace the domain by the one that you're interested in.

The command doesn't work. For this reason I pinged **google.co.za** through Gnome Nettool. 

Here are the results:

Packets Transmitted: 5
Packets Received: 0
Successful Packets: 0%

The same thing is happening irrespective of the website I choose to ping.

---

### Post by KIAaze on 2011-05-25
It looks like you are behind some firewall.
Did you have any similar problems with other PCs or other operating systems (ex: Windows)?
Can you ping sites you can access with your browser?
======
Kaj en Esperanto ;) :
&#348;ajnas ke vi estas malanta&#365; iu fajro&#349;irmilo.
&#264;u vi havis similajn problemojn kun aliaj komputiloj aux aliaj operaciumoj (ekzemple Vindozo)?
&#264;u vi povas e&#293;osondi retejojn kiujn vi povas atingi per la TTT-legilo?

---

### Post by DemianDemerzel on 2011-05-25
> **KIAaze said:**
> It looks like you are behind some firewall.
Did you have any similar problems with other PCs or other operating systems (ex: Windows)?
======
&#348;ajnas ke vi estas malanta&#365; iu fajro&#349;irmilo.
Cxu vi havis similajn problemojn kun aliaj komputiloj aux aliaj operaciumoj (ekzemple Vindozo)? ;)

No. I didn't have the problem when I used Windows 7. It is only after I installed Ubuntu 11.04 that I started encountering the problem.

=============

Ne. Mi ne havis la problemon kiam mi uzis Vindozon 7. Nur poste mi instalis Ubuntu-on 11.04, ke mi ekis renkonti la problemon. :)

De kie vi lernis, kara amiko, ke mi parolas Esperanton ? :)

---

### Post by DemianDemerzel on 2011-05-25
> **KIAaze said:**
> It looks like you are behind some firewall.
Did you have any similar problems with other PCs or other operating systems (ex: Windows)?
Can you ping sites you can access with your browser?
======
Kaj en Esperanto ;) :
&#348;ajnas ke vi estas malanta&#365; iu fajro&#349;irmilo.
&#264;u vi havis similajn problemojn kun aliaj komputiloj aux aliaj operaciumoj (ekzemple Vindozo)?
&#264;u vi povas e&#293;osondi retejojn kiujn vi povas atingi per la TTT-legilo?

No. I cannot ping even those websites which I have no problem browsing. 

=====

Ne mi ne e&#265; povas e&#293;osondi retejojn, kiujn mi ne havas problemon malfermi.

---

### Post by alphacrucis2 on 2011-05-25
Can you try this:


```
sudo apt-get install traceroute
```

The above command should install the traceroute program

```
traceroute -n google.co.za 
```

The above command does a hop by hop probe of the path to the destination. -n means don't try and resolve the ip addresses back to hostnames. (it runs much slower if you leave the -n out)

You should get up to thirty lines of output. Can you copy and paste here the first ten lines.

---

### Post by KIAaze on 2011-05-25
De la lernu forumo. Kaj vi ankaux skribis tie ke vi jam demandis &#265;e lernu. :)
Tamen via problemo estas tre stranga. Mi ofte vidis la DNS problemon, sed tio ne sxajnas esti via kazo.

Pardonu min, sed mi da&#365;rigos en la angla, &#265;ar mi ne havas sufi&#265;e da tempo por traduki &#265;ion nun.
=======

How do you connect to the internet? cable? wireless? over a phone? over another PC? wireless USB-stick? Did you install any filter/proxy/firewall? firefox add-ons?

Can you post the contents of the following files:
```
/etc/network/interfaces
/etc/host.conf
/etc/hostname
/etc/hosts
/etc/hosts.allow
/etc/hosts.deny

```
And the output of the following two commands:
```
ifconfig
iwconfig

```

Sorry if you already posted this, but I might have missed a few things in the thread. :)

---

### Post by DemianDemerzel on 2011-05-25
> **alphacrucis2 said:**
> Can you try this:


```
sudo apt-get install traceroute
```The above command should install the traceroute program

```
traceroute google.za.com 
```The above command does a hop by hop probe of the path to the destination. 

You should get up to thirty lines of output. Can you copy and paste here the first ten lines.

Here is what I get. Because I just can't copy it, you will an image here.

[ATTACH]193117[/ATTACH]

---

### Post by alphacrucis2 on 2011-05-25
> **DemianDemerzel said:**
> Here is what I get. Because I just can't copy it, you will an image here.


No problem. It worked but I messed up the destination domain. Try again using google.co.za

---

### Post by DemianDemerzel on 2011-05-25
> **KIAaze said:**
> De la lernu forumo. Kaj vi ankaux skribis tie ke vi jam demandis &#265;e lernu. :)
Tamen via problemo estas tre stranga. Mi ofte vidis la DNS problemon, sed tio ne sxajnas esti via kazo.

Pardonu min, sed mi da&#365;rigos nun en la angla, &#265;ar mi ne havas multon da tempo por traduki &#265;ion nun.
=======

How do you connect to the internet? cable? wireless? over a phone? over another PC? wireless USB-stick? Did you install any filter/proxy/firewall? firefox add-ons?

Can you post the contents of the following files:
```
/etc/network/interfaces
/etc/host.conf
/etc/hostname
/etc/hosts
/etc/hosts.allow
/etc/hosts.deny

```And the output of the following two commands:
```
ifconfig
iwconfig

```Sorry if you already posted this, but I might have missed a few things in the thread. :)

None of the commands comes with any result. :(

E nunc io anque es un studiente de interlingua. ;)

---

### Post by alphacrucis2 on 2011-05-25
> **DemianDemerzel said:**
> None of the commands comes with any result. :(

E nunc io anque es un studiente de interlingua. ;)

They are file names. You would need to issue a command to list them. For example to list /etc/network/interfaces type:

```
cat /etc/network/interfaces
```

---

### Post by KIAaze on 2011-05-25
Opening them directly with a text editor should also work. They aren't read protected by default.

P.S.: Mi ne ankora&#365; lernis interlingua (kaj ne vere planas fari tion :P (ne ankora&#365; almena&#365;)).

---

### Post by DemianDemerzel on 2011-05-25
> **alphacrucis2 said:**
> No problem. It worked but I messed up the destination domain. Try again using google.co.za

I tried it twice and both times got the same result.

Image: 

[ATTACH]193118[/ATTACH]

---

### Post by DemianDemerzel on 2011-05-25
> **alphacrucis2 said:**
> They are file names. You would need to issue a command to list them. For example to list /etc/network/interfaces type:

```
cat /etc/network/interfaces
```

The trick didn't work, friend!

---

### Post by Wim Sturkenboom on 2011-05-25
We basically only need to know if pinging a hostname resulted in giving you an IP address of that host; that you did not receive any packets is less important.

Your firewall might well be blocking the ping requests. You can stop the firewall for the test and start it afterwards again. I assume you have a firewall frontend installed (not sure what the one in ubuntu 11.04 is).

---

### Post by KIAaze on 2011-05-25
Well, what errors does the command give you?
Please always give any output from commands. And if it doesn't give any output at all, please say so.

The only reason I could see for "cat *" not giving any output would be that the file is empty.
And /etc/network/interfaces should not be empty by default. (I can't check the default contents now, because I have a customized one, but I think there should at least be some "auto lo" and
"iface lo inet loopback" in it)
So there might be something really wrong with your installation.

The other possible reason would be that "cat" is broken, but then you should really reinstall since it's one of the most basic commands.

> (not sure what the one in ubuntu 11.04 is)
I think it's "ufw". But it should be disabled by default.
To check, run:
```
sudo ufw status
```
and
```
sudo iptables -L
```

If you get this when running "sudo iptables -L", there shouldn't be any firewall on your PC:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
But there could be one on the router or elsewhere.

To disable ufw:
```
sudo ufw disable
```
To disable all possible firewall rules on your PC:
```
sudo iptables -F
```
(this does not guarantee that they won't be back after a reboot!)

---

### Post by DemianDemerzel on 2011-05-25
> **Wim Sturkenboom said:**
> We basically only need to know if pinging a hostname resulted in giving you an IP address of that host; that you did not receive any packets is less important.

Your firewall might well be blocking the ping requests. You can stop the firewall for the test and start it afterwards again. I assume you have a firewall frontend installed (not sure what the one in ubuntu 11.04 is).

Stopping the firewall ? I think it is a system that protects internet users from malicious programs and other threats that lurk around on web. Do you think it would be safe to turn it off, even transiently ? 

If you think it is, tell me how to do it ?

---

### Post by DemianDemerzel on 2011-05-25
> **KIAaze said:**
> Well, what errors does the command give you?
Please always give any output from commands. And if it doesn't give any output at all, please say so.

The only reason I could see for "cat *" not giving any output would be that the file is empty.
And /etc/network/interfaces should not be empty by default. (I can't check the default contents now, because I have a customized one, but I think there should at least be some "auto lo" and
"iface lo inet loopback" in it)
So there might be something really wrong with your installation.

The other possible reason would be that "cat" is broken, but then you should really reinstall since it's one of the most basic commands.


There is no response when I give the commands.

---

### Post by alphacrucis2 on 2011-05-25
> **DemianDemerzel said:**
> The trick didn't work, friend!

This is what I get on my laptop:

```
jazz@laptopt400:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

ie the file /etc/network/interfaces contains just those two lines listed above. When you say it didn't work, did it output anything at all?


Anyway if traceroute is working then there is nothing wrong at the ip level but there could be a higher level problem with a firewall or something as suggested by KIAze. Here is another command to try:

```
telnet www.hotmail.com 80
```


This will try to open a http (port 80) connection to one of the sites you were having trouble with. If it connects ok, it will say something like:

```
jazz@laptopt400:~$ telnet www.hotmail.com 80
Trying 64.4.2.109...
Connected to dispatch.kahuna.glbdns.microsoft.com.
Escape character is '^]'.
[COLOR="Red"]^][/COLOR]
telnet> [COLOR="Red"]quit[/COLOR]
Connection closed.
jazz@laptopt400:~$ 
```

The red lines I typed to end the connection. ^] is done by holding down Ctrl key and typing ] then release the Ctrl key and type the enter key. Then type quit to make the telnet program exit.

---

### Post by KIAaze on 2011-05-25
> **DemianDemerzel said:**
> Stopping the firewall ? I think it is a system that protects internet users from malicious programs and other threats that lurk around on web. Do you think it would be safe to turn it off, even transiently ? 

If you think it is, tell me how to do it ?

I updated my previous post while you posted, sorry.
But you should find all the necessary info there. :)

And yes, it is relatively safe to turn it off if you are running GNU/Linux and don't have any server software (like apache, openSSH, etc) installed. So don't worry. :)
In fact, like I said, the firewall is turned off by default on Ubuntu Desktop and even on Ubuntu server.

It's a lot easier to debug networking problems with the firewall off.
Once everything works, you can turn it back on.

If I understand things correctly, you just recently installed Ubuntu, so I can't imagine you already being infected by malware.
Just don't visit suspicious websites while the firewall is off and you should be fine.

---

### Post by DemianDemerzel on 2011-05-25
> **alphacrucis2 said:**
> This is what I get on my laptop:

```
jazz@laptopt400:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```ie the file /etc/network/interfaces contains just those two lines listed above. When you say it didn't work, did it output anything at all? 

Yes, I get no response at all.


> Anyway if traceroute is working then there is nothing wrong at the ip level but there could be a higher level problem with a firewall or something as suggested by KIAze. Here is another command to try:

```
telnet www.hotmail.com 80
``` 

No response. :mad:

---

### Post by alphacrucis2 on 2011-05-25
It's very strange if /etc/network/interfaces is empty then something is very wrong. As KIAze said there should at least be the loopback interface defined in there. Has anyone asked you to post the output of:

```
ifconfig
```

---

### Post by DemianDemerzel on 2011-05-25
> **KIAaze said:**
> I updated my previous post while you posted, sorry.
But you should find all the necessary info there. :)

And yes, it is relatively safe to turn it off if you are running GNU/Linux and don't have any server software (like apache, openSSH, etc) installed. So don't worry. :)
In fact, like I said, the firewall is turned off by default on Ubuntu Desktop and even on Ubuntu server.

It's a lot easier to debug networking problems with the firewall off.
Once everything works, you can turn it back on.

If I understand things correctly, you just recently installed Ubuntu, so I can't imagine you already being infected by malware.
Just don't visit suspicious websites while the firewall is off and you should be fine.

I just checked the firewall is already off. I never turned it on.

---

### Post by DemianDemerzel on 2011-05-25
> **alphacrucis2 said:**
> It's very strange if /etc/network/interfaces is empty then something is very wrong. As KIAze said there should at least be the loopback interface defined in there. Has anyone asked you to post the output of:

```
ifconfig
```

It doesn't work either.

---

### Post by alphacrucis2 on 2011-05-25
> **DemianDemerzel said:**
> It doesn't work either.

Just to double check, ifconfig is a command not a file, so you dont need to use cat. Just type ifconfig and hit the enter key. In theory if ifconfig returns nothing then you have no network setup at all.

---

### Post by DemianDemerzel on 2011-05-25
> **alphacrucis2 said:**
> Just to double check, ifconfig is a command not a file, so you dont need to use cat. Just type ifconfig and hit the enter key. In theory if ifconfig returns nothing then you have no network setup at all.

It returns nothing.

---

### Post by KIAaze on 2011-05-25
I think you should reinstall.
Or at least try with a live CD if you haven't already done so. (if you have a cable connection with DHCP you shouldn't have to setup anything)

If it still doesn't work, I would start suspecting a hardware problem or a problem with your network (filter, firewall, proxy or hardware problem at router or higher level(ISP?) or faulty cables, antenna).

The best way to check if it's a hardware issue would probably be to try to connect with another PC or with another OS installed (Windows for instance)

But your installation definitely looks broken if "ifconfig" doesn't return anything!
Maybe try "ifconfig -a" just in case, but I doubt it will be much different.
(although it could be that ifconfig returns nothing if the interfaces file is empty... O.o)

---

### Post by DemianDemerzel on 2011-05-26
> **KIAaze said:**
> I think you should reinstall.
Or at least try with a live CD if you haven't already done so. (if you have a cable connection with DHCP you shouldn't have to setup anything)

If it still doesn't work, I would start suspecting a hardware problem or a problem with your network (filter, firewall, proxy or hardware problem at router or higher level(ISP?) or faulty cables, antenna).

The best way to check if it's a hardware issue would probably be to try to connect with another PC or with another OS installed (Windows for instance)

But your installation definitely looks broken if "ifconfig" doesn't return anything!
Maybe try "ifconfig -a" just in case, but I doubt it will be much different.
(although it could be that ifconfig returns nothing if the interfaces file is empty... O.o)

I tried Hotmail and other websites through the live CD. To no avail. Seems like the problem lies somewhere else.

Should I give Linux Mint a try?

---

### Post by jre6 on 2011-05-26
In the terminal type:
```

ping hotmail.com

```
replacing hotmail.com with the one which you cant access. Now your computer will try to see if the server responds to your request.. If it's successful you might see something like this:
```

PING hotmail.com (65.55.72.167) 56(84) bytes of data.
64 bytes from origin.sn133w.snt133.mail.live.com (65.55.72.167): icmp_seq=1 ttl=240 time=615 ms
64 bytes from origin.sn133w.snt133.mail.live.com (65.55.72.167): icmp_seq=2 ttl=240 time=639 ms
64 bytes from origin.sn133w.snt133.mail.live.com (65.55.72.167): icmp_seq=3 ttl=240 time=615 ms

```
Press Ctrl+C to stop, otherwise it'll go on for a long time.
And if its unsuccessful, it means that the ISP is at fault. Unsuccessful attempts look like this:
```

ping: unknown host hotmail.com

```

Just paste the results here and I'll see what can be done.

---

### Post by KIAaze on 2011-05-26
```
Should I give Linux Mint a try?
```
Yes. Although I doubt it will change much.
And if you can, try with another PC. You could ask a friend who has a laptop for example.

What about the router? Do you have your own? The router is the box you connect your cable to normally and where you configure your wireless settings.
You can usually access its control panel by entering something like 192.168.1.1 or 192.168.2.1 in your browser.
You'll also need a password, which should have been given to you with the router. Otherwise you can google the router model to check for a default password. As a last resort, you can also reset the router by pressing a reset button somewhere on it.

Once you have access to the router control panel, you can check to see if it's correctly configured for your ISP and if it uses any firewall.

---

### Post by DemianDemerzel on 2011-05-26
> **jre6 said:**
> In the terminal type:
```

ping hotmail.com

```replacing hotmail.com with the one which you cant access. Now your computer will try to see if the server responds to your request.. If it's successful you might see something like this:
```

PING hotmail.com (65.55.72.167) 56(84) bytes of data.
64 bytes from origin.sn133w.snt133.mail.live.com (65.55.72.167): icmp_seq=1 ttl=240 time=615 ms
64 bytes from origin.sn133w.snt133.mail.live.com (65.55.72.167): icmp_seq=2 ttl=240 time=639 ms
64 bytes from origin.sn133w.snt133.mail.live.com (65.55.72.167): icmp_seq=3 ttl=240 time=615 ms

```Press Ctrl+C to stop, otherwise it'll go on for a long time.
And if its unsuccessful, it means that the ISP is at fault. Unsuccessful attempts look like this:
```

ping: unknown host hotmail.com

```Just paste the results here and I'll see what can be done.

I can access Aljazeera and here is what I get when I ping the website:

[ATTACH]193264[/ATTACH]

Hotmail is one of the sites I can't access and here is what I get on trying to ping it:

[ATTACH]193265[/ATTACH]

---

### Post by DemianDemerzel on 2011-05-26
> **KIAaze said:**
> ```
Should I give Linux Mint a try?
```Yes. Although I doubt it will change much.
And if you can, try with another PC. You could ask a friend who has a laptop for example.

What about the router? Do you have your own? The router is the box you connect your cable to normally and where you configure your wireless settings.
You can usually access its control panel by entering something like 192.168.1.1 or 192.168.2.1 in your browser.
You'll also need a password, which should have been given to you with the router. Otherwise you can google the router model to check for a default password. As a last resort, you can also reset the router by pressing a reset button somewhere on it.

Once you have access to the router control panel, you can check to see if it's correctly configured for your ISP and if it uses any firewall.

I CANNOT TURN ON the firewall. 

And do router and modem refer to the same thing ?

---

### Post by KIAaze on 2011-05-26
> **DemianDemerzel said:**
> I CANNOT TURN ON the firewall. 

And do router and modem refer to the same thing ?

No: [http://www.differencebetween.net/object/difference-between-modem-and-router/](http://www.differencebetween.net/object/difference-between-modem-and-router/)

But both might be in the same box.

According to your ping output, it strongly suggests that you have a firewall somewhere, because you can access Aljazeera over port 80 (http), but don't get any answer to your ping requests (port 5813).

It could be that the https port (443) is blocked, in which case any website using it will be blocked.
hotmail.com does redirect to https automatically for instance...

You could probe your ports with [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) if you want (it uses https ironically :/ ).

I think netstat and nmap might also allow you to check your network, but I don't really know how to use them.

The only thing that bothers me is that you said that you had no problems with Windows. So unless the firewall/ISP filters by OS as well... 0.o

Port number reference (for when you want to configure your firewall. But now you should first figure out how to turn it off.):
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

---

### Post by KIAaze on 2011-05-26
**_*Important:*_**
If you plan to reset your router (i.e. use the button which resets everything to factory settings, not the buttons which turns it off and on again), **make sure you have all the configuration data from your ISP first**, as well as the default password of your router!

It's really better to try to find the password first.

---

### Post by jtarin on 2011-05-26
Could you post a screenshot of the terminal you are using?

---

### Post by DemianDemerzel on 2011-05-28
> **jtarin said:**
> Could you post a screenshot of the terminal you are using?

How to do that? Should I shoot a photograph of my modem?

============================================================================

Besides, I reinstalled the whole system twice today. No improvement. 

I am downloading Fedora 15. If things don't change for the better in Fedora, I'm afraid I will have to switch to Windows.

I just want to thank you all for your kind support. You did all you could to help me out but it seems I am too dumb to follow even the simplest of instructions. 

I have started reading more on operating systems and how computers work in general. Once I have some basic knowledge about computers, operating systems and the internet, I will come back again to trouble you with my annoying questions. 

Thanks again. :p

---

### Post by KIAaze on 2011-05-28
> **DemianDemerzel said:**
> How to do that? Should I shoot a photograph of my modem?

The terminal is the thing you entered all the commands in that we suggested.
And you can take a screenshot of it, like you did before with the ping utility... Simply pressing the "printscreen" button should open up the screenshot program.

Just in case:
[http://maketecheasier.com/ways-to-grab-screenshots-in-ubuntu/2008/11/11/](http://maketecheasier.com/ways-to-grab-screenshots-in-ubuntu/2008/11/11/)
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Otherwise, yes a photograph would also work, especially if you want to post pictures of the router, so we can determine the model. But then it's easier if you figure out the model yourself an tell us.
This will be useful to give instructions for the router configuration.

> **DemianDemerzel said:**
> 
Besides, I reinstalled the whole system twice today. No improvement. 

I am downloading Fedora 15. If things don't change for the better in Fedora, I'm afraid I will have to switch to Windows.


You can also use Live-USB sticks to avoid burning CDs:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It would be really interesting to know if the websites work after a **clean** install of Windows (**i.e. without installing any additional software from your ISP!**).
So yes, please do try it with Windows again and let us know.

But don't forget that you can dual-boot! (Install GNU/Linux after Windows for that)
I'm still dual-booting after 5 years of GNU/Linux (even though I barely use the Windows entry at all these days, not even for games, which is the main reason for still dual-booting ^^).

P.S.: I still don't know if you connect by wire or wireless, which router you use, etc. And you never posted all the files I asked for...

---

### Post by jtarin on 2011-05-28
> 
Quote:
Originally Posted by jtarin View Post
Could you post a screenshot of the terminal you are using?
How to do that? Should I shoot a photograph of my modem?I want to see if your idea and our idea of a terminal is the same thing.

---

### Post by DemianDemerzel on 2011-05-29
I have just downloaded Fedora 15 and am trying it from a live CD. A good news is that I have no problem accessing any website from Fedora 15. It means two things:

1. The problem has nothing to do with the DSL server or modem or anything related to the internet service provider
2. There is something wrong with UBUNTU!!!!!!!!!!!!!!!!!!!!!!!!

Now that we have narrowed down the source of the problem, any suggestions from your side, dear friends! :p

---

### Post by KIAaze on 2011-05-29
First suggestion: Use Fedora then. :)

Second suggestion: Check the MD5 sum of your Ubuntu live-CD: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
(I think you can also do it from the Live-CD boot menu.)

---

### Post by DemianDemerzel on 2011-05-29
> **KIAaze said:**
> First suggestion: Use Fedora then. :)

Second suggestion: Check the MD5 sum of your Ubuntu live-CD: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
(I think you can also do it from the Live-CD boot menu.)

Fedora doesn't have LibreOffice and now when I have downloaded it, it doesn't install.

---

### Post by jtarin on 2011-05-29
From the first page to this you have not provided the information about the fact you were trying to connect with a Ubuntu Live CD or given all the information that was asked of you. I for one cannot continue to help someone that can't help themselves.

---

### Post by DemianDemerzel on 2011-05-29
> **jtarin said:**
> From the first page to this you have not provided the information about the fact you were trying to connect with a Ubuntu Live CD or given all the information that was asked of you. I for one cannot continue to help someone that can't help themselves.

Hi JTarin,

I wasn't trying to connect through a live CD. I had installed Ubuntu 11.04. I also tried to connect through the CD but it didn't work. I guess I made it clear in the very first post that I **had installed Ubuntu**, didn't I? :p

---

### Post by jtarin on 2011-05-30
> **DemianDemerzel said:**
> Hi JTarin,

I wasn't trying to connect through a live CD. I had installed Ubuntu 11.04. I also tried to connect through the CD but it didn't work. I guess I made it clear in the very first post that I **had installed Ubuntu**, didn't I? :pYes but every one of your terminal command requests you were asked to initiate ended in you coming back with zero results which is virtually impossible on an installed system.

---

### Post by DemianDemerzel on 2011-05-30
> **jtarin said:**
> Yes but every one of your terminal command requests you were asked to initiate ended in you coming back with zero results which is virtually impossible on an installed system.
 
Do you call that thing terminal which props up when you press Alt + F2?
 
If yes, I wasn't getting any response when I entered ifconfig.
 
And anyways, I am not blaming you. I am grateful to you that you tried your best to help me out. It 
 
I have installed Windows 7 Ultimate again because I couldn't find LibreOffice in Fedora.
 
I will come back to Linux when I know more about Operating Systems. It was really a nice experience; except for those annoying websites. I found the forums and people like you very helpful. It is just that I was too stupid to understand.
 
And may I know your real name? Mine is Chetan Anand and I live in Patiala, Punjab, India.

---

### Post by jtarin on 2011-05-30
> **DemianDemerzel said:**
> Do you call that thing terminal which props up when you press Alt + F2?
 
If yes, I wasn't getting any response when I entered ifconfig.
 
And anyways, I am not blaming you. I am grateful to you that you tried your best to help me out. It 
 
I have installed Windows 7 Ultimate again because I couldn't find LibreOffice in Fedora.
 
I will come back to Linux when I know more about Operating Systems. It was really a nice experience; except for those annoying websites. I found the forums and people like you very helpful. It is just that I was too stupid to understand.
 
And may I know your real name? Mine is Chetan Anand and I live in Patiala, Punjab, India.

[Terminal]("http://www.videolan.org/doc/vlc-user-guide/en/images/terminal-linux.jpg")

---

### Post by DemianDemerzel on 2011-05-30
> **jtarin said:**
> [Terminal]("http://www.videolan.org/doc/vlc-user-guide/en/images/terminal-linux.jpg")
 
 
Wow! I was wrong on Terminal too! Was giving commands in some other window.

---

### Post by ChauDuong on 2011-05-30
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

I went through all this.

None of them worked for me.
Some have no effects and some are not applicable.

Please help me  >_<.

I cannot connect to this site, ubuntu.com, launchpad.net ...
I cannot update, upgrade or install anything...

Although I can ping them all.

Thank you in advance...

I tried everything!

---

### Post by fremantle on 2011-05-30
> **DemianDemerzel said:**
> Hi JTarin,

I apologise but I don't know what does a '*terminal*' mean?

I forgot to mention in the previous post but I also don't know what does '*pinging a website*' mean?

Thank you for taking out your precious time to reply.

lol..
anyways, i use some of those websites freqly, no problem here.

---

### Post by jtarin on 2011-05-30
Start another thread. This one is marked as Solved and will get little notice. Supply information as to how you connect. Wired/wireless. Adsl,PPPoE or cable etc. Also post what exactly you have tried.

---

### Post by KIAaze on 2011-05-31
> **ChauDuong said:**
> [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)


Well, that guide has one interesting point related to this thread...
> 1.5.2. Connected, Issues with Certain Websites

    Disable IPv6. 
But first, it's essential to understand what a terminal is.:roll:

---

### Post by dhawal92 on 2011-06-22
> **jtarin said:**
> Use the same procedure and open /etc/resolv.conf and edit to look like this:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```save...then try to connect.

wow worled for me thanks man :)

---

### Post by KIAaze on 2011-06-22
8.8.8.8 and 8.8.4.4 are the Google public DNS IP addresses.
So your system gets configured to use Google's DNS to find the IP address of websites. I think this should be mentioned in the solution. I wouldn't want to use some random DNS servers somebody posted here. :)
cf [http://code.google.com/speed/public-dns/docs/intro.html](http://code.google.com/speed/public-dns/docs/intro.html) for more info

---

### Post by deva99 on 2011-08-09
ok. i am new to this forum. anyways if ur unable to access the sites ..ha. i had same problem. here is the ultimate solution...

sudo pppoeconf 

n then follow command...this will set ur net by it self.. u dont need DSL settings or anything else. restart os...then u will see..tht u dont hav any conection to dial . just open browser...net will work.with all sites. if u wana disconnect net..just plug out ur wired lan ...hav fun.gd.tc :D:D:D

---

### Post by gandaran on 2011-08-09
> **deva99 said:**
> ok. i am new to this forum. anyways if ur unable to access the sites ..ha. i had same problem. here is the ultimate solution...

sudo pppoeconf 

n then follow command...this will set ur net by it self.. u dont need DSL settings or anything else. restart os...then u will see..tht u dont hav any conection to dial . just open browser...net will work.with all sites. if u wana disconnect net..just plug out ur wired lan ...hav fun.gd.tc :D:D:D
sudo pppoeconf is for setting up DSL modems, if you have a router just ensure you setup the router properly and it'l work just as good as pppoeconf.
two important things in any internet connection is that router provides the correct internet DNS and DCHP server is enabled in router setup.

---

