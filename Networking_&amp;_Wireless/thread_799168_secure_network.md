---
title: "secure network"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by notesetter on 2008-05-18
Every time I boot, I have to go into System==>Administration==>Network and then select my connection and reenter the password for my secure network. That's a lot of steps to get online every time I boot (I still can't use the hibernate feature on my Compaq Presario Laptop, which I hoped would be fixed in 8.04).

Is there a way to teach Ubuntu to save the password for the secure network?

Thanks,

Dave

---

### Post by redoscar3 on 2008-05-19
Are you using the network manager?  I entered all my authorization info there and now my Hardy setup just connects to my WPA access point automatically whenever I boot or resume from suspend.  This is a bit different from my Dapper and Edgy installs where I had to enter a special password to access the keyring.  I don't know if the Dapper and Edgy were different because I used ndiswrapper whereas with Hardy I was able to use the b43+fwcutter setup.  Mind you, this is on an Acer Aspire 3003 with a Broadcom wireless chipset.  Different hardware, but I would think things should work in a similar fashion.

---

### Post by notesetter on 2008-05-19
I'm not sure now if I'm using ndiswrapper or b43-fwcutter. I tried a few things before I got the wireless card to work.

At any rate, whenever I boot into Ubuntu, I have to open Network from the System==>Adminstration menu. The window that opens up is titled "Network Settings." Is the network manager a separate utility? How do I access it? Do I need to install it from the Synaptic Package Manager?

Thanks again.

---

### Post by redoscar3 on 2008-05-19
The network manager that I use is located on the top panel.  It may actually be the same as accessing through the System > Admin > Network menu items, I'm not for sure these days.  It is called nm-applet 0.6.6 and should be available by right clicking on the panel and selecting "Add to Panel" and then select "Network Monitor" from the list of items.

I did all my network selection and passphrase configuration from there.

When I'm connected using wired ethernet, the icon looks like two small monitors.  When I'm connected wirelessly, it gives a signal strength meter.

Does any of this sound familiar for your setup?

This is in the Gnome environment using a Gnome panel.

---

### Post by notesetter on 2008-05-19
Hi again,

I had the icon you speak of in the panel at the top right, but trying to edit the properties of my connections from there resulted in a message to the effect of "the device does not exist, make sure the name is typed correctly." So I removed that icon and replaced it with "notification area 2.22.1.3." When I left-click it, I can now select "Manual configuration..." and edit my network connections. However, I occasionally find myself unable to connect, and when I investigate, the problem is always the passkey. It seems that Ubuntu (or some other thing) adds 2 characters to the passkey randomly. When I find myself kicked off, the key is 18 characters long rather than the actual 16 characters of my network passkey. I then have to re-enter the passkey, and everything is fine for a while. It usually doesn't happen unless I shutdown/restart the machine, but sometimes it does happen in the middle of a session.

Any thoughts?

By the way, should I be using the "keyring" for this sort of thing? I don't know what that's about, and I haven't used it before.

Thanks,

Dave

---

### Post by redoscar3 on 2008-05-19
Dave,

The "Keyring" issue only seemed to be something I was required to do on my earlier installations of Ubuntu 6.06 and 6.10.  On those I had to use ndiswrapper which was a way to use the Windows XP driver to access my particular hardware.  Like you, I'm not sure why I had to go through that extra step to get connected.  However, with Ubuntu 8.04 it never asked me to register the access for the keyring, and so I don't have to do anything to get connected.

It sounds to me like you can get connected, but you have to reenter your passphrase each time.  So you obviously have your drivers configured for your hardware.  I think that a couple years ago that Linux used to store configuration information in a place like /etc/network/interfaces.  But to be honest, I don't think Ubuntu nm-applet is using this file to store configuration information.

Not knowing how you set up your Ubuntu, it's possible that you have done something to confuse the wireless scripts on where the passphase is stored and how to access that information.  I really wish I was smart enough to tell you where to look for a solution.

Could you completely uninstall the network manager and try reinstalling using the Synaptic Package Manager?  There is just a chance that could get you working properly.  Let me know if that works out for you.

---

### Post by redoscar3 on 2008-05-19
Dave, if you want to try removing and reinstalling the network manager packages, the package names are:

network-manager
network-manager-gnome
wpasupplicant

I'm hoping reinstalling these will get your setup corrected.

Good luck

---

### Post by notesetter on 2008-05-26
I tried removing the network manager and reinstalling it but it still doesn't give me any options for saving my network password and automatically connecting at startup. So I installed a program called "network selector" through Add/Remove and made a panel launcher for it. It allowed me to store the network password and now, whenever I restart, I click the network selector launcher, then select my wireless network from the network selector icon in the notification area. It automatically connects using the saved password.

Not automatic, but fewer steps than before. I may try your suggestion of uninstalling/reinstalling associated packages in the future. For now, I'm good.

Thanks for your suggestions.

Dave

---

