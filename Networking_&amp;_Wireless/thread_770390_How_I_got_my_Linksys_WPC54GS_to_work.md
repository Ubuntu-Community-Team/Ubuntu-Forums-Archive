---
title: "How I got my Linksys WPC54GS to work"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by AWCADDET on 2008-04-27
Hey all, first actual bit of help I've given out, because frankly, I am very new to this, making me a n00b =)

OK so after spending all of last night researching how to get my card working on the new **Ubuntu 8.04**, and with no prevail, I decided to give it one last shot before I was swapping back to XP, and what did you know... It worked!

Please bear in mind I have no idea if this will work for you, And I only tested it with a **WEP** key. So **Good Luck** if you decide to use this.

**[SIZE="3"]What You Need To Start[/SIZE]**
- Preferably a fresh install of Ubuntu (Or just make sure you remove any old installs of ndiswrapper)
- A Linksys WPC54GS Wireless card (Other cards might work with this method as well)
- A Router + Ethernet Cable
- A cup of coffee
- Patience

**[SIZE="3"]Getting it to work[/SIZE]**

**1)**
Boot unto Ubuntu, Disconnect your Wireless card and connect up your Ethernet cable to your laptop, Now you have wired access to the Internet.

**2)**
Open up Synaptic Package Manager
[INDENT][INDENT][SIZE="1"]>System
>Administration
>Synaptic Package Manager[/SIZE][/INDENT][/INDENT]
And click on the **Reload** button. This will update with the latest repositories, depending on your connection speed this can take a while.

**3)**
Search for **ndis**, and scroll down until you see
[SIZE="1"][INDENT][INDENT]- ndisgtk
- ndiwrapper-common
- ndiswrapper-utils-1.9[/INDENT][/INDENT][/SIZE]

Select all three of these, and mark for install.
Now click apply and let it download + install them for you.

**4)**
Download the correct windows driver for your card from the Linksys Website. If unsure about which version, check the back of the card.
 Just save it to your desktop for now.

**5)**
Make a folder in **Home** and call it **Linksys**
Open up what you have just downloaded, and drag + drop the **.sys** and **.inf** files to the **Linksys** folder.
   To make life easier rename the .inf file to **linksys.inf**

**6)**
Open up the Terminal
[INDENT][INDENT][SIZE="1"]>Applications
>Accessories
>Terminal[/SIZE][/INDENT][/INDENT]

and enter "**cd Linksys**" (Without Quotes)

**7)**
Now enter
"**sudo ndiswrapper -i linksys.inf**"

**8 )**
Now enter...
"**sudo modprobe ndiswrapper**"

**9**)
Ok, now we want to update the Hardware Driver; This method could be done differently, but to ensure it got detected I did it this way.

- Unplug the Ethernet cable (You are now disconnected from the Internet)
- Insert the WPC54GS card into the slot
- Wait for the **Hardware Drivers** tool to pick it up

Now you should be looking at a window containing a **Device Driver** for **Broadcom B43 wirelessdriver**

**10)**
Now we need the Internet again, so follow these steps

- Reconnect the Ethernet cable, and wait for it to connect.
- Click **Enable** for the Device Driver in the other window, and click yes/forward to whatever it asks you to do.

When this is finished, and it tells you it has been enabled, move onto next step.

**11)**

Now you can

- Disconnect your Ethernet cable, and roam around for your Router
- Enter the WEP key (If any) and **enjoy wireless Internet with your WPC54GS card.**


**[COLOR="Red"]Like I said, I am still very new to this, sorry if you lot think this is the wrong way of doing it, or if there is a quicker method. I am just sharing a route which worked for me.[/COLOR]**

---

