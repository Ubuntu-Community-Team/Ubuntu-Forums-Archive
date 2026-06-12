---
title: "Can I block applications with a firewall?"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by NikS on 2009-09-14
Hi..
I have an internet connection that has a download limit per month. So i need to watch my network so that nothing accesses it other than the applications I need, like firefox or synaptic etc.

Is it possible for me to block network access based on the applications...??
I installed firestarter, but it manages ports and I am not that well aware of opening/closing (forwarding: what does it mean??) them.. I think it would be better for me if there was some way to block applications from reaching the internet. (Like, some pop-up comes up when some application tries to connect asking me to take action or else I categorize applications to be allowed or to be blocked...!!)

Thanks

---

### Post by talsemgeest on 2009-09-14
> **NikS said:**
> Hi..
I have an internet connection that has a download limit per month. So i need to watch my network so that nothing accesses it other than the applications I need, like firefox or synaptic etc.

Is it possible for me to block network access based on the applications...??
I installed firestarter, but it manages ports and I am not that well aware of opening/closing (forwarding: what does it mean??) them.. I think it would be better for me if there was some way to block applications from reaching the internet. (Like, some pop-up comes up when some application tries to connect asking me to take action or else I categorize applications to be allowed or to be blocked...!!)

Thanks
Since an app will only connect to the internet once it has been started (usually by you), you are probably better off making sure that you only run apps that you want to use, and close them afterwards.

---

### Post by XCan on 2009-09-14
I don't think there are any easy way to shut down apps from the internet like in Windows. Those solutions I've found were more involved that I liked at least.

---

### Post by 3rdalbum on 2009-09-14
> **NikS said:**
> Hi..
I have an internet connection that has a download limit per month. So i need to watch my network so that nothing accesses it other than the applications I need, like firefox or synaptic etc.

Is it possible for me to block network access based on the applications...??
I installed firestarter, but it manages ports and I am not that well aware of opening/closing (forwarding: what does it mean??) them.. I think it would be better for me if there was some way to block applications from reaching the internet. (Like, some pop-up comes up when some application tries to connect asking me to take action or else I categorize applications to be allowed or to be blocked...!!)

Thanks

What you're looking for is one of those lovely anti-virus-company inventions called an "outbound firewall". If you thought Windows Vista's UAC prompts were annoying, try running an outbound firewall that asks about every single program that tries to access the internet.

No, as far as I know there is no way to replicate this extremely frustrating prompting. The only program on Linux that accesses the Internet uncommanded is the Update Manager, and this can be disabled. Just run whatever programs you want to run, and don't run anything that you don't want to run.

You might be able to block individual programs from accessing the Internet by using AppArmour and building profiles, but this might be beyond your abilities, and in any case I don't know enough about it to walk you through.

I also suggest having a look at some articles about what firewalls actually do; it might help you use Linux's inbuilt firewall and understand its function.

---

### Post by armandh on 2009-09-14
fortunatly you have probably avoided the biggest of the calling home hardware/software by not needing an AV. Unlike XP&Vista where practically every add on hardware driver is like ET calling home on every startup, Ubuntu's printer and mouse drivers don't. However, the biggest automatic user in Ubuntu is probably the unified update function. just don't update except to your schedule.

---

### Post by freak42 on 2009-09-14
well I can only propose a nasty hack, but maybe this is better than nothing.

you can use tsocks ([http://tsocks.sourceforge.net/](http://tsocks.sourceforge.net/)) its in the repos.
Actually this app wraps network calls and sends them to a proxy for software that doesn' support proxies. However I guess if you specifiy a bogus proxy in the tsocks conf file it will just basically block the internet connection attempts by the appliation.

hth

---

### Post by scorp123 on 2009-09-14
> **XCan said:**
> I don't think there are any easy way to shut down apps from the internet like in Windows And you know why? :D

Because there is hardly ever the necessity for this. I am not aware of any program in Ubuntu that would access the Internet behind your back. The exception being the "Update Manager", but that one is easy to turn off (and even if: the lists of updates it pulls are just a few KB in size ... it won't download a thing unless you explicitly tell it so).

---

### Post by XCan on 2009-09-14
Sure, however, I would still liked an easy-to-use approach, especially considering how many people live by Wine.

---

### Post by scorp123 on 2009-09-14
> **XCan said:**
> especially considering how many people live by Wine. The programs inside Wine won't be launched unless you launch your Wine session. So they too can't do anything behind your back unless you have explicitly started them.

---

### Post by talsemgeest on 2009-09-14
> **XCan said:**
> Sure, however, I would still liked an easy-to-use approach, especially considering how many people live by Wine.
Is there an easier approach than having to do nothing?

---

### Post by XCan on 2009-09-14
Of course the obvious solution for control is not to start any apps at all, or better yet not starting the computer. But some people do require apps that can't be inspected that run through Wine, telling them to not start them doesn't sound like a satisfactory solution. Or consider online installers, or apps meant to be used while online, that a user did not realize. User error: Most absolutely definitely. User-error resistant: Debatable. Or perhaps Ubuntu completely separates that from user friendliness? Well I don't know. I just feel it could come in handy for some users (not really me) if it wouldn't be so involved.

---

### Post by adrianx on 2009-09-14
> **XCan said:**
> Of course the obvious solution for control is not to start any apps at all, or better yet not starting the computer. But some people do require apps that can't be inspected that run through Wine, telling them to not start them doesn't sound like a satisfactory solution. Or consider online installers, or apps meant to be used while online, that a user did not realize. User error: Most absolutely definitely. User-error resistant: Debatable. Or perhaps Ubuntu completely separates that from user friendliness? Well I don't know. I just feel it could come in handy for some users (not really me) if it wouldn't be so involved.
Wouldn't you say that expecting a Linux distribution to cater for programs that are not meant to run in Linux is asking a bit much? 

I doubt that the Windows firewall (or any other one for that matter) would permit me to block individual Linux applications that I run inside a VM (like VirtualBox). The situation with Wine is similar.

---

### Post by bodhi.zazen on 2009-09-14
The windows "application firewall" is skin deep and is easy to work around.

---

### Post by XCan on 2009-09-15
> **adrianx said:**
> Wouldn't you say that expecting a Linux distribution to cater for programs that are not meant to run in Linux is asking a bit much? 

I doubt that the Windows firewall (or any other one for that matter) would permit me to block individual Linux applications that I run inside a VM (like VirtualBox). The situation with Wine is similar.

Please read my post again. 

bodhi: You're right, or rather the built-in firewall in Windows does not stop outgoing either by default, but third-parties of course go to various depths. Question is, is nothing better than something? Again, the point here is to provide an option, there are tons of worthless apps already. :p

---

### Post by bodhi.zazen on 2009-09-15
> **XCan said:**
> Question is, is nothing better than something? Again, the point here is to provide an option, there are tons of worthless apps already. :p

See Master Foo :

[Master Foo and the Nervous Novice]("http://catb.org/%7Eesr/writings/unix-koans/nervous.html")

"Something" is not better then nothing. If needed iptables can be configured to restrict outgoing traffic, but not per application.

The closest thing we have to per application restrictions would be Apparmor.

---

### Post by 3rdalbum on 2009-09-15
Also see Sun Tzu in The Art of War:

"It is often easier to not do something dumb than it is to do something smart."

---

### Post by XCan on 2009-09-15
*Sigh*, not unexpected answers. Linux is great as one can use it however one wants, but only if it goes along the lines of the fundamental mentalities of Linux will it be accepted. 

Anyway, I know all your arguments, and I know your reasoning, and I can't say that I don't agree with them in almost all cases. But I disagree about not providing the option simply due to the Linux mentality. Philosophy is great, but people are people and not replicates of a logical device.

---

### Post by adrianx on 2009-09-15
> **XCan said:**
> Please read my post again.

> **XCan said:**
> *Sigh*, not unexpected answers. Linux is great as one can use it however one wants, but only if it goes along the lines of the fundamental mentalities of Linux will it be accepted. 

Anyway, I know all your arguments, and I know your reasoning, and I can't say that I don't agree with them in almost all cases. But I disagree about not providing the option simply due to the Linux mentality. Philosophy is great, but people are people and not replicates of a logical device.
You know, at first I thought that I really *did* misunderstand your post.... now I'm not so sure.

Statements like "fundamental mentalities of Linux", "Linux mentality" and "...perhaps Ubuntu completely separates that from user friendliness?" can easily cause that kind of confusion. :confused:

---

### Post by RetchingRabbit on 2009-09-15
> **XCan said:**
> *Sigh*, not unexpected answers. Linux is great as one can use it however one wants, but only if it goes along the lines of the fundamental mentalities of Linux will it be accepted. 

Anyway, I know all your arguments, and I know your reasoning, and I can't say that I don't agree with them in almost all cases. But I disagree about not providing the option simply due to the Linux mentality. Philosophy is great, but people are people and not replicates of a logical device.

All of this seems more like a high school philosphy debate than a tech question. Allow me to pose a question of my own:
Exactly what applications do you use that are accessing the internet unbidden? 





Please include pertinent log files.

---

### Post by HarrisonNapper on 2009-09-15
Firstly, let me start by saying that there is something and it's not nothing. Secondly, let me say that easy-to-use is an entirely subjective term. For instance, you have succeeded in using the internet; many people do not find the internet (or as they call it: "AOL") easy to use.

So here is a solution that is easy-to-use for some if the steps are followed correctly:
Graphical:
> 
1. Open synaptic
2. Search for firestarter
3. Add this package and all of its dependencies (this will be default, so, like windows, just "Ok" through it)
4. Once it has installed, go to your Main Menu and select Applications>Internet>Firestarter
5. Select the tab "Policy"
6. There is a drop-down menu that defaults to "Inbound traffic policy"; change that to "Outbound traffic policy"
7. You may now select whether you would like to deny or allow outbound traffic by default
8. Now comes the slightly more difficult part: finding the ports the application operates on; for that, I would suggest using your search engine of preference (try Google if it's not working elsewhere)
9. Now that you have succeeded in identifying the ports, simply create an exception for those ports by right-clicking in the second box that will start with "Deny/Allow Service" and selecting "Add Rule"
10. Create a name for the service you are creating an exception for and specify the ports in the following format: number-number
11. Success! Switch over to the status tab and start your new firewall
That may have seemed long and complicated, but I encourage you to think about it in a new way: Windows makes it appear as though firewalls permit/deny applications when this is not the case. This may seem to be easier, but not only is it less secure than specifying ports, it can actually be less secure than not having run that firewall in the first place (on Linux, anyway). I would also ask you to think back on your first experiences with Windows and imagine those experiences if you had had almost no one around who knew what Windows was. Linux is a great Operating System, but it is not perfect. With patience, I hope you will eventually find, as I did over the years, that the imperfections of Linux are far more tolerable than those of Windows.

---

### Post by Geoff918 on 2009-09-15
You *could* pull your ethernet cable, or turn-off your wireless card when you're not explicitly using the internet. This is the most fool-proof way of not having random information go out.

Very few items will use much internet bandwidth, anyway. Don't launch your IM program, don't launch NTP, disable Auto-updates (as many have said already), don't start any host protocols such as ftp, http, ssh, etc.

If all of the items in question are in Windows, why not run VirtualBox and simply disable networking unless you choose to "go online" with it? Granted, Windows is on the internet all the time and randomly connecting to things, you won't find that sort of thing with the Linux kernel.

---

### Post by XCan on 2009-09-16
I never said I needed to block an app off the network. I claimed and still do that I would rather have the option and let the user choose than not having it at all (friendly that is ;) ) since that's not how we've ever done it. Perhaps we don't see the need of such an option, that's great, but that automatically means that such an option should never exist?

---

### Post by NikS on 2009-09-20
Thanks a Lot everyone for your replies..

The first reason for me to think that I need a firewall was that, when I see the system monitor, it continuously shows me some network activity.. Some bites being received and some being sent...
I still do not know the reason why...!!!
The other thing is, even when I am connected to the net,(when I can browse) , the icons showing the connectivity in the upper right corner show disconnected networks...!! (showing a red cross..)

Later, I have learned that the network activity is shown even when there is no actual net consumed... Is it something because of the broadband connection I use..?? I first have to connect to a LAN, through which, after giving a password I can connect to the internet...!

Thanks all.

---

### Post by bodhi.zazen on 2009-09-20
What your are seeing is almost certainly "normal" activity.

[http://avahi.org/](http://avahi.org/)

You can disable avahi, although it will give you a warning, which you can ignore =)

If you want to know what the traffic is, use a sniffer, such as wireshark.

---

### Post by NikS on 2009-09-24
Thank you bodhi.zazen..
:)

---

### Post by Shaddarr on 2010-11-12
I find it interesting that noone has actually answered his question, although many gave their 'Linux-y Philosophy'-type answers (which is to be expected on a Linux forum). 

The restating of "I don't care what you want, but look at how cool linux is! It can do this.. and this..." is not an answer. Giving solutions to what is not the issue is an answer, but not what he was looking for. He states that 'blocking a specific application' is not what he was looking for (despite the thread title) but it is what 'I' was looking for.

Perhaps I need to start my own thread, but I'll try asking here first: Is there a way to block applications (not ports) from accessing the network? 

The person who said 'windows doesn't even do that' is incorrect. Many Windows programs utilize port 80 as their outgoing, yet firewalls will pop up saying that they are requesting access, and other applications (such as Firefox) will not set off the notification. This is Application Level Detection And Notification. This is what I am looking for, and it seems Linux/gui does not offer it (although Tuxgaurdian looks promising).

---

### Post by bodhi.zazen on 2010-11-13
> **Shaddarr said:**
> I find it interesting that noone has actually answered his question, although many gave their 'Linux-y Philosophy'-type answers (which is to be expected on a Linux forum). 

The restating of "I don't care what you want, but look at how cool linux is! It can do this.. and this..." is not an answer. Giving solutions to what is not the issue is an answer, but not what he was looking for. He states that 'blocking a specific application' is not what he was looking for (despite the thread title) but it is what 'I' was looking for.

Perhaps I need to start my own thread, but I'll try asking here first: Is there a way to block applications (not ports) from accessing the network? 

The person who said 'windows doesn't even do that' is incorrect. Many Windows programs utilize port 80 as their outgoing, yet firewalls will pop up saying that they are requesting access, and other applications (such as Firefox) will not set off the notification. This is Application Level Detection And Notification. This is what I am looking for, and it seems Linux/gui does not offer it (although Tuxgaurdian looks promising).

The short answer is no.

A somewhat longer answer is there have been some attempts to write such an application for Linux, but I would not advise any of them as they do not work well (IMO). This is not Windows and what the experienced Linux users will tell you is such an application is not needed, or at least the need has not been great enough that such an application has yet been developed.

Even on the Windows side, such applications are not as fool proof as you might think, they are relatively easily defeated.

If you would like such a policy you would need to learn apparmor or selinux or similar tool. These tools are moderately complex do not come with graphical tools to configure them the way you intend.

---

### Post by nothingspecial on 2010-11-13
@ Shaddarr

What exactly are you trying to restrict?

The specific app may have an option.

---

### Post by Shaddarr on 2010-11-14
> **bodhi.zazen said:**
> The short answer is no.

A somewhat longer answer is there have been some attempts to write such an application for Linux, but I would not advise any of them as they do not work well (IMO). This is not Windows and what the experienced Linux users will tell you is such an application is not needed, or at least the need has not been great enough that such an application has yet been developed.

Even on the Windows side, such applications are not as fool proof as you might think, they are relatively easily defeated.

If you would like such a policy you would need to learn apparmor or selinux or similar tool. These tools are moderately complex do not come with graphical tools to configure them the way you intend.

Thank you for your thorough response. It is unfortunate, but the more I learn about Linux, the more I see that it was not designed with these approaches in mind. I still think *nix is completely wonderful, however.

> **nothingspecial said:**
> @ Shaddarr

What exactly are you trying to restrict?

The specific app may have an option.

There are too many to list here, but for the most part, they are Windows applications. *nix has just as many 'home programmers' putting out their software, trying to get their foot in the doors of companies, giving away their work for fun, etc.; but it seems that there are many more programs (at least from a user perspective) that 'phone home' in the Windows environment. This has been this way for a long time as well. Many programs relay to companies and users' statistics and information that is mostly not harmful, however some collect information and perform actions that are dubious. Stopping all communications from the installation onward is a good way of controlling said possibilities.

My concern was mainly for family members (and other people of course) that are encouraged to move to Linux, especially as it becomes more and more Novice Friendly. These users may not think of protecting their personal information as top of the list, and with background communications not being monitored (or restricted perhaps is a better phrase) it presents a chink in the armor of personal computing usage of Linux. They may try new applications without the thought of what it may do to their systems, and Linux does not seem to have inherent protection for this (as the malicious code distributors on this forum alone has shown).

As stated above and in your apt signature, I realize this, that Linux was not approached with the end user in mind, but with function in mind, usage was second, if you understand my meaning.

As far as this issue specifically, I suppose the best option is to install Virtualbox OSE, throw another instance of the OS in there, and try out any programs as will, without fear then of it affecting the host system (if it has no connection to it). Since Tux Guardian seems to be defunct, I suggest this to all who may read this, and not want new applications they try out to 'phone home'.

---

