---
title: "Why can’t I connect via Wi-Fi in Windows after trying to configure my Ubuntu drivers?"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2011-04-29
Hi,

I am trying to get my Broadcom driver to work in 64-bit 10.10 (eventually got it working in 32-bit 10.10 last week) but have installed 64-bit over that. I am noticing something bizarre:

I have a Windows 7 OS on one partition and 10.10 on a second. I have noticed these past two weeks that if I try and configure my Broadcom drivers in Ubuntu to work with Wi-Fi (so far unsuccessful), that when I next boot into Windows, I can’t connect to the network. Initially, Windows would not see the network until I reset the router. Now however, I get the error “Windows can’t connect to this network” when I try to connect.  Prior to trying to get my Ubuntu drivers to work, I never, ever had an issue connecting through Windows 7.

Last week, I finally successfully configured my b43 drivers in Ubuntu (10.10 32 bit) and could connect to Wi-Fi. I could then boot into Windows and also connect to the Wi-Fi, something I could not do when my Ubuntu Wi-Fi was not working. So, when my Ubuntu Wi-Fi worked, so did my windows. When my Ubuntu Wi-Fi didn’t work, I have to jump through hoops to get it to work in Windows. I have installed the 64-bit of 10.10 and am now again in the process of trying to get my Broadcom wireless card to work.

I am not using Ubuntu ndiswrapper but instead successfully used sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer to get my Wi-Fi working in 32 bit (still not working in 64 bit).

What would cause the relationship between the work in Ubuntu to affect my card on the Windows side? 

Does this behavior give any insight into helping me get my driver working in Ubuntu?

Remember, I never had ANY issues with connections in Win 7 (since Dec. 2009) before playing with drivers in Ubuntu, so there is a connection.

Sorry for this long post but I am still learning!

Chris

---

### Post by 3rdalbum on 2011-04-29
What it sounds like to me is that the Broadcom driver on the Linux side is leaving the wireless hardware in an inconsistent state, so when Windows tries to use the card it fails.

This problem should not appear if you do a complete shutdown when going between Windows and Linux, because the device will lose power and thus go back to its default state when repowered. I wouldn't advocate this as a permanent solution, but can you confirm that the device works properly after a complete shutdown and boot into Windows?

---

### Post by grahammechanical on 2011-04-29
I have heard that it is possible to use software to switch off the wireless adapter. It is the reason why some say that wireless works in Windows but not in Ubuntu even though all the settings are correct. Switch off wireless, close Windows, load Ubuntu and no wireless. It appears that with your machine it is happening the other way around.

Regards.

---

