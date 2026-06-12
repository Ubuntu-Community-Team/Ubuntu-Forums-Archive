---
title: "Networking complete freeze of Dapper"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by johanPO on 2006-11-19
My machine has been upp and running for a few months now with WLAN, fixed IP and WEP. 
Yesterday I did something stupid. I decided to try out WPA, and decided to follow the [instructions]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") . I did not have the Network manager installed, so I installed with apt-get.. After this I disabled eth2 in Networking, and loged out. No change, so I restarted my PC. After this I have had major problems to get things to work again. Basicaly the Network manager does not want to work, (when I enter the WEP I do not get access) so I decided to go back to my old working setup and that is when the problems started. 
Whenever I enter the WEP, IP adress, Gateway etc and press OK in the Networking, my machine freezed up comlpetly. Nothing helped, but power on/off. When I looked in /etc/network/interfaces no changes were made. 
When I used DHCP I got an IP, and things worked. But as soon as I tried to enter a static IP adress, my machine froze. 

So basically I had to manually edit the /etc/network/interfaces. That was the only way to get this to work. I guess I have learned my lesson, and will not play around with these settings in the future..

---

