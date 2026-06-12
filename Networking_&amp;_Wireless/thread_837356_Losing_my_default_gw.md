---
title: "Losing my default gw"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by pappo on 2008-06-22
I live in a rural area and I bought an Alltel USB wireless device for my home and got rid of my Wildblue Satellite service.  Alltel device works great and is much faster, but I have a problem losing my default gw address.

My network has three PC's (one XP Pro and two Linux) connected via a D-Link wireless router.  I put the Alltel device on my XP box and did ICS (Internet connection sharing).  When doing that I used my XP local lan connection to connect to my router and ICS made its address 192.168.0.1.  Now I had to change the D-link router IP to 192.168.0.2 so it would not conflict.

The problem is that my Ubuntu box is connected via DHCP wireless and everytime the DHCP connection is made the router tells it that its gateway is 192.168.0.2 and that breaks the path.  When I look at /etc/resolv.conf, it has reset whatever I put in there, back to 192.168.0.2, and when I look at "route -n" I see that I am back to 192.168.0.2 as my default gw.

The fix is easy, but manual.  I have to go in and run "sudo route add default gw 192.168.0.1" and it is back working until the next time DHCP connects.
The Ubuntu is my wife's machine and she is not command line savvy so I wanted to know how to make the default gw 192.168.0.1 permanent.

Thanks.

---

### Post by plewisfdx on 2008-06-22
Maybe a setting on the router could be changed to alleviate this problem.  Have you tried plugging the windows computer using ICS into the WAN port of the router?  

I don't know if it will work, but then the router would be using the win/ICS computer for ITS default route and the route on the wireless and connected comptuers would also be ok at 192.168.0.2.

If that doesn't work try to change a setting on the router to tell it to use the win/ICS computer for WAN.  Give it a route to the WAN, again saving you from making changes to EVERY connected computer now and in the future.

If that fails...

Have you looked at /etc/network/interfaces?
If you use network-manager (default for ubuntu) then this file will not be populated.  If you populate it, it should override network manager.  Here's an example of how to populate that file:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

You can hard code gateway in that file.

You can sudo aptitude remove network-manager if it still is handling your wifi.

If that fails...

A workaround would be to create a shell script to run at each boot.

```
#!/bin/bash
sudo route add default gw 192.168.0.1 &

```

Save the file, make it executable (chmod +x filename), and then go to System->Preferences->Sessions->Startup Programs and "Add" this new file to that list and make sure its checked.  

The command requires sudo, so you'll need to either:
1. change the line above to read ```
echo "password" | sudo -S route add default gw 192.168.0.1 & 
``` substituting password for your sudo password.  This will leave your sudo password in plaintext in your file, so the other option is...
2. add this command to visudo to allow this user to execute without a password prompt.
```
sudo visudo
```
and in the "user privilege specification section" add
```
*user* *host* = NOPASSWD: /sbin/route

```

substituting user for your username and host for your hostname.

---

