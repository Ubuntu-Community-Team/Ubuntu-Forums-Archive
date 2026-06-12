---
title: "Really frustrated and disappointed with WiFi on Ubuntu"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2007-02-07
So I just installed Edgy a few days ago and got it setup for the most part, I am learning more than I normally did in the past about Linux. I have tried different distros off and on for the past decade and have never stuck with it because the experience has been just awful.

However Ubuntu (Edgy) has really changed a lot of my thoughts on Linux. Sad to say though that my negative feelings for the OS are coming back. I installed my wireless NIC drivers fine and can get on the internet after being prompted for my WPA key a bunch of times. I posted on the forums looking for help and thought I had a resolution.

[http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session](http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session)

However I am still being prompted for my keyring password every time I reboot and its quite annoying. I don't understand why it is so difficult to do something as simple as log into a wireless network. I was hoping something like this would have been easier.

Now the fact that I'm somewhat of a Linux noob doesn't help so I suppose take my rant for what its worth. Also if you have any suggestions as to how I can resolve this issue it would be much appreciated.

---

### Post by gradedcheese on 2007-02-07
Please look at this:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

and scroll to "Avoiding password nagging" to learn how to solve that keyring issue.   You'll need some basic tools:

sudo apt-get install binutils make gcc

but otherwise it's very easy to do.  I hope that helps.

By the way, I would argue that most of your frustrations with the OS are actually an issue with your wireless chipset manufacturer and it is indeed an unfortunate state of affairs.  In case you're curious, it's a problem of communication (they won't disclose enough information to people willing to write drivers, for free, for these cards), and FCC regulations (which require some WiFi firmware parts to be extremely closed).  The situation is getting better, and some recent developments should make cooperation with chipset manufacturers even better, but it will take a little time.

---

### Post by handy on 2007-02-07
I agree with you:

All of the *nix distro's share the same problem to much the same extent:  The owners of the firmware that lives in the hardware = wireless NIC's, won't make their code open source!  

This means that the coder's have to work incredibly hard to reverse engineer the firmware - drivers - so the hardware will work.

A really tough job, & in my opinion wireless networking is the biggest stumbling block for the *nix distro's at the moment.  It won't always be this way, but that is how it is right now, I'm sorry to say.

Blame it on the paranoid (greedy) marketroids. :(  :confused:

---

### Post by gradedcheese on 2007-02-07
handy -- there's a little more to it.  The WiFi NIC chipset has to ensure that a user cannot accidentally (and, to some extent) maliciously cause the card to operate outside of FCC guidelines.  This includes setting Tx power to illegal levels, changing to channels you're not allowed to use, etc.  If/when the card allows this to be violated and it gets violated, the chipset manufacturer is (I believe) responsible, even if the driver wasn't written by them.  Hence, they're very scared to work with the community.  Furthermore, some cards have their MAC (media access control) as hardware (or a combination of firmware) while many implement the MAC in software (ie: in the driver/module).  This presents a challenge when one wants to allow a good driver to be written while making sure that the MAC can't be made to do things that the FCC would object to.  However, the infrastructure for this is indeed changing and things will be better.  Until then, some cards work because there was some communication and a driver got written, some work because of reverse-engineering, and some don't work because they haven't been reverse-engineered yet.  I don't like the situation, but there's more to it than marketing :(

I don't like blaming 'the OS' though, I mean we have a community willing to write and maintain drivers for free for these manufacturers, where else can they get that deal? :)

---

### Post by handy on 2007-02-07
Thanks for the heads up! :) 

It is obviously more complicated than manufacturers worried about loosing their perceived competitive edge.

I'm not really sorry for using the all inclusive throw away line - **blame it on the (greedy) paranoid marketroids**, I love to use that line every chance I get! :KS

---

### Post by SnowPunk98 on 2007-02-07
Interesting I didn't know that it was the fault of the manufacturer rather than the OS. So why is it that regular NICs have good driver support and WiFi do not? Is it because they have more damage capability for the company or that wired NICs have been around longer, or what?

As for the link you posted about getting rid of the nagging I think I already did that.

A question I have is how do I know if my keyring password is the same as my login password. I obviously know what my login password is but I don't know how to check or reset the password for the keyring.

---

### Post by gradedcheese on 2007-02-07
It really has to do with the FCC: there isn't much that you can do with an Ethernet NIC to violate FCC regulations, but you can easily do it with a WiFi interface due to it having a radio as its PHY.  Also as you said, the Ethernet NICs have been around a long time and are no longer considered hot intellectual property by their developers (they were though at one time and writing the first drivers from them was a pain!).  WiFi cards are therefore in a uniquely bad position, but it has almost nothing to do with the OS and everything to do with the attitudes of their chipset manufacturers and fears of getting into trouble.  

I'll try to see what can be done about your password situation and I'll post any info that I find.

---

### Post by SnowPunk98 on 2007-02-07
I would think I would see more users with this problem, either I am not seeing them or I am one of the few. Either way I will run through this guide and hopefully it will fix my problem. I also found a test version of that allows me to reset the keyring password which might be the problem I am having.

---

### Post by SnowPunk98 on 2007-02-10
Dude I can't get this freekin keyring thing to go away. All I want to do is log into Ubuntu and have WiFi work, is that so much to ask :(

---

### Post by SnowPunk98 on 2007-02-10
please help

---

### Post by handy on 2007-02-14
Please understand that the problem is due to manufacturer's not releasing their firmware's code.  

This means that the programmer's have to work harder than we can imagine to reverse engineer all this stuff.  The old NIC's have basically all been done, in most cases years ago.

Wireless networking is probably the biggest problem for non windoze systems in the world at the moment.

I'm sure that there will be people with detailed info' about this situation that will likely contradict what I have said.  But the bottom line still stands.

Wireless networking is tough stuff for Linux & BSD at the moment!

---

