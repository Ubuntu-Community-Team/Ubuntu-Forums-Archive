---
title: "how can I Login to Panera Bread's free WiFi"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by daniel-grunberg on 2014-02-04
At the Panera Bread at the Mall in Columbia, MD: 

 When I used Ubuntu 12.04 LTS and Firefox (with everything recently updated) -- 

 When I tried to login to Panera Bread's free Wifi, I got a Panera Bread greeting page. When I clicked that page's Login button I got a page unavailable message. Panera recognized me and Ubuntu continued to show that I was connected to Panera, nevertheless Panera wouldn't let me surf the Web with Firefox (or Chromium or Opera which I also have on my system). 

 [By the way I was able to use Windows 7 (dual booted on my system) and Firefox to connect to Panera Bread's Wifi, click on the Login button on Panera's greeting page, and surf the Web.] 

 [Also by the way, I can always use Ubuntu and Firefox to connect to the Internet and surf the Web at any Starbucks.] 

 Am I missing something? 

 More to the point, has anyone using Ubuntu or another flavor of Linux been able to browse while connected to Panera Bread's free Wifi? And if so, how?how can I Login to Panera Bread's free WiFi

---

### Post by varunendra on 2014-02-06
Welcome to the forums Daniel!

A "system-ca-certs" issue maybe? It often happens with WPA2 Enterprise networks which I assume they would be using.

Please check -
```
sudo grep 'system-ca-certs' /etc/NetworkManager/system-connections/*<the connection's name here>*
```
If you see a line with value "true", it is most certainly the thing causing the problem. Try changing it to false -
```
sudo sed -i '/system-ca-certs/ s/true/false/' /etc/NetworkManager/system-connections/<the connection's name here>
```
or deleting the line altogether -
```
sudo sed -i '/system-ca-certs/ d' /etc/NetworkManager/system-connections/<the connection's name here>
```

If the connection still fails, check again with the first command to make sure its value didn't change to "true" again, or if it did and so you deleted it, it didn't regenerate.

---

### Post by daniel-grunberg on 2014-03-06
Thanks for the reply, varunendra.

When I thought about the /etc/NetworkManager/system-connections/PANERA file that you mentioned, it occurred to me that I was able to logon to Panera's wifi before Panera changed their wifi system. 

I reasoned that an old *PANERA* file might not be compatible with Panera's new wifi system. So I renamed *PANERA as *[I]PANERA.bak 
[/I]
Last week I visited Panera Bread at Columbia, MD. I was able to connect to Panera's wifi. I checked and there was a new *PANERA *file in Ubuntu's ~*/system-connections*directory. 

Thank you for jogging my mind.

---

### Post by varunendra on 2014-03-06
..And thank You for the feedback, it's good to know and keep in mind the possibilities other than what we usually think about. :)

Please mark the thread as [SOLVED] now that it is, using the "Thread Tools" link above the first post.

---

