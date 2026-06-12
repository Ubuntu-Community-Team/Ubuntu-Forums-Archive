---
title: "I'm struggling witht the basics but need to understand Networking"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by divadp on 2010-05-24
I am in day two of Ubuntu.

I am a confident IT user however not a teckie. 

My experience so far is that I have returned to life in the tme of dos. I fear if I carry on with Linux I face a steep learning curve. Adding a ubuntu machine to an existing network is a first step, but seems daunting.

My aim in putting Linux on my laptop was to avoid having to buy a copy of windows. I want to add a wireless router  to my peer to peer windows home network (XP and vista) and work from the garden with the ubuntu machine. Having had a quick look at what this involves scares me stiff. I couldn't get windows to recognise the ubuntu laptop on the wired network, and in reading a few comments this part seems fraught with difficulty let alone the prospect of getting the wireless bit to work.

The question is. How difficult is this going to be for a Newbie (who struggled to network windows xp and windows vista), given that quite technically competent sounding people on the forums are struggling to get networks to work and wireless networks particularly? In what order should I approach this? What is the best source of info?

Thanks

---

### Post by 3rdalbum on 2010-05-24
What internet connection do you have? Your best option is to buy a wireless router that will also act as a gateway (modem). Then literally all you have to do is:

1. Hook up your wired clients to the router, via Ethernet cable
2. Provide your ISP's settings to the router (all this configuration is done through a web-based interface - you can access it from one of your wired computers, and there will be instructions provided with the router)
3. Set up the wireless side using the web-based interface; you tell it what name (SSID) to have for the network, what encryption method (choose WPA2 Personal) and what password.
4. The Ubuntu machine will start picking up the new wireless network in the Network Manager. You can then click on the recognised network and it will connect.

---

### Post by divadp on 2010-05-24
Thanks for your prompt reply.You make it sound re-assuringly simple.

I have an adsl internet connection through a wired modem/router (netgear) and I hoped to link the linux machine into this wired network as stage 1. I also have been given a netgear wireless router and I hoped that I could add this to the netgear router and only power it up when I wanted to work wirelessly with the laptop in the garden stage 2.

Have I confused myself by reading about samba? and command line instructions?

Is just buying a wireless modem/router going to save more in time than it will cost to buy (my time is cheap at the moment as I'm not working!)

D

---

### Post by bredman on 2010-05-24
Everything that you learned for Windows networking is exactly the same  for Linux networking, so you won't have to learn any new concepts.

Adding a Linux machine to a network is no more difficult than adding a Windows machine, with the exception of wireless. For most laptops, wireless should work immediately, for others you may have to ask for help. I know of very few types of hardware where it is very difficult to set up a wireless network.

You started in the correct manner, it is easiest to test a wired network first and then move onto a wireless network.

You say that the Windows machines could not recognise the Linux machine on the wired network. This is because by default, a new machine does not expose any services on the network. You have to make something available for it to be seen. For example, in Ubuntu you can make a folder visible on the network by right-clicking on a folder and select "Sharing Options".

---

### Post by divadp on 2010-05-24
I wasn't planning to set up the network now, however I did try setting my folder for sharing only to be told I needed the windows networks sharing service.

I would have thought this would be 'in the box' Do the developers read these threads do you think?

As I said every step is going to need a 'learning process' and I am a bit wary of stumbling down a path I might regret without planning ahead and reading up a bit.


David

---

### Post by bredman on 2010-05-24
When you try to share a folder, you will be offered the choice to add the software to interact with Windows computers. You should accept the offer and all will work well.

This is not included by default because everybody does not need it. It is only useful if you need to interact with Windows machines. You will notice in Linux that not everything is delivered by default because it is impossible to predict what everybody will need. The extra software is just a click away if you need it, you don't have to search the internet like you do in Windows.

---

### Post by eriktheblu on 2010-05-24
Ubuntu, targeted toward your normal computer user doesn't place multi-platform networking as a high priory.

Your typical Windows install isn't compatible with Linux network protocols either.

I believe the default Ubuntu setup can connect with Windows shares.

---

### Post by divadp on 2010-05-24
I'm still struggling and looking at the help threads I'm not the only one trying to do this as a newbie, and in fact some of the struggling newbies seem to be quite competent IT people.

I appreciate that linux is new and different for me and does stuff differently, however I think the profile of people moving to linux is very much the person who might want to link computers together at an early stage.

So on to my problem. I have now opened my file for sharing on the ubuntu laptop,downloaded something as told to (Samba?) done some pinging to establish that the network connections work - and they do. I just seem to be walking through treacle. I have found out about network manager from other threads, and like them I don't have it on the panel although it is installed so can't go into it. I have found "network tools" and network connections, but never seen network manager which I presume is why I can't get it all to work.

By the way this is just a peer to peer I'm doing - am I getting confused by 'client server'?

What to do?

---

