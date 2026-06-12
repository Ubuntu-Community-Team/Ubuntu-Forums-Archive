---
title: "resolv.conf file NOT resetting"
date: 2018-10-08
forum: Networking &amp; Wireless
---

### Post by ajay.dham on 2018-10-08
I am running Ubuntu 16.04.05.

I noticed that the resolv.conf fie was not a symbolic link, so I created the symbolic link by running these two commands:

1.  sudo rm /etc/resolv.conf
2.  sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf

This worked great.  See image below.

[ATTACH=CONFIG]281280[/ATTACH]

Now I ran my vpn by using this command:
sudo netExtender -u <username> -p '<password>' -d LocalDomain <VPN Connection Name>  

Again this worked out great and I was able to VPN and all working. 

Now I disconnect from the vpn by doing a ctrl-c. Disconnected successfully. 

Now, I am not able to access internet or anything because the resolv.conf file did not reset.  It kept the parameters that were given to it when it made the vpn connection.  Then I ran the permissions command on the resolv.conf file and now the symbolic link was missing again.  Look at this image of the commands that I took.  

[ATTACH=CONFIG]281281[/ATTACH]

Now, if i run the following 2 commands again, it'll work.  

1.  sudo rm /etc/resolv.conf
2.  sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf

Question is why am I loosing this link with the symbolic file??  I should not have to run the 2 above commands again and again after I disconnect from the VPN.  It goes to say though if I never connect to the VPN then I have that internet connection and can ping the outside world.  This issue is ONLY once I disconnect from VPN.  Am I perhaps missing some permanent type command?  

FYI > I am not a expert in Ubuntu or linux for that matter, so if you guys can provide any help then please try to be as detailed as possible, so I can follow the steps to fix this issue. 

Thank you all for your support in advance. 

- AJ

---

