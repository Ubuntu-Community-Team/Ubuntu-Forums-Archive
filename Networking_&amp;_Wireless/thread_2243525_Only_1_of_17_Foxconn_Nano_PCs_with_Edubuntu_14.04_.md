---
title: "Only 1 of 17 Foxconn Nano PCs with Edubuntu 14.04 can connect to wifi or ethernet."
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by smnbldwn on 2014-09-09
Hi, this is my first post. My school gave me a Windows 8 laptop on which I installed Ubuntu without any problems. I therefore persuaded them to buy a class set of desktop PCs without operating system to which I would install Edubuntu 14.04. All are now running but only 1 of them can connect to a wifi signal and access the internet. They are supposed to be identical and I installed Edubuntu from the same memory stick so I am stumped. Ethernet cable can't connect either. In both cases the network is detected but connection doesn't work.

The only difference I can think of is that for the install that worked, it managed to connect during install and then probably downloaded the right drivers. I will put a couple of pictures below with the screenshots of the configuration. 

[IMG]http://i402.photobucket.com/albums/pp103/smnbldwn/Install.jpg[/IMG]
[IMG]http://i402.photobucket.com/albums/pp103/smnbldwn/Setup.jpg[/IMG]

I am not sure what to do next to find the solution, especially as the machines cannot connect to the internet. I have tried wiping and re-installing and trying to connect during the installation process but no joy so far. Could someone with more knowledge please give me some tips on how to diagnose and fix this problem.

Thank you so much.

---

### Post by jeremy31 on 2014-09-09
I will try to help even if this seems impossible.  On the pc that works run this command in terminal(CTRL+ATL+t) ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
``` and post the resulting wireless-info.txt or attach the wireless-info.tar.gz

After that copy the wireless_script to a USB flash drive or burn it on a cd and copy it into your home folder on one of the other pc's and use terminal for this ```
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]chmod +x wireless_script && ./wireless_script
``` and post this for non working wireless[/FONT][/COLOR]

---

### Post by smnbldwn on 2014-09-10
Here is the wireless info txt file:
[ATTACH=CONFIG]256319[/ATTACH]

Now I will follow the rest of the advice.

Thank you so much!

---

### Post by smnbldwn on 2014-09-10
And this one didn't work!

---

### Post by smnbldwn on 2014-09-10
Here is the report from the non-working computer.[ATTACH=CONFIG]256321[/ATTACH]

Thank you!

---

### Post by smnbldwn on 2014-09-10
Hopefully I can get the ethernet working too!

---

### Post by smnbldwn on 2014-09-10
Update, it just gets weirder "Non functioning PC"  has now connected to my mobile phone wifi hotspot! I am trying to get it to update to see if it will automatically download the right stuff to make it go.

---

### Post by jeremy31 on 2014-09-10
You might need to ```
sudo iw reg set GB
``` on the pc's that aren't working. You should also set it in the crda file with ```
sudo gedit /etc/default/crda
```
The last line will likely be REGDOMAIN=00
Change the 00 to GB
Use caps save the file and reboot

It also seems that Ubuntu is detecting an issue with the beacons from the access point

---

### Post by smnbldwn on 2014-09-10
Thank you again, our network has issues of its own too. I will try out your suggestions tomorrow.

---

### Post by smnbldwn on 2014-09-11
Ok, now the computer that worked previously will not now connect to our school network. I ran the test while it was connected to my mobile hotspot and got this:
[ATTACH=CONFIG]256361[/ATTACH]

---

### Post by Bucky Ball on 2014-09-11
There is a fault with your school network? One of the computers connects to it anyway? The computer that doesn't connect to the school network connects fine with your phone as a hotspot? In that case, the hardware on the computers seems to be fine; they can all connect wirelessly. 

Now, what was that problem with your school's network? Perhaps hold it there and don't make any more changes until you can confirm what the problem at their end is (as it may complicate things when the school network is fully operational) because it sounds like you've confirmed all computers can connect wirelessly (and the ones that don't connect to the school network can see it ... you didn't outline what happens when you try to connect to that network; please do).

---

### Post by jeremy31 on 2014-09-11
You might want to talk to whoever is in charge of the schools wireless and see if there are any free IP addresses on the AP you are trying to connect to.  The last wireless-info is incomplete for whatever reason

---

### Post by Bucky Ball on 2014-09-11
> **jeremy31 said:**
> You might want to talk to whoever is in charge of the schools wireless and see if there are any free IP addresses on the AP you are trying to connect to. 

A good point, and also conceivable someone may have allocated only one IP to that space intentionally by configuring a dedicated router. Was there only one computer in there before? They may be setting static IP addresses using MAC addresess of known computers on the network. That way they can disable anything outside that and none available for any blow-ins. ;)

In the static IP scenario, you would need them to set aside a series of IP addresses numbering the same as the amount of computers in the room; for instance, for 19 computers: 192.168.0.100-18, as an example.

---

### Post by smnbldwn on 2014-09-11
The room was previously a computer room so it should cope with more than one computer. The computers that can't join detect the network but then try to connect and fail. The same thing happens on the ethernet connection. I agree that I need to talk to the network administrator but want to make sure it is not the "weird" new linux computers first. The network guy is a mac head. I will try all the computers with my phone first. Then try to work out what is going on with the ethernet connections.

---

### Post by Bucky Ball on 2014-09-11
You could be wasting time before you talk to IT. Those machines may not have access to the network at their end, which is why you can't connect. If the network is visible on every machine, it appears wireless is working fine. You just need IT to confirm they can see your machines and your machines have access to the network.

If the answer to both is affirmative, then we know where we stand and let's get down to it. At the moment, without confirmation from IT that everything should be AOK for you to connect, stumbling in the dark and don't really know what to look for or where to start.

If the machines don't have access to the network at IT end it would explain why the wireless network is visible, but can't connect, and ethernet can't connect, either. Ethernet works on the one that connects wireless as well, I presume?

---

### Post by smnbldwn on 2014-09-12
Ok you guys were right, weird stuff going on with the network, it is an open network but only accepts the first 500 devices and the first computer was number 500! Thanks for all your help, I'll mark this one as solved until we get people in to reset the network.

---

### Post by Bucky Ball on 2014-09-12
Bingo! We were pretty close! ;) :-k

Nice work nutting it out at your end, and what a coincidence that the one connected machine was number 500. Theoretically, you could have connected any ONE of those machines ... but ONLY one. 

Hopefully all will be resolved when they make it 518. Keep us updated. ;)

(If anyone's confident, it is probably just a matter of logging on to the router with a web browser and changing the DHCP server IP range to between 192.168.0.001-518, or something like it, but if a government organisation they possibly like to do it by the book.)

---

