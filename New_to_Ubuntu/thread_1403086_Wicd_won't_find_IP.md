---
title: "Wicd won't find IP"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-02-09
After uninstalling Network manager because of issues with that, I installed Wicd and it's worse. When wicd first started up it found my network as hidden ESSID but after I put in the wep key it starts to connect then stops as it's unable to get IP address. If I click on network to connect to hidden network it has a box for ssid and when I put the name in to connect it just stops and I lose the option to connect to anything. If I refresh the original option to connect is gone. Also there's no option to put in the ESSID in properties and it doesn't ask for a password like Network Manager. Do I have to set up a keyring or something? After reinstalling Ubuntu 6 times in seven weeks I'm about done. If I can't get this network issue solved I'm going to have to call it quits. Please any help would be appreciated. At least I could get connected with Network manager, but I can't reinstall it because I have no internet connection. Thats the reason for a few reinstallations of Ubuntu. Very frustrating.
P.S I have googled and searched for days and can't find an answer.

---

### Post by gordintoronto on 2010-02-09
Why not unhide the ESSID, if only temporarily?

If you can't get an IP address from DHCP, you could set it to a static IP address.  That means you need to specify DNS servers, just use OpenDNS. (208.67.222.222 and 208.67.220.220)

---

### Post by k3lt01 on 2010-02-09
Unfortunately there is no easy fix for this so I will go through a few options I have found myself, and seen others use, in the past.

If you have recently updated Ubuntu there maybe a copy of the Network Manager debs still in your system. Take a look in /var/cache/apt/archives and see if the required .debs are located there. If they are you should be able to simply reinstall them.

Another option I have heard about, but never seen or tested myself, is  program someone from the Ubuntu community developed. I can't remember its name atm sorry, but apparently you can use it to download Ubuntu .debs and all their dependencies through Windows and then install them onto your Ubuntu PC.

You may be able to use the LiveCD, or Alternate CD if you used that, to reinstall Network Manager. Not sure about that though.

If all that fails and you still can't get Wicd to work you will need to do a complete reinstall of Ubuntu. I would then advise you to follow gordontoronto's advice and set the dns to the dns he mentioned.

---

### Post by ThePinkWitch on 2010-02-10
> **gordintoronto said:**
> Why not unhide the ESSID, if only temporarily?

If you can't get an IP address from DHCP, you could set it to a static IP address.  That means you need to specify DNS servers, just use OpenDNS. (208.67.222.222 and 208.67.220.220)

Thanks for reply :) How do I unhide ESSID?

---

### Post by ThePinkWitch on 2010-02-10
> **k3lt01 said:**
> Unfortunately there is no easy fix for this so I will go through a few options I have found myself, and seen others use, in the past.

If you have recently updated Ubuntu there maybe a copy of the Network Manager debs still in your system. Take a look in /var/cache/apt/archives and see if the required .debs are located there. If they are you should be able to simply reinstall them.

Another option I have heard about, but never seen or tested myself, is  program someone from the Ubuntu community developed. I can't remember its name atm sorry, but apparently you can use it to download Ubuntu .debs and all their dependencies through Windows and then install them onto your Ubuntu PC.


You may be able to use the LiveCD, or Alternate CD if you used that, to reinstall Network Manager. Not sure about that though.

If all that fails and you still can't get Wicd to work you will need to do a complete reinstall of Ubuntu. I would then advise you to follow gordontoronto's advice and set the dns to the dns he mentioned.

Hi :) thanks for your reply. I tried getting Network Manager from the cd once before and it was such a hassle I just reinstalled Ubuntu. I really don't want to do it again because I have done it so many times and it takes ages to set everything up again. I think it sux personally that with ubuntu you're kinda screwed if you don't have an internet connection as far as getting and installing programs. It's a nightmare for us beginners. I wish you could remeber the name of the program to get debs it sounds really handy. Anyway thanks I'll check the archives as you have suggested and then try gordontorontos advice.
Thanks guys :)

---

### Post by k3lt01 on 2010-02-10
The program is called keryx, [here's]("http://keryxproject.org/") the direct link.

---

### Post by ThePinkWitch on 2010-02-10
> **k3lt01 said:**
> The program is called keryx, [here's]("http://keryxproject.org/") the direct link.

Oh wow thanks for finding it for me :D Anyway I have reinstalled Ubuntu again but that program will be really handy. Thanks again :)

---

### Post by gordintoronto on 2010-02-10
> **ThePinkWitch said:**
> Thanks for reply :) How do I unhide ESSID?

It's not material now, but it's a setting in your router.  In many cases, the router is at 192.168.1.1, and you need to know the admin userid and password in order to change the settings.

---

### Post by AggravatedGestalt on 2011-01-15
Here I go again. I have posted on this issue before, and received no replies. This is not solved. Another variation of this issue is that WICD has trouble connecting to an encrypted wireless AP, and NetworkManager does not. Now why would this be? Does it happen in any other distro, or only Ubuntu? My guess is only Ubuntu. I have suspicions that someone wants people to use NetworkManager, and nothing else; and this would be an ok idea if NM were to be improved, and display things like channels, and offer more adult oriented information, and not default to automatically connecting to an AP, and more. Why does NM get the IP instantly, and neither WICD nor Wifi-Radar can dependably do so? I have tried this with three diferent wireless chips, and all have basically the same results. So pardon me if you will, but this is not solved. I was under the impression that WEP had not changed too drastically in the last few years.

---

### Post by k3lt01 on 2011-01-15
> **AggravatedGestalt said:**
> Here I go again. I have posted on this issue before, and received no replies. This is not solved. Another variation of this issue is that WICD has trouble connecting to an encrypted wireless AP, and NetworkManager does not. Now why would this be? Does it happen in any other distro, or only Ubuntu? My guess is only Ubuntu. I have suspicions that someone wants people to use NetworkManager, and nothing else; and this would be an ok idea if NM were to be improved, and display things like channels, and offer more adult oriented information, and not default to automatically connecting to an AP, and more. Why does NM get the IP instantly, and neither WICD nor Wifi-Radar can dependably do so? I have tried this with three diferent wireless chips, and all have basically the same results. So pardon me if you will, but this is not solved. I was under the impression that WEP had not changed too drastically in the last few years.Hmmmmmmmmmmmmmmmmmmmmmmm. No wonder people have high blood pressure.

This thread was marked solved by the OP because for them the issue they posted about was Solved. You are having, by your own admission a different issue (the word "variation" automatically indicated a difference). So my advice to you would be to post in the Networking section and ask about your particular problem there.

Oh and there is no conspiracy theory involved, NM is used by Gnome, Ubuntu uses Gnome (until Unity is default anyway) so NM comes by default. If you choose to use Wicd, very bad idea IMnsHO, it may be an idea to google for the Wicd website and see if that has any relevant information.

---

### Post by AggravatedGestalt on 2011-01-15
I guess I set my expectations too high; I have a million available apps, many of them useless, but only one wireless network management application works with Ubuntu without installing things on top of alternative wireless apps (dhcpcd?).. I guess I figured that with such a plethora of stuff, maybe a single (functional) alternative to NM might work without patching, or researching, or tweaking, or uninstalling anything. Or maybe a hint/clue might be included in the repository description? Now I am not convinced, but I still cannot help but think of elitist, exclusive snobs, who covet obscurity, so long as it does not affect them. Since this is clearly not the case, how can I personally contribute to making this bug easier to deal with for myself and others?

---

### Post by k3lt01 on 2011-01-15
> **AggravatedGestalt said:**
> Since this is clearly not the case, how can I personally contribute to making this bug easier to deal with for myself and others?Submit a bug report on Launchpad and follow any instructions given.

---

### Post by AggravatedGestalt on 2011-01-15
That's an excellent suggestion! However, I see that others have done so without any results. After I throw my drop in the bucket, is there anything else?

---

### Post by k3lt01 on 2011-01-15
Do some more research. Google is your friend!

I know what I am saying is probably coming across as me being facetious but there are some things that do get unanswered here because others haven't had any experience with the said issue. At times like these it boils down to the person with the issue doing as much research of their own as they can.

---

