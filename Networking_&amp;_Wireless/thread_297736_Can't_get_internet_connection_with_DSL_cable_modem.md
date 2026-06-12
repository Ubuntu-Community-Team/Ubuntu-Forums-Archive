---
title: "Can't get internet connection with DSL cable modem"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by m_vrik on 2006-11-11
In my previous thread, "Can't Connect to Internet With Cable Ethernet," posted about 1 1/2 weeks ago, I thought that I had solved my internet connection problem by using a router between my laptop and the DSL modem.  But, when I tried to network another laptop with Windows XP Home on it, I lost the linux internet connection and my windows connection.  Now, I am connecting the laptop with Windows to the internet via a direct connection to the DSL modem, but, when shut down and I then transfer the connecting cable to my linux laptop, I'm back at the beginning.  Not sure what to try at this point?

---

### Post by FrodoB on 2006-11-11
Without more information it is hard to say, but it almost sounds like you are using the same addresses for both machines?

You should have the DHCP server on your router up and your clients should get addresses from DHCP.

You should post the output of netstat -rn from the Linux machine and Windows as well.

---

### Post by stream303 on 2006-11-11
> **m_vrik said:**
> In my previous thread, "Can't Connect to Internet With Cable Ethernet," posted about 1 1/2 weeks ago, I thought that I had solved my internet connection problem by using a router between my laptop and the DSL modem.

That's a fine idea.  Now you won't have to worry about loading any PPPOE software, as the router and modem will handle it in hardware between themselves.  In addition, your router probably has an internal firewall option.  One thing to check when bringing an off the shelf router home is to make sure that the address of the router doesn't conflict with the address of your modem!  I've seen this happen where they both try to be the same address.  If so, just reconfigure the router to use a different address.

> But, when I tried to network another laptop with Windows XP Home on it, I lost the linux internet connection and my windows connection.

With a router in place, your windows box no longer needs to use the pppoe software.  I'm not windows-savvy anymore, but if you could reconfigure your windows box for normal operations, say just standard networking and not pppoe anymore, it might work with the router in place.

> Now, I am connecting the laptop with Windows to the internet via a direct connection to the DSL modem, but, when shut down and I then transfer the connecting cable to my linux laptop, I'm back at the beginning.  Not sure what to try at this point?

Right.  Windows is setup for pppoe with a direct connect to the modem, whereas the Ubuntu box isn't when you just swap cables.  Avoid the hassle of loading pppoe on Ubuntu and use the router instead.

I'd suggest using the router again, making your standard Ubuntu box happy , and reconfiguring windows for standard network operations instead of pppoe.  Now you can use the router for both boxes.

Take inventory of your network settings in the windows box, and perhaps grab your isp's DNS nameserver addresses.  Add these in the Ubuntu networking tabs, or perhaps in the router-setup page to ease any dns issues.

Optionally, you could disable IPV6 on the Ubuntu box as well, but I'd see how it goes with the router setup again before trying this.

---

### Post by m_vrik on 2006-11-12
Stream303,
You were right about the router solving the internet connection problem.  With a little playing around, I have both the Windows laptop and my Linux laptop connected to the internet through my Xincom router.  The only problem now, and its minimal, is that every time that I boot up the Linux laptop I have to go throught the configuration process to establisht the internet connectivity.  Thanks for your suggestions.

---

### Post by stream303 on 2006-11-13
Glad thats working for you!  With your laptop having to go through the configuration process each time, do you mean username-password access or are you having to reconfigure your networking addresses each time?

If it's just username-password stuff, there are probably settings in the router you can make to pass them to the isp automatically (unlike the router's administration password itself)

Maybe we can knock this last little problem out....

---

### Post by m_vrik on 2006-11-14
Stream303,
I appreciate your help.  I was trying to load lilo and screwed up my laptop so I had to reinstall Dapper.  After the reinstall, my network is working fine -- no problems.  Don't know what was wrong but I stumbled into a solution.  Thanks again.

---

