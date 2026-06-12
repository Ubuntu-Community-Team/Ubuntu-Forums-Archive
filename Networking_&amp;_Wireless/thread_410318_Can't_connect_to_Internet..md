---
title: "Can't connect to Internet."
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by fynen on 2007-04-15
Hi, I'm  a complete beginer with Linux. I've installed Umbuntu on a new hard disk and it works fine, but I'm unable to make a connection to the Internet.  I'm sharing a broadband  account with my neighbor. I 've a very strong wireless connection to his router with my D-Link DWL-2100ap, with my  access point working as an ap client. 
Works flawlesly when I run  Win XP. Running Umbuntu though there's no sign of the Access point. 
There isn't a driver for Linux included with the D-Link cd  and I haven't found one on the Internet. 
I don't mind buying another access point thats compatiable with Umbuntu if that's what I need to do.
Can anyone please advise me what I should do? I'm very keen on getting started with Linux.
Thanks in advance, Fynen

---

### Post by Turgon on 2007-04-15
Have you looked into ndiswrapper? Its a wrapper that make you able to use the windows driver under linux (in many cases). I don't know if it supports ap's, but its worth a shot!

If you search for ndiswrapper in synaptic you will find a package called ndisgtk which is a gui for ndiswrapper thats easy to use.

If you like the terminal, you can just type: sudo apt-get install ndisgtk
Type in you password and it will install.

After that, open the application (should be under the system menu somewhere) and load the windows driver.

Hope this helps.

Good luck!

---

### Post by Austin_KW on 2007-04-15
Are you using an access point in client mode, do you connect to the access point with an ethernet cable? Or do you want to connect to your ap using wireless.

If you are connecting using ethernet you should not need any additional drivers.
If you a connecting wirelessly then what type of wireless adapter do you have?

---

### Post by fynen on 2007-04-17
> **Austin_KW said:**
> Are you using an access point in client mode, do you connect to the access point with an ethernet cable? Or do you want to connect to your ap using wireless.

If you are connecting using ethernet you should not need any additional drivers.
If you a connecting wirelessly then what type of wireless adapter do you have?

Yes, I'm using an access point in client mode and using an ethernet cable. I thought that the linux software would see the ethernet connection the same as though the computer was connected to the internet via cable. I checked the setup for the lan connection several times and couldn't find any mistakes
Is it that the problem likely lies in my lan setup?
Or is the problem that my D-Link access point doesn't speak Linux language and I need to go to the ndiswrapper?
Thanks, Fynen

---

### Post by Austin_KW on 2007-04-17
> Yes, I'm using an access point in client mode and using an ethernet cable. I thought that the linux software would see the ethernet connection the same as though the computer was connected to the internet via cable.
Yes you are correct, It should just be seen as an ethernet connection. You do not need ndiswrapper,any wireless drivers or any additional drivers to use the access point in client mode.

Do you know if you are using dhcp or static addressing on the network.
If you dont know and it works on windows XP, open a windows terminal and post the output of the command "ipconfig /all"

On linux, what is the output of the commands "ifconfig -a" and "cat /etc/network/interfaces"

---

### Post by fynen on 2007-04-17
Success! thank you, I'm now on the internet with Linux. I checked my Windows setting and it said that DHCP Enabled: No
On Linux the same setting didn't work although I could contact my AP client.
I tried changing the Linux setting to DHCP: enabled and was able to go onto the Internet.
Thanks very much for the help, Fynen

---

