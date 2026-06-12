---
title: "Installing on an Acer Aspire Laptop"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by konini on 2010-03-31
Hello everybody

Firstly I'd like to apologise if this has been covered previously - I'm on a very slow dial up connection in Cambodia and searching isn't working for me.

I've been using Microsoft since DOS3.1 but have been convinced to make the switch. I've downloaded 9.10, but now I think I may have made my first mistake as I just noticed 'Desktop' in the file description.  My machine is a notebook not a netbook, not sure if that makes a difference and would be grateful if someone could advise me if I have downloaded the wrong file. I have an Acer Aspire 4730Z.  Also, as a complete beginner, would I be better with Kubuntu?

The thing that concerns me most is drivers.  I sent an email to the Acer help desk asking if there was a download location for drivers, and their response was 'we don't support Ubuntu' - pretty much letting me know I'm on my own.  I'm sure there must be a way - after all, you people are all using it.   I just don't know what to do,  as I said I can't browse because of the slow connection; I leave the machine on and it downloads big files overnight.

Sorry that these are such a lame questions.  I may have been using computers for almost 30 years but this is my first time with a different system for 25 of those years, and I was a lot younger then with better memory and logical skills.

Thank you in advance for any help anyone can give me, also any undocumented tips - I tend to be one of those people for whom if something can go wrong, it will.

---

### Post by k33bz on 2010-03-31
You have the right version downloaded, now as far as drivers, best thing to do is try it out on your notebook as just a live cd. you will see what will work right out of the box and what may need some tweaking (which we will help you with here).

---

### Post by k3lt01 on 2010-03-31
I use an Acer Extensa and my father uses an Acer Aspire 5100. In my experience Acer support is nothing short of useless even for Windows. My father's laptop currently has the amd64 version  of 9.10 on it. Desktop just means normal. Server, well, means server. NBR is Netbook Remix. You have the right version with Desktop. As for drivers unless there is a drastic change in Acer laptops over the last 3 years you will be fine for drivers. Having said that I agree that it will be best to use the LiveCD first, in other words don't install it yet, just to make sure things are ok.

If you need any more help just post here again and we can help you as you go.

---

### Post by konini on 2010-03-31
Wow - so fast and so helpful.  I'm going to have to wait until the weekend, but I'm going to have a good try at this.  I've decided it's either Ubuntu or go over to the Dark Side and get a Mac.  Mac = lots of dollars, so I'd really rather not.

 Thank you both.  I really appreciate it.

---

### Post by coffeecat on 2010-03-31
I've just done a quick search of the forum, and there are a few people posting with an Acer Aspire 4730Z. It seems that most of the hardware will work with the inbuilt drivers. But, as others have said, see how Ubuntu runs in live mode from the CD. That way you can test the hardware before committing yourself to a hard drive installation.

But to comment on a couple of points:

> **konini said:**
> I'm on a very slow dial up connection in Cambodia and searching isn't working for me.

Almost certainly the inbuilt dial-up "modem" is unlikely to work - at least not without a lot of tweaking and fiddling. This is because >99.9% of Windows machines come with so-called winmodems. Here's a useful link to give you more background (and with links for getting some winmodems to work):

[https://help.ubuntu.com/community/DialupModemHowto/GeneralDiscussion](https://help.ubuntu.com/community/DialupModemHowto/GeneralDiscussion)

> **konini said:**
>  would I be better with Kubuntu?

Kubuntu comes with the KDE desktop, which some people prefer. Ubuntu comes with the gnome desktop which is perhaps a little easier for newcomers. You may come across people saying that KDE is better for newcomers because the desktop is more like the Windows one. True - in its default configuration it has a button at bottom-left with a main menu but there, in my opinion, is where the similarity ends. :wink:

---

### Post by Peter09 on 2010-03-31
My son and I have installed Ubuntu onan Aspire One, no problems. The only hickup was that the wireless does not work until you do an update through the hard wired connector. I think it needs to download the driver from the repositories.
 
Edit: We both installed the netbook remix version which is great for the aspire one.

---

### Post by roger_1960 on 2010-03-31
Hi

I would reiterate coffeecats comments about dial up modems.  They often can be made to work, but with quite a bit of fiddleing about.  Make sure you find out what your modem is before deleting windows (or dual boot).  It may be wise to save a copy of the windows drivers for the modem on a CD for use later if needed.  Beware buying a Macbook - they are great (I think the OS is about as good as Ubuntu, but the hardware is superb) - but they don't have dialup modems built in!

---

### Post by conradin on 2010-03-31
> **k3lt01 said:**
> I use an Acer Extensa and my father uses an Acer Aspire 5100. In my experience Acer support is nothing short of useless even for Windows. My father's laptop currently has the amd64 version  of 9.10 on it. Desktop just means normal. Server, well, means server. NBR is Netbook Remix. You have the right version with Desktop. As for drivers unless there is a drastic change in Acer laptops over the last 3 years you will be fine for drivers. Having said that I agree that it will be best to use the LiveCD first, in other words don't install it yet, just to make sure things are ok.

If you need any more help just post here again and we can help you as you go.

Nope Acer still sux. I I owned an Acer Aspire 4730Z. It came with vista, and still lacked drivers when it was brand frikin new. I seem to recall that the atheros wifi card gave me trouble in both Linux and everything else. a Few months later the think fried. (the way they design their heat sinks is a fail waiting to happen.)

in any event, conical will send you a live CD of your choice if downloading a ubuntu version is not fitting for you.

---

### Post by TBABill on 2010-03-31
I have the same model of Acer Aspire (4730z) that I have run Ubuntu 9.10 on. Mine is a US version and I am unsure if that matters with the model being the same, but it's a 14 inch display with Intel video and unsure if Atheros or Broadcom wireless adapter.
 
Anyway, it installed fine with Ubuntu and did not need to be tweaked to get it up and running. The video resolution was picked up automatically at 1280x800. The wireless adapter did not work immediately. But all I had to do was install the system, then plug into my router and do a system update. After the update the system prompted me that their were proprietary drivers available and I clicked the icon and installed (it will be on the top panel to the right by the speaker icon when it prompts you or you can click through the system/hardware menu and do it manually).
 
That was it for me. Everything else just worked, including sound. Try out the LiveCD first, of course, and if it runs ok then you can trust the install if your model matches the hardware found on the 4730z sold in the US.
 
Best of luck to you!

---

### Post by undecim on 2010-03-31
A lot of companies will say "we don't support Linux" or "we don't support Ubuntu"

What that means is that they don't spend their time checking to make sure that it works. Fortunately though, most of the companies they buy hardware from to use in their laptops will either create Linux drivers, or release hardware specifications, which the Ubuntu and Linux developers can use to create drivers.

Also, using the live CD, you can try it out first and see if it works! And even after you decide to install it, you can dual boot and have Windows to fall back on for example, if your dial-up modem doesn't work.

In other words there's nothing to lose by trying it out.

---

### Post by KdotJ on 2010-03-31
I run Ubuntu 9.10 on an Acer Aspire and it works perfectly (in my eyes atleast). No issues with wireless adapter driver, sound drivers, video drivers, everything worked mostly straight out the box.

I hope you're as lucky as I am with it, and I hope you enjoy the switch

---

### Post by acemanollie on 2010-03-31
my friend had one issue. his mic would not work.

---

### Post by k3lt01 on 2010-03-31
> **TBABill said:**
> Atheros wirelessHas been supported ootb since Jaunty (9.04). Before Jaunty there was a little bit of fiddling but thats not the case any more.

> **TBABill said:**
> Broadcom wirelessUnfortunately I don't know what the situation is with the Broadcom wireless set. Maybe others do but I'm pretty sure Acer uses Atheros right through the Aspire range.

---

### Post by TBABill on 2010-03-31
k3lt01, I checked when I got home and the Aspire does have an Atheros wireless chip, but my Acer Extensa has a Broadcom. I wasn't sure which was which from work and with my horrible memory I won't remember next time either :)

---

### Post by k3lt01 on 2010-03-31
Unfortunately I think all Extensa's need Ndiswrapper and Windows drivers. I may be wrong but mine certainly does.

Aspires on the other hand are a different matter. My dad's machine has had to have 3 different setups since 8.04. 8.04 = ndiswrapper, 8.10 = madwifi, 9.04 and 9.10 work ootb with the kernel having the correct driver already in it.

---

### Post by konini on 2010-04-02
Once again, a huge thank you to everybody.  We'll only be in Cambodia for another few weeks, so hopefully the modem will be something I'll never have to use again. As a point of interest, I never ceased to be surprised how much optic fiber they've rolled out here - now they just have to get the population computers and the villages connected to the electricity grid! (And that, by the way, isn't a  joke).

Kubuntu sounds like it's the way to go - my husband has no interest in computers and sees their only purpose as being for reading the newspapers when we're away from home and getting football results, all clickable icons that I've placed on the desktop for him.  Command line would never go well with him, which is partly why I've been putting this off for so long (that, and I'm lazy, not to mention having not used command line myself for more years than I care to think about).  My main concern was internet (how could one survive without it?) and I'm currently using a Ralink driver as the others, includng Broadcom and Athelos, that came in a pack I downloaded last year woudn't work.

I use drive imaging software, so no matter what kind of mess I make I can restore my Windows partition to the day I bought it and get back online and come back here for advise.  

One final question here - I don't have a CD/DVD with me and don't think the village store will stretch to that kind of stock - can I do the same with a USB stick drive?  Can't see why not, but I think I said that if it can go wrong for me, it will.

Thanks again for the responses  - you're all very kind.  It may be a little while - I think I'm going to wait until I get into a bigger town before I start playing around so much.

---

### Post by k3lt01 on 2010-04-02
[This thread]("http://ubuntuforums.org/showthread.php?t=1288604") may be of interest to you with installing from a USB flash drive.

---

