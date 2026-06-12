---
title: "extremely confusing network problem"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by gairy_s on 2008-01-01
Let me start off by saying I've read through these forums for the past year, and it seems that the community support here is far greater than what I have seen with openSUSE and Fedora. Thank you for all of your help within the past year since I started using Ubuntu on my HP ze4930us laptop and now with Ubuntu Server as a Samba server in my network.

Here is my problem. I'll make the explanation simple, because this problem is confusing the heck out of me. My Comcast coax comes into the house and hits some splitters for cable in multiple rooms. The installer added another splitter in the bedroom, one for cable and the other for my Scientific Atlanta DPC2100 cable modem. When I added VOiP, the installer added a splitter at the coax going to the cable modem in order to add the Touchstone phone modem. THIS is the only common connection between the two. The phone modem is connected via RJ11 to the filter and then the home phone line.
The cable modem goes via RJ45 to a D-Link DI-524 router. Port 1 goes to my desktop running Vista. Port 3 goes to my Brother laser printer. Port 4 goes to my Ubuntu Samba Server. Port 2 goes to a D-Link DES-1105, which goes to my Cisco home lab, 2 2507 routers, which has been off for some time now.

My desktop is a HP a1600n with 200GB WD h/d, 3 GB RAM, and nVidia 7300GS video card. I decided to dual-boot my desktop with Ubuntu. I backed up everything, reformatted, installed Vista, and proceeded with the Ubuntu install.
/dev/sda1 - NTFS - 75G - Vista install
/dev/sda2 - Ext3 - 20G - Ubuntu root
/dev/sda3 - swap - 2G
/dev/sda4 - extended
/dev/sda5 - Fat32 - 30G - /osswap
/dev/sda6 - Ext3 - 55G - /home

When I completed my install, I lost everything wireless and my phone modem. This is not a joke. When I rebooted, my phone modem only had the Power LED light on and DS LED blinking. I also could not connect to my router with my server via 192.168.0.1 in Firefox. Unfortunately, I need Windows to complete my network administration courses, but I'm ready to complete the switch. So far, I have called Comcast and they are at a complete loss. When I reboot to Vista, all is well again. I have just finished my Vista reinstall, and I can now communicate with my router, so I am about to call Comcast back and disconnect my cable modem and just use my phone modem for both VOiP and Internet, which they couldn't understand why the installer did this in the first place. I also plan to remove the D-Link router in the next few days for something a little newer.

Does anyone have any idea why this would happen? Also, is there a recommendation as to what router I should purchase that works great with Ubuntu, and that Vista can not get it's dirty evil grips onto? I've only been in school for 1 year now, so I'm by no means an expert, but I do have a fairly good idea about networking, and this is blowing my mind. It's not so much the fact that it crippled my network, but why did it effect my phone modem when there is no connect between the two except at the coax?

I apologize for the lengthy explanation, I just wanted to make sure I provided as much information to help diagnose as I could.

---

### Post by peitschie on 2008-01-01
Ummm... Is it accurate to say that everything depending on the computer having a network connection failed?  As far as I can tell, an unsupported network card on the computer would cause all these problems as if the computer can't connect to the router, then nothing else will function...

---

### Post by gairy_s on 2008-01-01
I could understand an unsupported card disabling my local access, but why would Vista take out my entire network when it is shut down. Nothing physical changed, all I did was turn off my Vista side and rebooted with my Ubuntu side. I have to check to see if the nVidia controller is supported.

---

### Post by peitschie on 2008-01-01
So let me see if I have this straight...

Is this an accurate representation of your network?

```

 Comcast Internet
        |
     **Splitter**
    /      \
House    **Splitter**
          /      \
      Cable TV    **Splitter**
                  /     \
       Phone Modem    Cable Modem
                          |
                       [=== D-Link DI-524 ===]
                      /       /      \       \
                    **Desktop**   |    Printer  Server
                              |
                      D-Link DES-1105

```

---

### Post by gairy_s on 2008-01-01
Yep. I went ahead and reset the router after the Vista reinstall. Tonight my wife has some work to get done, so tomorrow when I get home from work, I'll call Comcast to disconnect the cable modem and just use the telephone modem. I also think I am going to replace the D-Link with a Linksys. But for tomorrow, I'll make the switch, make sure everything has a connection, then shut down Vista and wait for a few to see if we lose connection again. If all is good for about 30 min, I'll attempt the dual-boot again.

---

### Post by peitschie on 2008-01-03
So... any  luck on this?

---

### Post by gairy_s on 2008-01-03
The field technician literally left 15 minutes ago. I have had to reset my D-Link and get the rest of my house online. :) Now that this is working again, I am only using the Arris Touchstone modem for both my internet and phone. I will be trying the dual-boot again this weekend. If I come across problems again, I'll let you know.

On a side note, when I spoke to the field technician about my problem, he stated that Comcast only allows 1 IP address per house. The only way a customer is allowed multiple IP addresses is if they pay for separate accounts. He said that it may take time for Comcast to find you, but when they do locate multiple IP addresses at the same location, they disconnect all services to that location and the customer service technicians will have no indication as to whether this is the problem or not without calling the business office. He said it may have been the reason, but very highly unlikely due to the fact that I have had service for over a year. He did clarify why the phone tech couldn't provision the MTA because he was trying to work around the multiple IP address problem instead of just doing a dump and refreshing my IP and allowing it to propagate.

---

### Post by gairy_s on 2008-01-04
I believe we have found the problem, but I'm not sure why. Another tech is coming out Sunday. Apparently, the original phone installer placed a filter in between the phone modem and the wall outlet. The tech removed the filter and I haven't had a problem yet. I did replace the DI-524 with a WRT150N, but the call for Sunday is to upgrade my service to a Linksys WCG200 for no additional charge, due to new lag issues with the combined service through the Arris modem during web surfing and Counter-Strike.

The reinstall of the dual-boot was a success, and I haven't found any other problems. Thank you everyone for your immediate responses.

One last question if possible. I intend on changing my Ubuntu server setup to act as a home server, i.e. LAMP, Samba, etc. Are there any known issues with the server running the DNS and DCHP functions instead of the WCG200? I had problems with Amahi and DHCP with the DI-524, and I'm still anxiously waiting for Ubuntu Home Server. BTW, thank you to all that are working on that project, I can't wait to get my hands on it.

---

### Post by peitschie on 2008-01-04
Glad to hear it all resolved satisfactorily :)

Regarding issues running DNS and DHCP from the home server... as far as I am away there should be no major issues.  Just need to ensure your router can automatically get an address properly (not all offer this feature).  

If you don't want the heartache of doing things that way however, it is possible to leave the DHCP on the router and just move the DNS, or even leave the DNS and DHCP on the router if you don't need specific hostnames for your internal systems...  Is there a particular reason you want to move both?

---

### Post by gairy_s on 2008-01-05
I use wireless in my home for 3 laptops and 1 desktop. I also have the WPA enabled. So that side is somewhat secure, but I'd like to have home authentication because I can see 3 other networks when I search. I also would like to locally host a site for my family and set up VPN for my wife who travels. My goal is to set a domain with a remote server hosting the main site, and a home domain with FTP and other services set up for my wife and family.

I am also in school for Network Administration, and I have finished my first SLES 9 course. I have a domain setup for my test lab, 2 Cisco routers and 2 PC's running Ubuntu, and I'm finding this rather fun. I need the experience and would like to implement it on my home network.

---

### Post by peitschie on 2008-01-06
Sounds like a lot of fun :)... those are the best reasons I have heard for trying lol.  Would be cool if you could post a thread on how your setup works when you're done :)... I'd be interested in seeing how you work it all out!

---

### Post by gairy_s on 2008-01-06
I sure will. I definitely want a copy of Ubuntu Home Server when it is finished, but I'll post how Ubuntu on 2 computers works with SME server, Vista, and XP.

---

