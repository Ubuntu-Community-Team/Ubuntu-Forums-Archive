---
title: "Network Connewctions"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by 2roombas on 2009-03-14
Why do I see the word "never" in the Network Connections dialog by my connection?  Clicking Edit I still cannot change that never it seemd.

I'm trying to get my laptop connected to the internet now after my full install of ubuntu?  Somehow it was working just fine before when I was dual booting, but now after nixing windows I'm having trouble. Not real sure what I did before to get it going.:confused:

---

### Post by newbee70 on 2009-03-14
Have you researched your problem.

try this link.

[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)


And <b> Welcome to Ubuntu and the Forums, where many great people will help you out. </b>

---

### Post by 2roombas on 2009-03-14
Hmmmm... I see the problem, but not sure what to do about it?! :  Help!

I have three computers and 2 have Linux ubuntu on them now.   My dell mini has 8.04 and connects to my wireless just fine. When I had 8.04 on my laptop, it too was connecting just fine.  This a.m. I installed 8.10 on my laptop and now I cannot connect.  I have looked at the "network connections" of both and see the dialogs are set up different. The 8.04 has the "hex" option but the 8.10 does not.  That (hex option) was what made it connect before. Does this mean I need to turn around and downgrade my 8.10 to 8.04 again, or is there a fix for this?

---

### Post by 2roombas on 2009-03-15
Well, I thought I found the fix to my problem after searching these forums and finding a guy wit the same trouble. Here is what he did.. I tried this but.... How can it update if there is no connection? I tried it anyway, nothing.
[I]
"Plug computer into Ethernet, go to system>administrator>update manager and update your computer. Once it is done restart computer. Now go to system>administrator>Hardware drivers and activate all that's there, ie the Wireless card and the graphics card."
[/I]

When I right click the computer icon the **Wired Network**, **Auto etho **and **Wireless Networks** is grayed out and un-clickable. 

Yes, on left click **Enable Networking** is enabled, so is **Enable Wireless.**

As I said before, this version on my laptop does not have that "hex" option that I had before the full install and had it connecting with no problem. In this version the only options available in the Wireless Security tab

None
WEP 40/128-bit Key
WEP 128-bit Passphrase
LEAP
Dynamic WEP (802.1x)
WPA & WPA2 Personal
WPA & WPA2 Enterprise

I really would appreciate some help, please?  Thanks.  Am I not providing the correct info?

---

### Post by Bucky Ball on 2009-03-15
If you can, plug in an ethernet cable then get your updates, go to System->Administration->Synaptic package manager and search for 

ubuntu-restricted-extras

Install and wait for awhile. If you are not offered the restricted drivers for your wireless card, go:

System->Admin->Hardware Drivers and check to see if there is a driver available for your wireless card. You are going to need to get that up, blue light on, before you can connect to your router or wireless device. :)

---

### Post by 2roombas on 2009-03-15
> **Bucky Ball said:**
> If you can, plug in an ethernet cable then get your updates, go to System->Administration->Synaptic package manager and search for 

ubuntu-restricted-extras

Install and wait for awhile.

I did this and couldn't find that?! 

>  If you are not offered the restricted drivers for your wireless card, go:

System->Admin->Hardware Drivers and check to see if there is a driver available for your wireless card. You are going to need to get that up, blue light on, before you can connect to your router or wireless device. :)

When I did this the only driver listed is "wi"   ... and it says "this driver is activated and curently in use."

---

