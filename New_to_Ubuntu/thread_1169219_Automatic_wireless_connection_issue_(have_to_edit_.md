---
title: "Automatic wireless connection issue (have to edit to get it to work?)"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by hewittkennedy on 2009-05-24
We have a brand new Dell Mini 9 and right out of the box, I could get the wireless connection to work -- had to find my router, put in WEP key but it worked.

Then for a while when I turned the Mini on, it would not connect.  If I would left click on the Network Manager icon, I would get Wired Network and VPN Connections through Edit Connections menu items, but no radio buttons under the Wireless Networks so that I could choose my network and connect.  For a while, even using Edit Connections wouldn't work, although I could easily have been tweaking settings to the point where I was making it impossible for the wireless to connect, being a newbie.  All this time, my Windows laptop was connecting to wireless just fine.  Harrumph.  At least I used that laptop to find this forum.

Then I think I got it to connect again by using Edit Connections, selecting one of the now two "Auto ROUTERSSID" entries (we have FIOS) and then fixing some setting.  Not sure what I changed that did the trick.  Not sure what I did to make the second "Auto ROUTERSSID" appear either.

Now for some reason, the radio buttons under Wireless Networks have appeared and I can select my router, but still it will fail to connect (tries, just doesn't work).  Then if I go to Edit Connections and select the more recent of the two connections, and click edit, but make no changes at all, and then hit OK, it will connect.

What can I do to make hitting the radio button work for my wireless connection work without having to fake edit the connection?

---

### Post by davidce on 2009-05-25
I, too am writing from a Dell mini 9, and I too got windows to communicate with my wireless Motorola Surfboard.  But ubuntu just gives me options that are incomprehensible.  What's SSID? What does VPN mean?  I think I've bitten off more than I can chew.  This is not a friendly environment, where you have to build everything yourself...  Are there really people out there who enjoy recreating wheels?  May god help them get a life.   I just want to use ubuntu to do some text stuff, and get onto internet.  If you get any help, please let me know.
davece

---

### Post by Miljet on 2009-05-25
Usually connecting to the internet is as simple as clicking on the internet icon at the top right of your screen, putting a tick beside your network name (which is known as the SSID), entering your network passphrase, and finally entering your login password.

If you have gone into the network manager and made a bunch of changes, you may have some cleaning up to do before it will connect automatically.

---

### Post by hewittkennedy on 2009-05-25
Thanks Miljet for explaining what to expect.  That made me realize that having two "Auto ROUTERSSID" entries was the problem.  It would try the one that had a bad setting in it first, where the bad setting must have been the totally weird WEP key that I did not enter, but might be how the real key was converted from WEP 128-bit passphrase to WEP 40/128-bit Key, a setting I remember tweaking.  [Note to davidce:  I don't understand what I just wrote, just that I know it worked by trial and error and taking notes so I could remember exactly what I'd done when it worked.]

I deleted that entry from Wireless list, and then tried again.  This time, it asked for the key when it tried to connect; I entered, but it didn't work.  The setting that was different was Authentication (default was "Shared key"; changing to "Open system" made it work -- this was the one setting shown in the dialog box for which I was't confident it was correct, and there were only two choices).

This again meant I had two "Auto ROUTERSSID" entries, so I deleted the older one and rebooted.  Now it works automatically, which is what I was after.

To davidce:  I recently got FIOS and the installer left me with a booklet that specifically listed my SSID, which is the router's name (it's one of the connection possibilities that shows up, along with what I recognize as my neighbors router names).  The WEP key is the password to the router, if you will.  Miljet has a different version of Ubuntu than I do, but his/her advice gave me confidence to keep plugging away.  If you really bought your computer direct from Dell with only Ubuntu loaded, then we have the same machine; what could still differ is how you connect:  I assume wirelessly, but if you give more details about your router (DSL? cable?), I'll bet someone, maybe even me, can help.

---

### Post by Miljet on 2009-05-25
Glad to hear that you got yours working. And thanks for posting what worked for you. That is sure to help someone else.

---

### Post by hewittkennedy on 2010-01-24
Aha!  I now know what happened that caused me to post my question:  I successfully connected the first time, but then about two weeks later, the update manager installed a huge number of updates and I had to reboot.  The first time I rebooted, I'll bet I wasn't paying much attention and checked the "Allow one time only" instead of "Always allow" in the dialog box the first time the computer tried automatically to connect the wireless.  I have no idea why it asked me this question, but that's where the problem began.  

Unrelated to my original post, I recently had a still-under-warranty hard drive failure, and had to replace it, which also meant restoring Ubuntu. And having update manager do the same thing a few weeks later.  Having to go through this all again, I instantly recognized where my original problem began!

I often check "this time only" on the theory that I'll get a future opportunity to check the "always" button when I will have more time to think through the implications of various answers.  That didn't serve me well here!

---

