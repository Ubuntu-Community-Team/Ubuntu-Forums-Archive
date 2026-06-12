---
title: "ADSL problem"
date: 2005-06-10
forum: Networking &amp; Wireless
---

### Post by moshi on 2005-06-10
I'v spent a lot of time on browsing forums in networking but still can not find a way to set up my ADSL via PPPOE! I'v tried Red Hat, Lindos, Fedora, Mandrake and SuSe whitout problem before,only ubuntu has this problem. I really don't understand why ubuntu can say it is user friendly!

---

### Post by cwaldbieser on 2005-06-11
Well, you have not really given us much to go on.  From reading your post, I can divine:

1) You are having a problem setting up a DSL connection to an Ubuntu machine.
2) You have had some experience in this arena before with other Linux distributions.

What kind of problem are you having?  Most of the time, you just plug in your NIC to your DSL modem or router and you are good to go.  At least that has been my experience, though anyone who peruses the networking subforum can see that this is not always the case.

Some useful info such as your network setup, type of NIC, what you have already tried and what the results were would help a lot.

Also, comments like:

>  I really don't understand why ubuntu can say it is user friendly!

tend not to engender sympathy in those who would otherwise be willing to help you.  In fact, based on experiences I have had with several different operating systems, I could just as easily apply your statement to several flavors of UNIX, Linux, Windows, and Mac operating systems (to name a few).

We all are suceptible to frustration at times, and computers sometimes seem to have a special knack for bringing out this particular sentiment in us all.

There is an old saying, "You can catch more flies with honey than with vinegar."  This old wisdom suggests that you are more likely to win help for yourself by approaching others from a position of supplication rather than one of confrontation.

---

### Post by moshi on 2005-06-11
Dear Cwaldbieser,

Thank you for your advice. I am using a pci enthernet card and a ADSL modem by using DHCP through pppoe, but there is no option in networking where I can put my userID and passwords. I almost tried every forum I read from this site including tring to compile new kernel with mm patch for pptpclient, so I don't really remember what  I'v tried, but the results were all negative. One result worth mention is that the bash always say gcc command not found before and after I installed gcc-2.95 and gcc-3.3.5 respectively.

---

### Post by cwaldbieser on 2005-06-11
Hmm.  Well, I am not entirely familiar with your situation.  I will try to explain a little bit about my ISP and how my setup works, and then maybe you can explain where the key differences from your setup, and we will be able to arrive at some sort of answer.

First, my ISP gave me a DSL modem (a Westell 2200), that has both ethernet and USB jacks.  I plugged my computer's pci ethernet card into the modem's ethernet jack.  Now, the stock Ubuntu kernels understand how to do ADSL networking, so I don't have to do anything with the kernel.  The only piece remaining is the credentials-- How does my ISP log me on through my account?

Well, my ISP officially only supports certain versions of Windows and Mac, and they give you software that is supposed to run a wizard and set all that up for you.  For better or for worse, when I tried to run that software on a WinXP Home system, it crashed, so I had to call technical support, and they helped me set it up manually.

Basically, the modem has a mini web-server set up inside it.  If you open a browser and enter the modem's IP address in the URL bar, you get to a configuration web page where you can make all kinds of setting changes, including your user account and password.

I am guessing that your modem may have a similar configuration screen.  I have router that has a very similar kind of configuration setup.  I just googled for my modem, and here is a link that describes what I am talking about:

[http://www.lava.net/support/config/dsl/westell/](http://www.lava.net/support/config/dsl/westell/)

So my thought is that you just need to look up information on your particular DSL modem, or you might try calling your ISP's technical support and asking them how to configure the modem with your account information.

Does that make sense to you?  Or am I totally off base?

---

### Post by moshi on 2005-06-11
Thank you for your reply, and I'v read your post on DSL before, but I think PPPoE is different from your situation.

---

### Post by cwaldbieser on 2005-06-11
Well, you may be right.  I make no claims as to being an expert about computer networking, or about having any special insight in your case in particular.  

However, the PPPoE term you used did sound familiar to me-- something I had researched over a year ago when I was going to make the switch from dial-up to DSL.  I looked up some links on Google and Wikipedia.  Maybe someone can help me out here or correct me if I am in error, but it appears that current DSL technology either works by using PPPoE or PPPoA.  I am pretty sure that my connection to the Internet uses PPPoE.

Link to DSL in Wikipedia:
[http://en.wikipedia.org/wiki/ADSL](http://en.wikipedia.org/wiki/ADSL)

Is your ISP a big name that someone else here may have heard of or be using?  If so maybe they can give you hand with your problems.  Anyway, I wish you good luck!

---

### Post by pietro_spina on 2005-06-17
[QUOTE=moshi]but there is no option in networking where I can put my userID and passwords[/QUOTE]

have you tried this (probably have, but I'll offer it up anyway)

from a terminal window type

```
sudo pppoeconf
```

This is what I used for my PPPoE dsl connection through Verizon Boston...
it asked for my dsl acount user name and password and if I wanted to connect at start up... 

If you don't choose to connect at start up then you have to enter

```
pon dsl-provider
```

to fire it up each time... but you can make a button or such for that...

-p

---

### Post by mila80 on 2005-06-20
And if your connection make other trouble... Try with it;

Change your /etc/network/interfaces by commenting out the lines:


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
# script grep
# map eth0

# The primary network interface
#iface eth0 inet dhcp

My connection stopped after a while and I can use synaptic or apt.... When i change it, all works well...

Bye, MArco

---

### Post by teumima on 2005-06-23
[QUOTE=moshi]Thank you for your reply, and I'v read your post on DSL before, but I think PPPoE is different from your situation.[/QUOTE]
 Moshi,

You in Israel? 

If you are. I'll tell you how to set it up. In case you're not don't want to waste space.

sudo pppoeconf should work for anywhere.

Take care

---

### Post by ubuntu_demon on 2005-06-25
[QUOTE=mila80]And if your connection make other trouble... Try with it;

Change your /etc/network/interfaces by commenting out the lines:


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
# script grep
# map eth0

# The primary network interface
#iface eth0 inet dhcp

My connection stopped after a while and I can use synaptic or apt.... When i change it, all works well...

Bye, MArco[/QUOTE]
 don't do this. It will only take your network/internet down as soon as /etc/network/interfaces  is loaded again (for example after a reboot). 

mila80 please don't give this advice anymore

---

