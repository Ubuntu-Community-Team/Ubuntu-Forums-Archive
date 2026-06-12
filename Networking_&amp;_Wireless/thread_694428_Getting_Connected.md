---
title: "Getting Connected"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Dancing Bear on 2008-02-12
I decided 3 days ago, rather hastily, to switch to Linux from Vista. I predicted, correctly, that my number one problem would be the most important one: getting connected once I switch over. I can learn and solve problems by using the internet, but I just can't get on the net. I've tried everything I know to try, and I need help! Here are the specifics. 

- my machine is a gateway laptop running windows vista premium
- I normally connect to an adsl line through a wired router. I have a connection set up with my login and password, and have to connect everytime I turn on the computer.
- I successfuly burned an Ubuntu ISO CD which the computer boots from if it's in the drive. I did not wipe vista yet, mainly because I was expecting this problem. I am assuming that once I do figure out how to get Ubuntu connected, I can wipe this nasty OS off the machine, and start up from my Ubuntu CD. Is that true? 
-Once running Ubuntu from the CD, I opened up the terminal and typed in:

            sudo pppoeconf

I then followed all of the steps that the manual(s) outlined. I entered my username and password, I answered yes and no to the questions as directed. It even told me that the connection was triggered. When I tried to check it with "plog" it told me that the connection was rejected, twice. So it contradicts itself. I was also unable to connect through firefox. 

I tried some other things, but, not to ruffle any feathers out there, there isn't a lot of coherency in the support sector for linux. 

I want Ubuntu! I just need my internet connection going. Any help would be appreciated. Thanks!

---

### Post by banewman on 2008-02-12
Being adsl you shouldn't be worrying about anything ppp
if you go to system - admin - network in your menu you should have an eth0 listed - your wired broadband - make sure that is enabled.
:)

---

### Post by Dancing Bear on 2008-02-12
[QUOTE]Being adsl you shouldn't be worrying about anything ppp
if you go to system - admin - network in your menu you should have an eth0 listed - your wired broadband - make sure that is enabled.
[/QUOTE

I have done that, and it doesn't seem to recognize my ethernet. 

If I do have ADSL, is there a set procedure to follow in the ubuntu documentation? Cuz that's what I thought I had followed up to this point, and why I was doing PPPO. 

My computer has a Marvell Yukon 88E8038 PCI-E Fast Ethernet Controller. I have an ethernet cord going from this to a 4 way wired router, which then connects into the wall.

---

### Post by banewman on 2008-02-12
It seems that that card isn't supported by the kernel - you'll have to go to the makers website and find the appropriate driver and install it.
Sorry...

---

### Post by Dancing Bear on 2008-02-12
> **banewman said:**
> It seems that that card isn't supported by the kernel - you'll have to go to the makers website and find the appropriate driver and install it.
Sorry...

I have the linux drivers for that modem. Do you have any advise on how to install it? I'm completely new to linux, and everytime I do something, I have to shut down Windows Shista, and restart in Ubuntu. So any failures that can't be resolved within a non-connected Ubuntu require me to make the journey back to Vista.

---

