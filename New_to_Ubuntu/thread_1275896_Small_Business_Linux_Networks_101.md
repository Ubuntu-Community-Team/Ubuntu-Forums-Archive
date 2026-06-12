---
title: "Small Business Linux Networks 101?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by JoJerome on 2009-09-26
So a friend and his business partner are starting a mom-and-pop sized custom motorcycle shop and have asked me to be their in-house geek. Which is great, but it's been a VERY long time since my degree or latest experience in such work and I've never set up a Linux network.

But being that the business is starting from scratch I'm hoping to start right ... i.e.; Linux Baby!!!

To start we're probably looking at about 3 PCs; front, back office and workbay. Plus our personal Windows and Mac laptops will want to talk to the network. Probably involve little more than network and filesharing to start with and some basic small business management/accounting software. But the idea is to be able to grow as the business (hopefully) grows. 

So, some questions for you experts out there from this humble Jedi apprentice: 

- The one Linux distro I've used myself is Kubuntu. So being that's the one I'm already a little familiar with, is Kubuntu/Ubuntu feasible for such a venture or should I really look at a different flavor of Linux?

- Any good Linux Networking 101 books to recommend? I've always really loved the "Sam's Teach Yourself..." series for their simplicity and ease of use. 

- Any good Linux Networking 101 online courses/sites to recommend while I'm waiting for the book(s) to arrive?

Thanks in advance!

---

### Post by powel212 on 2009-09-26
A little tutorial[http://ubuntuforums.org/showthread.php?t=1233071&highlight=config+samba]("http://ubuntuforums.org/showthread.php?t=1233071&highlight=config+samba")

I hope that helps

Powel

---

### Post by bodhi.zazen on 2009-09-26
Sounds exciting. You are asking about a very broad topic. I suggest you look into the areas you need. The one thing I see you specified is file sharing, for that I advise Samba.

What else do you wish to do with the server ? Are you looking to do a web site / advertisement ? for that look at Apache.

---

### Post by pauna on 2009-09-26
I own a small business of my own, but my setup would not be of any use to you. But from experience I'd say, that you should create a small back-office server, which is a centralized location for all files and services etc. 

As for the actual software, see if Amahi fits your needs: [http://www.amahi.org/](http://www.amahi.org/)

---

### Post by JoJerome on 2009-09-26
Thanks for the replies so far!

- Samba: Being a favor of Ubuntu I trust it's similar/as easy as Kubuntu? (If you can't tell how much LOVE Kubuntu...)

- Website: I'm doing that too (Ahhh, feels good to be geeky again!). But for now at least it will be hosted remotely for simplicity sake. From what I hear though, if ever I decide to run the server myself, Apache is the way to go.

- As for basic setup, I kind of figure the back office would be the primary server. But again, to get started I don't see needing much more than a bare-basic ability to share files and run some (hopefully) simple small business software (accounting, inventory, etc). 

- Having never been the grand network poobah myself, but having worked in a variety of small businesses and office settings, I can't get over how horribly complicated some feel they have to make their setup. I for one would like to be able to go on vacation and know that my network is easy enough to walk someone through problems over the phone while I'm sipping margaritas on the beach. 

Well, ok, I might be dreaming for it to be *that* easy, but you get the idea. Start out simple and basic, grow from there. And hopefully impress but not frighten my not-computer-savvy business partners. 

:KS

---

### Post by bodhi.zazen on 2009-09-26
Samba is not a version of Ubuntu, Samba is a server (like apache) that allows file sharing between Linux and Windows.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

It seems complicated at first, but it is not too bad =)

---

### Post by JoJerome on 2009-09-26
*"Samba is not a version of Ubuntu, Samba is a server (like apache) that allows file sharing between Linux and Windows."*

Ahhh, gotcha. Thanks again for the replies and advice. Another friend via email is telling me it's not too terribly tricky to set up a Linux network but let those users who must have Windows run Windows. He also said Ubuntu should be fine as an OS. 

For now though, I don't think we're there. 

I've ordered "Beginning Ubuntu Server Administration: From Novice to Professional." Based on a few reviews at Amazon it looked like a not-too-risky bet.  If anyone has a favorite book or tutorial-for-absolute-beginners site, do let me know!

It is quite exciting and I'm honored to be invited in on the ground floor of this business (they do actually have some clients already - just need a storefront). I told them I'm rusty as hell, but I think it's the kind of deal where they'd rather have a friend who's rusty but whom they know and trust and will work for peanuts as I grow with the business. 

Thanks again for the continued help - I'm sure I'll be back here a lot!
:)

---

### Post by bodhi.zazen on 2009-09-27
Don't worry, you will learn fast. If you get stuck, come on back.

---

### Post by mapes12 on 2009-09-27
There are many posts advocating Samba for Windoze shares but in my experience it can be hellish to configure. If you simply want file sharing between windoze and Ubu then I find PyNeighborhood very simple to set up and easy to use. This is what I do:

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

BTW - if you're running Vista or whatever the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is the MS end of line from now on..........

---

### Post by JoJerome on 2009-09-27
Thanks Mapes - To start, I'm hoping to talk them into using Ubuntu/Kubuntu exclusively for the shop, though I know at the least their personal Windows laptops will want to talk to the network and at the most, someday someone will say "I've just gotta have Windows on this particular workstation."

Pauna - browsed the Amahi site you pointed me to. Wow, powerful-looking software! I'll definitely look into it.

Bodhi- Yes, started browsing networking tutorials and thumbing through a book or two. Like riding a bicycle it's all coming back to me now. I'll definitely be back for advice and "Help! I've fallen and I can't get up!"
:)

---

