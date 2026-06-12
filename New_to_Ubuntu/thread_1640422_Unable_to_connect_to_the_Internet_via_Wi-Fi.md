---
title: "Unable to connect to the Internet via Wi-Fi"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by jamieb234 on 2010-12-07
Hi there, 
I am really stuck with a problem on my machine and would really appreciate some advice.

I have a Windows laptop which also has Ubuntu Linux 10.10 installed onto it and I would like to start using Linux a lot more and learning about the system.  However, I am having trouble connecting to the Internet in Linux.  I use wireless Internet at my home and when logging onto Linux, the laptop is recognizing the WI-FI point in the house and it asks me for the pass code to allow me to connect.  When I type the pass code, the laptop does not connect in Linux and the box re appears asking me for the pass code once again. 

I am able to connect to the Internet via Windows with no issues, no errors are thrown regarding the passcode that I have set for to the router. I have tried this on another Windows laptop in my house and once again, I have been able to connect to the Internet with no trouble, the issue only seems to occur on Linux. 

Has anybody else had this problem?  I have been searching for advice online for a while and can't seem to find the correct solution to my problem, any ideas?

Thanks!
Jamie

---

### Post by gordintoronto on 2010-12-07
Does it keep asking again and again, or just twice?

I prefer to right-click on the network manager icon and select "edit connections." That opens a small window, I select the wireless tab and the add button, and enter the ssid, then the security information.

---

### Post by uriel1998 on 2010-12-07
I had borked mine for a while by trying to add DNS servers manually (following directions from OpenDNS, oddly enough, and I recommend them for everything else).  If you've specified things like DNS servers or gateways, try UNspecifying them - or even deleting the connection and starting over.

---

### Post by jamieb234 on 2010-12-08
It happens everytime I try to connect to the internet through the wireless router. 

I have also tried to remove the connection and then adding the connection again, this still did not work, however I will try the suggestions you guys have provided.

Is there a possibility that this could be something to do with the type of pass code I have assigned to the router?  It currently requires a WPA2 pass code, would changing this work?

Sorry if these suggestions seem unusual but as I say I am a noob to Linux lol.

Thanks

---

### Post by rx007 on 2010-12-08
Hello jamieb, 

please check your wifi setup if its wpa / wpa2 security. also check your encryption type tkip/aes. if it matches your settings in your windows, it will connect.

regards,

---

### Post by jamieb234 on 2010-12-08
Hello again, 

I have tried all of the above suggestions and I'm still getting the same problems :( 

I tried to add the connection manually but this did not work, I also tried to match the connection details to those that are on Windows. 

Everytime I typed the passcode into linux, it tries to connect and then comes back with a box stating that authentication is required by the network and it asks me to type in the WPA2 personal code in again, everytime I type this in the same just keeps happening and I become stuck in a loop.  

The encryption type is set to AES on Windows but when amending the network options in Linux 10.10 there is no mention of encryption type.

I would be very grateful for any further suggestions
Thanks

---

### Post by uriel1998 on 2010-12-08
> **jamieb234 said:**
> Hello again, 

I have tried all of the above suggestions and I'm still getting the same problems :( 

I tried to add the connection manually but this did not work, I also tried to match the connection details to those that are on Windows. 

Everytime I typed the passcode into linux, it tries to connect and then comes back with a box stating that authentication is required by the network and it asks me to type in the WPA2 personal code in again, everytime I type this in the same just keeps happening and I become stuck in a loop.  

The encryption type is set to AES on Windows but when amending the network options in Linux 10.10 there is no mention of encryption type.

I would be very grateful for any further suggestions
Thanks

Have you ever gotten it to connect with a no security or a different type of security?

---

### Post by jamieb234 on 2010-12-09
Hi uriel1998,

I was talking to a friend of mine from work and he suggested the same thing, I am going to find the windows cd that I used to connect to the router and adjust the security so that there is none on it, then I will upgrade the security one at a time to try and find the right type of security on Linux. 

Thanks for your help, I will update once I have tried. 

Jamie

---

### Post by sirkeith on 2010-12-09
I have a fairly new Toshiba laptop that was pretty good with Windows 7. I installed 10.04 and 10.10 from a live cd and one of my problems was wireless wouldn't work I tried just about everything I and others thot of. Finally I downloaded Maverick from the PPA's with 2.6.36. kernel and everything works. I kept 10.10 on 2.6.35 my system and have installed updates as they come along and it still does not allow wireless and other problem to be corrected.

Just a thought.

keith

---

### Post by toasterboy1 on 2010-12-09
I had problems with wireless connection using a previous kubuntu version when using wpa. I started using wicd, which solved my problem, and have used it ever since. You might want to give it a try. It should be in the repos.

---

### Post by jamieb234 on 2010-12-09
hey guys!
wow what a carry on! I finally managed to get the issue resolved I found the Belkin installation CD and changed the security from WPA2 to just WPA, obtained the code from the installer and typed this into Ubuntu when it asked for the pass code and voila! IT WORKED!

However, this leaves me in a slight problem because a few of us in the house use Windows machines and this security format only seems to be working for Linux and not Windows :( 

However, not I know how to get Linux to connect to the Internet I will just switch the security as and when I need to or I will just connect via Ethernet, this just means I'm having to go into another room as oppose to my own.  

Thanks for everybody's help, really appreciated it and I'm happy to have got there in the end!

:D

---

### Post by uriel1998 on 2010-12-09
> **jamieb234 said:**
> Hi uriel1998,
I was talking to a friend of mine from work and he suggested the same thing, I am going to find the windows cd that I used to connect to the router and adjust the security so that there is none on it, then I will upgrade the security one at a time to try and find the right type of security on Linux. 
Thanks for your help, I will update once I have tried. 
Jamie

If you have wired access from either machine, you should be able to log into the control panel.  You should be able to find instructions if you search off the router's make and model.

---

### Post by uriel1998 on 2010-12-09
> **jamieb234 said:**
> hey guys!
wow what a carry on! I finally managed to get the issue resolved I found the Belkin installation CD and changed the security from WPA2 to just WPA, obtained the code from the installer and typed this into Ubuntu when it asked for the pass code and voila! IT WORKED!

However, this leaves me in a slight problem because a few of us in the house use Windows machines and this security format only seems to be working for Linux and not Windows :( 


Glad to hear you got it (mostly, at least) working...

---

### Post by anewguy on 2010-12-10
So if I understand things correctly, the router was using WPA2 and the Windows computers could connect, but you couldn't.  Then when you changed the router to WPA you can connect but the Windows computers can't.

I think you may want to try a couple of things:

- just use WPA.  On the Windows machines, you'll need to go into network connections and either delete the current known connections (so Windows would re-detect the router encryption and ask for a password) or try to edit them to the correct encryption type.  I'm pretty sure it's because Windows has remembered these connections, and hence it thinks they should be using WPA2 as in the past, that causes the problem.  Deleting the connections should get around that.

- research your adapter (I don't believe we ever asked what it was) as it's possible there may be WPA2 support but that it must be manually added and configured - I just saw a RTL chipset that required that late last week here on the forums.  If you need help researching that, please provide the following for us:

[LIST]
[*]open a terminal window (Applications/Accessories/Terminal)
[*]Type lspci <press enter> and post the output back here.
[*]Type lsusb <press enter> and post the output back here
[*]Type lshw -C network <press enter> and post the output back here
[*]Type ifconfig <press enter> and post the output back here
[*]Type iwconfig <press enter> and post the output back here.
[/LIST]

We can try to help from that information.

Dave ;)

---

